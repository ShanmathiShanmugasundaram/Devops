# Devops
# Git Command Practice - Day 1

Below are the Git and Linux commands used along with their explanations.

---

## Linux Commands

- `ls` – Lists files and directories in the current folder.  
- `pwd` – Displays the present working directory path.  
- `ls -l` – Shows detailed file information (permissions, owner, size).  
- `ls -a` – Lists all files including hidden files.  
- `ls -s` – Shows file sizes in blocks.  
- `mkdir devops` – Creates a new directory named *devops*.  
- `rmdir shanmathi` – Removes an empty directory.  
- `cd devops` – Changes directory to *devops*.  
- `cd ..` – Moves one directory up.  
- `touch new.txt` – Creates a new empty file named *new.txt*.  
- `vim new.txt` – Opens the file in Vim editor.  
- `cat new.txt` – Displays the content of *new.txt*.  
- `cp new.txt newdir/` – Copies *new.txt* into *newdir* folder.  
- `rm day1.txt` – Deletes the file *day1.txt*.  
- `echo "Day 1" >> day1.txt` – Appends text to *day1.txt*.  
- `history` – Displays command history.  
- `history >> day1.txt` – Appends command history to *day1.txt*.  

---

## Git Commands

- `git init` – Initializes a new Git repository.  
- `git add README.md` – Stages the README file for commit.  
- `git add .` – Stages all modified and new files.  
- `git commit -m "first commit"` – Commits staged changes with a message.  
- `git config --global user.email "email"` – Sets global Git email.  
- `git config --global user.name "name"` – Sets global Git username.  
- `git branch -M main` – Renames current branch to *main*.  
- `git remote add origin <repo-url>` – Connects local repo to remote GitHub repo.  
- `git push -u origin main` – Pushes code to remote main branch and sets upstream.  
- `git push origin main` – Pushes changes to main branch.  
- `git push` – Pushes changes to the tracked branch.  
- `git clone <repo-url>` – Clones a remote repository.  
- `git status` – Shows the current status of files.  

---
