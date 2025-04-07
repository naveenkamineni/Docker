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

## 📝 Example: Writing a Dockerfile for Nginx

A **Dockerfile** defines the environment for your container. Below is an example Dockerfile for running an **Nginx web server**:

```dockerfile
# Use the official Nginx base image  
FROM nginx:latest  

# Copy custom static files to Nginx's HTML directory  
COPY index.html /usr/share/nginx/html/  

# Expose port 80 to allow traffic  
EXPOSE 80  

# Start Nginx when the container starts  
CMD ["nginx", "-g", "daemon off;"]  
```

### 📌 Steps to Create and Use the Dockerfile:
1️⃣ **Create a file** named `Dockerfile` (without any extension).  
2️⃣ **Copy** the above content into the file.  
3️⃣ **Build an image** from this Dockerfile using:
   ```bash
   docker build -t my-nginx .
   ```
4️⃣ **Run the container** from the built image:
   ```bash
   docker run -d --name my-nginx-container -p 8080:80 my-nginx
   ```
   Now, you can access your Nginx server at **http://localhost:8080**! 🚀  

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
docker run -d --name my-container -p host-port:Application-port my-image-name
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
### 📜 Remove a Docker Image
```bash
docker rmi image-id
```
### 🗑️ Remove Multiple Images
```bash
docker rmi $(docker images -q) -f
```
### 🗑️ Remove a Container
```bash
docker rm container-id
```
### 🗑️ Remove Multiple Containers
```bash
docker rm $(docker ps -a -q) -f
```

---

Here's a well-structured and formatted version of your content for the GitHub README file:  

---

# Managing Files and Logs in Docker Containers with Volume Mounts Concept

When working with Docker containers, you may need to modify configuration files, monitor logs, or update content without rebuilding the container. Docker volumes allow us to achieve this efficiently.  

## 📌 Copying a File from the Container to the Host  
To copy a file from a running container to the host machine, use:  This is needed when you wanted to change something in running container. After Copying the copies to the local folder and mount that files to running container like below. If you make changes to the to local file that will reflect to the running container.

```sh
winpty docker run --rm -v "//c/Users/kamin/OneDrive/Desktop/mysql-prometheus-grafana/data:/mnt" \
    nginx sh -c "cp /usr/share/nginx/html/index.html /mnt"
```
- This command runs a temporary Nginx container and copies the `index.html` file from inside the container to the mounted host directory.

## 📌 Updating Files Inside a Running Container  
To change a specific file inside a container from outside, use **volume mounting**. For example, if you want to update an `index.html` file in an Nginx container:  

```sh
docker run -d --name nginx-container -p 8090:80 \
    -v "//c/Users/kamin/OneDrive/Desktop/mysql-prometheus-grafana/data/index.html:/usr/share/nginx/html/index.html" \
    nginx
```
Here,  
- `-v <local_path>:<container_path>` mounts the local `index.html` file into the container.  
- Any changes made to `index.html` on the host system will reflect inside the container instantly.  
  

## 📌 Mounting Logs for Easy Access  
For debugging and monitoring, mount the container logs directory to a local path:  

```sh
docker run -itd --name nginx-logs-container -p 8091:80 \
    -v "//c/Users/kamin/OneDrive/Desktop/mysql-prometheus-grafana/nginx-logs:/var/log/nginx" \
    nginx
```
- This ensures all logs generated inside `/var/log/nginx` are accessible from the host system.  

### 📜 Viewing Logs in Real Time  
Use the following command to follow (stream) logs:  

```sh
docker logs -f nginx-container
```
- The `-f` flag streams logs as they are generated.  

## 🔥 Best Practices for Managing Regularly Changing Files  
- **Use Docker Volumes** for storing logs, configuration files, dependencies, and frequently updated content.  
- **Bind Mounts** are useful for quick changes, while **Named Volumes** offer better data persistence.  
- **Monitor Logs** by mounting log directories to an external location for easy access.  

By using Docker volumes effectively, you can manage configurations, track logs, and update files seamlessly without restarting or rebuilding containers. 🚀  

---

Absolutely! Here's a complete, clean, and professional section you can add to your GitHub README to explain Docker networks:

---

## 🌐 Docker Networks: What, Why, and How?

### 🔍 What is Docker Network?

A **Docker network** allows containers to communicate with each other, the host machine, and external systems. It provides connectivity, isolation, and service discovery among containers running on the same or different Docker hosts.

Using Docker networks, you can:
- Connect multiple containers for microservices.
- Isolate services for security.
- Control how containers communicate with each other and the outside world.

---

## 🧱 Types of Docker Networks

Docker supports multiple network drivers, each with different use cases:

| Network Type  | Description |
|---------------|-------------|
| **bridge** (default) | Creates a private network on the host; containers can communicate using container names. |
| **host** | Shares the host's network stack; no isolation between container and host network. |
| **overlay** | Enables communication between containers across multiple Docker hosts (used in Docker Swarm). |
| **macvlan** | Assigns MAC addresses and IPs from the physical network; containers act like real devices. |
| **none** | Disables all networking; the container has no access to network interfaces. |

---

## 🛠️ How to Create a Docker Network

To create a custom Docker bridge network:

```bash
docker network create my_custom_network
```

This will create a bridge-type network named `my_custom_network`.

---

## 🔗 How to Add a Container to a Network

You can attach a container to a network using the `--network` flag:

```bash
docker run -d --name my_app --network my_custom_network nginx
```

This connects the `nginx` container to the `my_custom_network`.

You can also connect an existing container:

```bash
docker network connect my_custom_network existing_container
```

---

## 🤔 When to Use Specific Docker Networks

| Network | Use Case |
|--------|----------|
| **bridge** | Default; use for communication between containers on the same Docker host. |
| **host** | When performance is critical or when the container must use host’s IP (e.g., running a local web server on the same ports). |
| **overlay** | For multi-host communication in Docker Swarm clusters. |
| **macvlan** | When containers need to appear as separate physical devices on the network. Useful for legacy systems. |
| **none** | When networking is not needed (for maximum isolation). |

---

## ✅ Example: Two Containers Talking Over a Network

```bash
# Create a custom bridge network
docker network create my_app_net

# Run two containers in the same network
docker run -d --name web --network my_app_net nginx
docker run -it --name tester --network my_app_net alpine sh

# Inside 'tester' container, ping 'web'
ping web
```

✔️ You’ll see a successful response because they’re on the same network.

---

By using Docker networks effectively, you can manage connectivity, security, and scalability for your containerized applications.

Let me know if you want a visual diagram or example microservices architecture with networks too!

## 🎯 Conclusion
Docker simplifies **application deployment** by packaging everything into a **container**. It is widely used for **microservices, cloud deployment, and DevOps**. With Docker, you can ensure **portability, scalability, and efficiency** across different environments.

💡 **Docker Easy!** 🐳🚀

