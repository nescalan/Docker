# 🚀 Project 1: Nginx Web Server with Docker

**Author:** Ing. Nelson González Escalante

---

## 🎯 Objective

Deploy an **Nginx web server** using Docker, accessible from the browser without affecting the host system. Learn to manage the container easily: create, run, verify, access, stop, and remove it.

---

## 📋 Requirements

- Docker installed on your system
- Port `8080` available on your host (or you can choose a different one)

---

## 🧪 Steps to Complete the Project

### 1. Create and run the Nginx container

Open your terminal and run:

```bash
# Pull the Nginx image (if not already downloaded)
docker pull nginx

# Create and run the container with a name and port mapping
docker run -d --name web-nginx -p 8080:80 nginx