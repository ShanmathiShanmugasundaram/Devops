# Day 3 Work
# Running Node.js App in Docker (Ubuntu VM + VS Code Remote SSH)

---

## Step 1: Open Ubuntu VM in VS Code

- Open VS Code
- Connect to Ubuntu VM using Remote SSH
- Open terminal inside VS Code

---

## Step 2: Clone the Repository

```bash
git clone https://github.com/jagadeeshkanna97/docker_sample/
cd docker_sample
```

---

## Step 3: Create Dockerfile

Create a file named:

```
Dockerfile
```

Paste the following content:

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm", "start"]
```

---

# Dockerfile Explanation

## FROM node:18-alpine

- Uses Node.js version 18 with Alpine Linux.
- Lightweight image.
- Includes Node.js, npm, and minimal Linux OS.

---

## WORKDIR /app

- Creates `/app` directory inside container (if not present).
- Sets it as working directory.
- All next instructions execute inside `/app`.

Equivalent to:
```
mkdir /app
cd /app
```

---

## COPY package*.json ./

- Copies `package.json` and `package-lock.json`
- From local machine → container `/app`

---

## RUN npm install

- Installs all dependencies inside container.
- Creates `/app/node_modules/`
- Express and other libraries are installed because they are listed in `package.json`.

---

## COPY . .

- Copies entire project into container `/app`
- Includes app.js and all source files.

---

## EXPOSE 3000

- Tells Docker the application runs on port 3000.
- Does NOT publish port.
- Port mapping happens during `docker run`.

---

## CMD ["npm", "start"]

- Runs when container starts.
- Executes `npm start`.
- `npm start` runs `node app.js` (based on package.json).

---

# Why Separate COPY for package.json?

Docker builds images in layers:

Layer 1 → FROM node image  
Layer 2 → COPY package.json  
Layer 3 → RUN npm install  
Layer 4 → COPY application code  

If only `app.js` changes:

- `package.json` remains unchanged
- Docker reuses cached `npm install`
- Dependencies are NOT reinstalled
- Build is faster

---

# Build Docker Image

```bash
docker build -t docker-node-app .
```

What happens:

1. Docker reads Dockerfile  
2. Downloads Node Alpine base image  
3. Copies package.json  
4. Installs dependencies  
5. Copies app code  
6. Creates final image  

`-t docker-node-app` → Tags the image name.

---

# Run Docker Container

```bash
docker run -p 3000:3000 docker-node-app
```

What happens:

1. Creates container from image  
2. Runs `npm start`  
3. Node app starts inside container  
4. Maps port 3000 (container) → 3000 (host)

Port Mapping:

Host (VM/Windows) → 3000  
Container → 3000  

---

# Test Application

Open browser:

```
http://localhost:3000
```

If using VM:

```
http://<VM-IP>:3000
```

Expected Output:

```
Hello from Docker!
```

---
