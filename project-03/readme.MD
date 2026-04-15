## ✅ Project 2 Completed: Interactive Ubuntu Container

**Status:** ✅ Done

**Objective:** Learn to use Docker containers interactively to run basic commands in a Linux environment without affecting the host system.

**What was accomplished:**
- Started an interactive Ubuntu 20.04 container
- Updated package lists (`apt update`)
- Installed `nano` text editor
- Created `hola.txt` with content inside the container
- Verified file content (`cat hola.txt`)
- Exited and removed the container with no residues on the host

**Key commands used:**
```bash
docker run -it --name ubuntu-lab ubuntu:20.04 /bin/bash
apt update
apt install -y nano
echo "Hola Docker - My first file inside a container" > hola.txt
cat hola.txt
exit
docker rm ubuntu-lab