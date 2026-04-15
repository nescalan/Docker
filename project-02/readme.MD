# 📄 Dockerfile Explanation

This `Dockerfile` creates a basic Ubuntu-based image with the `nano` text editor installed and a sample text file.

---

## 🔍 Line-by-Line Explanation

### 1. `FROM ubuntu:24.04`
**Use an official base image**

This line specifies the base image to start from. Here, we use the official Ubuntu 24.04 (Noble Numbat) image from Docker Hub. All subsequent instructions will be built on top of this operating system.

---

### 2. `RUN apt update`
**Update package lists**

This command updates the list of available packages and their versions from the Ubuntu repositories. It does not install or upgrade any packages — it simply refreshes the package index.

---

### 3. `RUN apt install -y nano`
**Install the nano text editor**

The `-y` flag automatically answers "yes" to any confirmation prompts during installation. This installs the `nano` editor, allowing you to edit files directly inside the container.

---

### 4. `WORKDIR /usr/local/app`
**Set the working directory**

This creates and switches to `/usr/local/app` as the working directory inside the container. Any subsequent `RUN`, `CMD`, `COPY`, or `ADD` commands will be executed from this location. If the directory does not exist, Docker creates it automatically.

---

### 5. `RUN echo "This is a random text in the file" > hola.txt`
**Create a file with content**

This command creates a file named `hola.txt` inside the working directory (`/usr/local/app`) and writes the specified text into it. The `>` operator redirects the output of `echo` into the new file.

---

### 6. `RUN cat hola.txt`
**Display the file content**

This command reads and outputs the contents of `hola.txt` to the terminal during the image build process. It is useful for verification — you will see the text printed in your build logs.

---

## 🐳 How to Build and Run This Dockerfile

```bash
# Build the image
docker build -t ubuntu-with-nano .

# Run a container from the image
docker run -it ubuntu-with-nano /bin/bash

# Inside the container, verify the file exists
cat /usr/local/app/hola.txt