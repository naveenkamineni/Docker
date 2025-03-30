# 🐳 Docker - Containerization Made Simple

Docker is a **software tool** that packages **code, libraries, and dependencies** into a single unit, called a **container**. It simplifies application deployment and ensures **portability** across different environments using **Dockerfiles**.

🚀 **Docker makes running microservices easy by containerizing applications!**

---

## 🔄 Alternatives to Docker
While Docker is popular, there are some alternatives:
- **Podman** 🏗️
- **LXC (Linux Containers)** 📦
- **Kubernetes** (For orchestration) ☸️
- **OpenShift** 🌍

---

## 🔑 Key Docker Terms
1. 🖼️ **Docker Image** - A lightweight, standalone, and executable package that includes everything needed to run an application.
2. 📦 **DockerHub / Registry** - A cloud-based repository for storing and distributing Docker images.
3. 🏗️ **Docker Container** - A running instance of a Docker image that includes the application and its dependencies.
4. ⚙️ **Docker Daemon** - A background service that manages Docker objects such as images, containers, and networks.
5. ⬇️ **docker pull** - A command used to download images from DockerHub or other registries.
6. 🏗️ **docker build** - A command used to create a new image from a Dockerfile.
7. ▶️ **docker run** - A command to start a container from a Docker image.
8. 🖥️ **Docker Client** - A command-line tool that communicates with the Docker Daemon.
9. 🏠 **Docker Host** - The machine where Docker Daemon runs and manages containers.
10. 📜 **Dockerfile** - A script that defines the instructions for building a Docker image.
11. 🔀 **docker-compose** - A tool used to define and run multi-container Docker applications.
12. 💾 **docker volumes** - A feature that allows persistent storage for Docker containers.
13. 🌍 **Docker Swarm** - A native clustering and orchestration tool for managing multiple Docker containers.

---

## 📜 What is a Dockerfile?
A **Dockerfile** is a **script** that automates the process of creating a **Docker Image**. It includes:
- 📄 **Application files** (HTML, configurations, etc.)
- 📦 **Libraries & dependencies**
- 🚪 **Ports** for networking
- 📂 **Directory structure** inside the container
- 🎬 **Entry point** to start the container

---

## ⚙️ Setting Up Docker Environment
Before using Docker, we need to set up an **environment** for **containerization**.

### 🏗️ Ways to Create a Docker Environment
1. 🖥️ **Docker Desktop** (For Windows & macOS)
2. 🏢 **Installing Docker on Virtual Machines (VMs)**
3. ☁️ **Docker on Cloud Platforms:**
   - 🟠 **AWS ECS, ECR**
   - 🔵 **Azure VMs**
   - 🌍 **GCP Docker**
   - 🚀 **OpenShift Docker**
4. 🐳 **Run Docker inside a Docker container** (Docker-in-Docker)
5. 🏠 **Docker on Bare Metal Servers** (Self-hosted environment)
6. ☸️ **Running Docker with Kubernetes (K8s)**

---

## 🖥️ How to Set Up Docker Desktop
1. **Download and install Docker Desktop** from the [official website](https://www.docker.com/products/docker-desktop/).
2. **Install Git Bash** (for Windows users).

```
        🏗️ Docker Container
         🖼️ Docker Image
         ⚙️ Docker Daemon
       🏠 Docker Environment
          🐧 Linux OS
        🖥️ Docker Desktop
          🏁 Windows OS
```

---

## ☁️ How to Set Up Docker on Cloud Instances (EC2): Linux-Based VMs

```
        🏗️ Docker Container
         🖼️ Docker Image
         ⚙️ Docker Daemon
       🏠 Docker Environment
          🐧 Linux OS
   ☁️ Cloud Infrastructure (EC2 Instance)
```

### 📜 Installation Commands for Linux (Ubuntu)
```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

---

## ⬇️ How to Pull an Image from Docker Hub
To pull an image from Docker Hub, use:
```bash
docker pull image-name
```
Example:
```bash
docker pull nginx
```
This command downloads the `nginx` image from Docker Hub to your local machine.

To list all downloaded images:
```bash
docker images
```

---

## 🏗️ How to Build a Docker Image
To build an image from a Dockerfile, run:
```bash
docker build -t my-image-name .
```

- `-t my-image-name` → Tags the image with a name.
- `.` → Refers to the current directory where the Dockerfile is located.

---

## ▶️ How to Run a Container from an Image
To run a container from a Docker image, use:
```bash
docker run -d --name my-container my-image-name
```
- `-d` → Runs the container in detached mode (background).
- `--name my-container` → Assigns a name to the container.
- `my-image-name` → The image to run.

To check running containers:
```bash
docker ps
```

---

## 💾 How to Create a Docker Volume
To create a volume for persistent storage:
```bash
docker volume create my-volume
```
To list all volumes:
```bash
docker volume ls
```

---

## 📂 How to Mount a Volume to a Container
To mount a volume while running a container:
```bash
docker run -d --name my-container -v my-volume:/app/data my-image-name
```
- `-v my-volume:/app/data` → Maps `my-volume` to `/app/data` inside the container.

---

## 🔍 How to Move into a Running Container
To open a shell inside a running container:
```bash
docker exec -it my-container /bin/bash
```
- `-it` → Allows interactive access.
- `my-container` → The name of the running container.
- `/bin/bash` → Starts a bash shell inside the container.

To exit the container shell, type:
```bash
exit
```

---

## 🚀 Important Docker Commands
### 📜 List Docker Images
```bash
docker images
```
### 📜 List Running Containers
```bash
docker ps
```
### 📜 List All Containers (Including Stopped)
```bash
docker ps -a
```
### 🗑️ Remove a Docker Image
```bash
docker rmi image-id
```
### 🗑️ Remove Multiple Images
```bash
docker rmi image-id1 image-id2
```
### 🗑️ Remove a Container
```bash
docker rm container-id
```
### 🗑️ Remove Multiple Containers
```bash
docker rm container-id1 container-id2
```

---

## 🎯 Conclusion
Docker simplifies **application deployment** by packaging everything into a **container**. It is widely used for **microservices, cloud deployment, and DevOps**. With Docker, you can ensure **portability, scalability, and efficiency** across different environments.

💡 **Docker Easy!** 🐳🚀

