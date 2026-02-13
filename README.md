# Day 2 - DevOps Practice

## VMware Installation & Server Setup

1. Install **VMware Workstation** or **VMware Player** on your system.
2. Create a new virtual machine (VM) and install your preferred OS (e.g., Ubuntu 22.04 LTS).
3. Configure the VM network settings (NAT or Bridged) to allow internet access.
4. Start the VM and open the terminal to access the server.
5. Update your system:

```bash
sudo apt update
sudo apt upgrade -y

Docker Installation
1. Remove old Docker packages (ignore errors)
sudo apt remove docker docker-engine docker.io containerd runc

2. Update the system
sudo apt update

3. Install prerequisites
sudo apt install ca-certificates curl gnupg lsb-release -y

4. Add Docker GPG key
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

5. Add Docker repository
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

6. Install Docker Engine
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

7. Start Docker service
sudo systemctl start docker
sudo systemctl enable docker

8. Verify Docker installation
sudo docker run hello-world

9. Run Docker without sudo (optional)
sudo usermod -aG docker $USER
newgrp docker


Or reboot the VM to apply the group changes.

10. Final tests
docker --version
docker ps

Notes / Troubleshooting

If Docker fails to pull images, check firewall or network settings.

Ensure system time is correct to avoid TLS handshake errors.

Keep your VM and Docker installation updated for compatibility.
