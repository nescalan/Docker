# 🐍 Dockerfile Explanation: Python Script Container

This `Dockerfile` creates a lightweight Python container to run a simple Python script (`greetings.py`).

---

## 🔍 Line-by-Line Explanation

### 1\. `FROM python:3.9-slim`
**Use an official base image**

This line specifies the base image. We use `python:3.9-slim` --- an official Python 3.9 image that is "slim" (minimal size, without extra packages). This keeps the final image small and efficient.

---

### 2\. `WORKDIR /app`
**Set the working directory inside the container**

This creates and switches to `/app` as the working directory inside the container. Any subsequent commands (`COPY`, `CMD`, etc.) will be executed from this location. If the directory doesn't exist, Docker creates it automatically.

---

### 3\. `COPY greetings.py .`
**Copy the Python script into the container**

This copies the `greetings.py` file from your host machine (current directory) into the container's working directory (`/app`). The `.` means "current working directory" (which is `/app` from the previous step).

---

### 4\. `CMD ["python", "greetings.py"]`
**Define the command to run the application**

This specifies the default command to execute when the container starts. It runs the Python interpreter (`python`) with the script `greetings.py`. Unlike `RUN`, `CMD` is executed at container runtime, not during image build.

---

## 📁 Project Structure

project-folder/\
├── Dockerfile\
└── greetings.py