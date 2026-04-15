# 📄 Dockerfile Explanation for Project 4

This Dockerfile containerizes a Flask web application using Python 3.9.

---

## 🔍 Line-by-Line Breakdown

### 1. `FROM python:3.9-slim`

**Use an official lightweight Python image**

This base image includes Python 3.9 with only essential packages, keeping the final image small and efficient for production.

---

### 2. `WORKDIR /app`

**Set the working directory**

Creates the `/app` folder inside the container and sets it as the current working directory. All subsequent commands will run from this location.

---

### 3. `COPY requirements.txt .`

**Copy dependency file first (layer caching)**

Copies only `requirements.txt` from your host into the container. Doing this **before** copying the rest of the code allows Docker to cache the dependency installation layer. If your code changes but `requirements.txt` stays the same, Docker reuses the cached layer instead of reinstalling packages — speeding up builds.

---

### 4. `RUN pip install --no-cache-dir -r requirements.txt`

**Install Python dependencies**

Installs all packages listed in `requirements.txt` (including Flask). The `--no-cache-dir` flag prevents pip from saving cache files, reducing image size.

---

### 5. `COPY . .`

**Copy the entire Python application**

Copies **all files and folders** from your host's current directory into the container's `/app` directory. This includes your Flask application code (`app.py`), templates, static files, and any other project files.

> ⚠️ **Note:** Unlike copying only `app.py`, this copies everything. Use a `.dockerignore` file to exclude unnecessary files (like `__pycache__/`, `.git/`, `venv/`).

---

### 6. `CMD ["flask", "run", "--host=0.0.0.0"]`

**Define the command to run the application**

When the container starts, this command executes `flask run --host=0.0.0.0`. The `--host=0.0.0.0` makes the Flask development server accessible from outside the container (necessary for port mapping to work).

---

## 📦 Complete Dockerfile

FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["flask", "run", "--host=0.0.0.0"]

---

## 🚀 Build & Run Commands
# Build the image
docker build -t flask-app .

# Run the container (map port 5000)
docker run -d -p 5000:5000 --name flask-container flask-app