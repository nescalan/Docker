# 🐍 Dockerfile Explanation: Python Script Container

This `Dockerfile` creates a lightweight Python container to run a simple Python script (`greetings.py`).

---

## 🔍 Line-by-Line Explanation

### 1. `FROM python:3.9-slim`
**Use an official base image**

This line specifies the base image. We use `python:3.9-slim` — an official Python 3.9 image that is "slim" (minimal size, without extra packages). This keeps the final image small and efficient.

---

### 2. `WORKDIR /app`
**Set the working directory inside the container**

This creates and switches to `/app` as the working directory inside the container. Any subsequent commands (`COPY`, `CMD`, etc.) will be executed from this location. If the directory doesn't exist, Docker creates it automatically.

---

### 3. `COPY greetings.py .`
**Copy the Python script into the container**

This copies the `greetings.py` file from your host machine (current directory) into the container's working directory (`/app`). The `.` means "current working directory" (which is `/app` from the previous step).

---

### 4. `CMD ["python", "greetings.py"]`
**Define the command to run the application**

This specifies the default command to execute when the container starts. It runs the Python interpreter (`python`) with the script `greetings.py`. Unlike `RUN`, `CMD` is executed at container runtime, not during image build.

---

## 📁 Project Structure
project-folder/
├── Dockerfile
└── greetings.py

text

---

## 🐍 Example `greetings.py` Script

For this Dockerfile to work, you need a `greetings.py` file. Here's a simple example:

```python
# greetings.py
print("Hello from inside the Docker container!")
print("Welcome to Docker!")
🚀 How to Build and Run
1. Build the Docker image
Navigate to the folder containing both Dockerfile and greetings.py, then run:

bash
docker build -t my-python-script .
Explanation:

docker build → Creates the image

-t my-python-script → Tags (names) the image as my-python-script

. → Uses the current directory as build context

2. Run the container
bash
docker run --rm my-python-script
Explanation:

docker run → Creates and starts a container from the image

--rm → Automatically removes the container after it stops

my-python-script → The image name to use

Expected Output
text
Hello from inside the Docker container!
Welcome to Docker!
📝 Summary of Docker Instructions
Instruction	Purpose	When executed
FROM	Sets base image	Build time
WORKDIR	Sets working directory	Build time
COPY	Copies files from host to container	Build time
CMD	Defines default runtime command	Container start
✅ What This Dockerfile Accomplishes
Uses a minimal Python 3.9 base image

Creates a clean /app working directory

Copies only the necessary script (efficient caching)

Runs the Python script when the container starts

The --rm flag ensures the container is removed after execution, leaving no residues on the host

💡 Key Learning Points
Layer caching: Copying files after WORKDIR and before CMD optimizes builds

Slim images: python:3.9-slim reduces image size vs. python:3.9

--rm flag: Useful for one-time scripts to avoid cluttering your system with stopped containers

CMD vs RUN: RUN executes during build, CMD executes at container runtime