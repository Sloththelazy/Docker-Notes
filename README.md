# Docker-Notes
Docker is widely used for its ability to streamline the development, deployment, and management of applications. Here are some of the key reasons for using Docker:

### 1. **Consistency Across Environments**
   Docker containers package everything needed to run an application, including its dependencies, libraries, and configuration files. This ensures that the application behaves the same in different environments (e.g., development, staging, production).

### 2. **Portability**
   Docker containers are platform-independent, meaning they can run on any system that supports Docker. Whether on your local machine, a server, or a cloud platform, the container will behave the same.

### 3. **Isolation**
   Each Docker container runs in its own isolated environment. This helps prevent conflicts between applications or different versions of dependencies.

### 4. **Efficient Resource Usage**
   Containers share the host system’s OS kernel and resources, making them much more lightweight compared to traditional virtual machines (VMs), which need separate guest OSes. This leads to faster startup times and better resource efficiency.

### 5. **Simplified Deployment**
   Docker images can be versioned and stored in repositories (such as Docker Hub), making it easy to roll out, update, or roll back applications. Teams can share images and ensure everyone is using the same version.

### 6. **Microservices Architecture Support**
   Docker is ideal for microservices architectures, where applications are broken down into smaller, independent services. Each microservice can run in its own container, and Docker makes it easier to manage and scale these services.

### 7. **Rapid Development and Testing**
   Developers can quickly create Docker images with the necessary environment to test different application configurations or versions. This allows for faster iterations and more efficient testing.

### 8. **Improved Security**
   Docker containers provide an additional layer of security by isolating applications from each other and the host system. While not completely foolproof, this helps limit the impact of security vulnerabilities.

### 9. **Scalability**
   Docker works well with orchestration tools like Kubernetes, which makes scaling applications across multiple containers and hosts seamless. This is especially valuable for large-scale, distributed applications.

### 10. **DevOps and CI/CD**
   Docker is heavily used in modern DevOps workflows, allowing for continuous integration and continuous deployment (CI/CD) by automating the creation, testing, and deployment of containers. This streamlines the overall software delivery process.

### Conclusion:
Docker simplifies the complexities of managing applications, particularly in environments where consistency, efficiency, and scalability are key. It has become an essential tool for developers and operations teams alike.

## Images vs Containers
In Docker, **images** and **containers** are two fundamental concepts, and they serve different purposes. Here’s a comparison to clarify their roles:

### **1. Definition**
- **Image**: 
  - A Docker image is a lightweight, standalone, executable package that includes everything needed to run a piece of software (code, runtime, libraries, environment variables, and configuration files).
  - It is essentially a **template** for creating containers.
  - Images are **static** and **read-only**.

- **Container**: 
  - A Docker container is a **runtime instance** of a Docker image. It’s what you get when you execute (`run`) an image.
  - Containers are **dynamic** and **modifiable** (they can be stopped, started, modified, or deleted).

### **2. Lifespan**
- **Image**: 
  - Images are immutable and do not change once created.
  - You can store an image and use it multiple times to create containers.

- **Container**: 
  - Containers have a lifecycle: they can be started, stopped, paused, and destroyed.
  - When a container is destroyed, any modifications made inside the container (that aren't persisted externally) are lost.

### **3. Purpose**
- **Image**: 
  - Acts as a blueprint for creating containers.
  - Can be shared and reused across different systems (stored in repositories like Docker Hub).

- **Container**: 
  - Acts as a running instance of an image where actual application execution happens.
  - Provides an isolated environment to run your software.

### **4. Example**
- **Image**: 
  - Let’s say you have an image of a Node.js application. This image contains the Node.js runtime, your application code, and any dependencies required.
  
- **Container**: 
  - When you run the Node.js image, Docker creates a container (runtime instance) from that image, and your application will run inside this container.

### **5. Storage**
- **Image**: 
  - Stored in **layers** that can be cached and shared between images, making Docker images very efficient in terms of disk space.

- **Container**: 
  - Containers have their own storage, but by default, changes to the container (e.g., installed software or modified files) do not affect the underlying image unless committed to create a new image.

### **6. Modification**
- **Image**: 
  - You cannot modify an image directly. If you want to make changes, you either create a new image or create a container, make the changes, and then commit the container to a new image.
  
- **Container**: 
  - Containers can be modified during their lifecycle (e.g., files can be added, removed, or modified).

### **7. Versioning**
- **Image**: 
  - Docker images can be versioned (tags can be applied), so you can maintain different versions of the same image.

- **Container**: 
  - Containers are not versioned. Each container is a disposable and isolated instance of an image.

### **8. Execution**
- **Image**: 
  - An image is not running by itself—it’s simply a static file system snapshot and metadata.

- **Container**: 
  - A container is the execution of an image in a lightweight, isolated environment. It runs as a process on your host system with its own CPU, memory, file system, and networking.

### Summary:

| Aspect              | Image                                      | Container                               |
|---------------------|--------------------------------------------|-----------------------------------------|
| **Nature**          | Blueprint or template                      | Runtime instance of an image            |
| **State**           | Static, read-only                          | Dynamic, modifiable                     |
| **Lifecycle**       | Persistent                                 | Temporary, with a lifecycle             |
| **Purpose**         | Provides the environment and dependencies  | Runs the application in isolated space  |
| **Storage**         | Stored in layers, shared across systems    | Temporary storage unless persisted      |
| **Modification**    | Immutable                                  | Can be modified but changes are lost when destroyed |
| **Versioning**      | Versioned with tags                        | Not versioned                           |
| **Execution**       | Cannot run on its own                      | Runs as an isolated process             |

In short, Docker **images** are used to create **containers**, and containers are the actual execution environments where your application runs.

## Docker Commands

Here is a list of essential Docker commands that a beginner should know, along with a short description and example use cases:

### 1. **`docker --version`**
   - **Description**: Shows the Docker version installed on your system.
   - **Example**:
     ```bash
     docker --version
     ```

### 2. **`docker pull`**
   - **Description**: Downloads a Docker image from a registry (like Docker Hub).
   - **Example**:
     ```bash
     docker pull nginx
     ```

### 3. **`docker images`**
   - **Description**: Lists all Docker images on your system.
   - **Example**:
     ```bash
     docker images
     ```

### 4. **`docker run`**
   - **Description**: Runs a container from a Docker image.
   - **Example**:
     ```bash
     docker run nginx
     ```
     - Run a container interactively:
     ```bash
     docker run -it ubuntu bash
     ```

### 5. **`docker ps`**
   - **Description**: Lists running containers.
   - **Example**:
     ```bash
     docker ps
     ```
   - List all containers (including stopped ones):
     ```bash
     docker ps -a
     ```

### 6. **`docker start`**
   - **Description**: Starts a stopped container.
   - **Example**:
     ```bash
     docker start <container_id>
     ```

### 7. **`docker stop`**
   - **Description**: Stops a running container.
   - **Example**:
     ```bash
     docker stop <container_id>
     ```

### 8. **`docker rm`**
   - **Description**: Removes a container.
   - **Example**:
     ```bash
     docker rm <container_id>
     ```

### 9. **`docker rmi`**
   - **Description**: Removes a Docker image.
   - **Example**:
     ```bash
     docker rmi <image_id>
     ```

### 10. **`docker exec`**
   - **Description**: Runs a command inside a running container.
   - **Example**:
     ```bash
     docker exec -it <container_id> bash
     ```
     - This starts a bash shell inside the running container.

### 11. **`docker build`**
   - **Description**: Builds a Docker image from a `Dockerfile`.
   - **Example**:
     ```bash
     docker build -t my-app .
     ```

### 12. **`docker logs`**
   - **Description**: Shows the logs of a running container.
   - **Example**:
     ```bash
     docker logs <container_id>
     ```

### 13. **`docker stop $(docker ps -q)`**
   - **Description**: Stops all running containers.
   - **Example**:
     ```bash
     docker stop $(docker ps -q)
     ```

### 14. **`docker network ls`**
   - **Description**: Lists Docker networks.
   - **Example**:
     ```bash
     docker network ls
     ```

### 15. **`docker network create`**
   - **Description**: Creates a Docker network.
   - **Example**:
     ```bash
     docker network create my-network
     ```

### 16. **`docker volume ls`**
   - **Description**: Lists Docker volumes.
   - **Example**:
     ```bash
     docker volume ls
     ```

### 17. **`docker inspect`**
   - **Description**: Shows detailed information about a container or image.
   - **Example**:
     ```bash
     docker inspect <container_id>
     ```

### 18. **`docker-compose up`**
   - **Description**: Starts and runs containers defined in a `docker-compose.yml` file.
   - **Example**:
     ```bash
     docker-compose up
     ```

### 19. **`docker-compose down`**
   - **Description**: Stops and removes containers, networks, and volumes created by `docker-compose up`.
   - **Example**:
     ```bash
     docker-compose down
     ```

### 20. **`docker tag`**
   - **Description**: Tags an image with a new name or version.
   - **Example**:
     ```bash
     docker tag <image_id> my-app:1.0
     ```

### 21. **`docker push`**
   - **Description**: Pushes an image to a Docker registry (like Docker Hub).
   - **Example**:
     ```bash
     docker push my-app:1.0
     ```

### 22. **`docker login`**
   - **Description**: Logs in to a Docker registry (like Docker Hub).
   - **Example**:
     ```bash
     docker login
     ```

### 23. **`docker commit`**
   - **Description**: Creates a new image from a container’s changes.
   - **Example**:
     ```bash
     docker commit <container_id> my-new-image
     ```

### 24. **`docker export`**
   - **Description**: Exports a container’s file system as a tar archive.
   - **Example**:
     ```bash
     docker export <container_id> > container-backup.tar
     ```

### 25. **`docker import`**
   - **Description**: Creates an image from a tarball archive.
   - **Example**:
     ```bash
     docker import container-backup.tar my-new-image
     ```

### Summary Table

| Command                | Description                                       | Example                                               |
|------------------------|---------------------------------------------------|-------------------------------------------------------|
| `docker --version`      | Check Docker version                              | `docker --version`                                    |
| `docker pull`           | Download an image                                 | `docker pull nginx`                                   |
| `docker images`         | List images                                       | `docker images`                                       |
| `docker run`            | Run a container                                   | `docker run nginx`                                    |
| `docker ps`             | List running containers                           | `docker ps`                                           |
| `docker start`          | Start a stopped container                         | `docker start <container_id>`                         |
| `docker stop`           | Stop a running container                          | `docker stop <container_id>`                          |
| `docker rm`             | Remove a container                                | `docker rm <container_id>`                            |
| `docker rmi`            | Remove an image                                   | `docker rmi <image_id>`                               |
| `docker exec`           | Run a command in a running container              | `docker exec -it <container_id> bash`                 |
| `docker build`          | Build an image from a Dockerfile                  | `docker build -t my-app .`                            |
| `docker logs`           | View container logs                               | `docker logs <container_id>`                          |
| `docker stop $(docker ps -q)` | Stop all running containers                 | `docker stop $(docker ps -q)`                         |
| `docker network ls`     | List Docker networks                              | `docker network ls`                                   |
| `docker network create` | Create a Docker network                           | `docker network create my-network`                    |
| `docker volume ls`      | List Docker volumes                               | `docker volume ls`                                    |
| `docker inspect`        | Inspect a container or image                      | `docker inspect <container_id>`                       |
| `docker-compose up`     | Run containers from a Compose file                | `docker-compose up`                                   |
| `docker-compose down`   | Stop and remove containers from Compose file      | `docker-compose down`                                 |
| `docker tag`            | Tag an image                                      | `docker tag <image_id> my-app:1.0`                    |
| `docker push`           | Push an image to a registry                       | `docker push my-app:1.0`                              |
| `docker login`          | Login to Docker registry                          | `docker login`                                        |
| `docker commit`         | Create a new image from container changes         | `docker commit <container_id> my-new-image`           |
| `docker export`         | Export container filesystem as a tar archive      | `docker export <container_id> > container-backup.tar` |
| `docker import`         | Import a tar archive to create a new image        | `docker import container-backup.tar my-new-image`     |

These commands are the foundation of working with Docker and will help you get started with building, running, managing, and deploying containers.

## Docker Port Mapping

Docker port mapping is the process of linking ports on a Docker container to ports on the host machine, allowing external access to services running inside the container. When running an application inside a Docker container, it operates in an isolated environment, and to interact with it from outside the container, you need to map the container’s internal ports to the host system's ports.

### Syntax:
To map a port, you use the `-p` or `--publish` option when running the `docker run` command. The general syntax is:
```bash
docker run -p <host_port>:<container_port> <image_name>
```

- **`host_port`**: The port on the host (your local machine or server).
- **`container_port`**: The port inside the container where the service is running.

### Examples:

#### 1. **Simple Port Mapping**
   Let’s say you want to run an **nginx** web server inside a Docker container, which listens on port 80 inside the container. To make it accessible on port 8080 on your host, you can map the ports as follows:
   ```bash
   docker run -p 8080:80 nginx
   ```
   - This maps the host's port **8080** to the container's port **80**. You can now access the nginx server by going to `http://localhost:8080` in your web browser.

#### 2. **Multiple Port Mapping**
   You can map multiple ports between the host and container. For example, if an application in the container uses both HTTP (port 80) and HTTPS (port 443), you can map both:
   ```bash
   docker run -p 8080:80 -p 8443:443 nginx
   ```
   - This maps:
     - Host port **8080** to container port **80** (for HTTP).
     - Host port **8443** to container port **443** (for HTTPS).

#### 3. **Random Host Port Mapping**
   Docker can also assign a random port on the host side, which can be useful in certain scenarios where you don't care which host port is used. To allow Docker to select a random host port, you can omit the `host_port`:
   ```bash
   docker run -p 80 nginx
   ```
   - Docker will randomly choose an available port on the host and map it to port **80** of the container. You can see the assigned port using the `docker ps` command or by inspecting the container.

#### 4. **Specifying the Host IP Address**
   You can bind the port to a specific network interface (IP address) on the host. By default, Docker binds the ports to all interfaces (`0.0.0.0`). To bind to a specific IP address, use:
   ```bash
   docker run -p 127.0.0.1:8080:80 nginx
   ```
   - This maps the container’s port **80** to host port **8080**, but only binds it to the **127.0.0.1** loopback interface. It will only be accessible locally and not from external machines.

### Checking Port Mappings:

To see the port mappings of a running container, you can use:

1. **`docker ps`**: Lists the port mappings for all running containers.
   ```bash
   docker ps
   ```
   The output will include columns like `PORTS`, showing which ports are mapped from the container to the host, e.g., `0.0.0.0:8080->80/tcp`.

2. **`docker port`**: Shows the port mappings for a specific container.
   ```bash
   docker port <container_id>
   ```
   Example output:
   ```
   80/tcp -> 0.0.0.0:8080
   ```

### Summary:
- **Port mapping** allows you to expose services running inside a container to the outside world.
- Use the `-p` flag with the format `-p <host_port>:<container_port>`.
- You can bind to specific IP addresses or let Docker assign a random port on the host.
- Use `docker ps` or `docker port` to check the current mappings.

Port mapping is crucial for making Docker containers accessible and integrating them with the external environment.

## Port Exposing

Docker **port exposing** refers to making a port available for communication inside a container or between containers. This is different from **port mapping**, which makes the container’s port accessible from the host or external networks.

### Key Differences:
- **Port exposing**:
  - Opens a port inside the container and allows other containers (in the same Docker network) to communicate with it.
  - Does **not** automatically allow external (host) access to the container unless a specific **port mapping** is also defined.
  
- **Port mapping**:
  - Binds a container’s port to a port on the host machine, allowing external access to the container from outside Docker.

### How to Expose Ports in Docker

1. **Expose Ports in the `Dockerfile`**:
   You can define which ports your container will use by specifying them in a `Dockerfile` using the `EXPOSE` instruction. This is a **declarative** way to let others know which port(s) your application listens on.

   Example `Dockerfile`:
   ```Dockerfile
   FROM nginx
   EXPOSE 80
   EXPOSE 443
   ```
   - This exposes ports **80** (HTTP) and **443** (HTTPS) inside the container, meaning the container can receive traffic on these ports from other containers, but not from the host unless you explicitly map the ports during the container run.

2. **Expose Ports Using `docker run --expose`**:
   You can also expose ports when you start a container using the `--expose` option. This is done in cases where you don’t want to modify the `Dockerfile`, but you still want to make the port accessible inside the container.

   Example:
   ```bash
   docker run --expose 8080 nginx
   ```
   - This command exposes port **8080** inside the container, making it available for communication with other containers on the same network.

### Communication Between Containers Using Exposed Ports

When two or more containers are running in the same Docker network, they can communicate with each other through the exposed ports.

#### Example:
1. **Create a Docker Network**:
   Create a custom bridge network to allow the containers to communicate.
   ```bash
   docker network create my-network
   ```

2. **Run a Container and Expose a Port**:
   Run an Nginx container and expose port 80.
   ```bash
   docker run --expose 80 --network my-network --name my-nginx nginx
   ```

3. **Run Another Container in the Same Network**:
   Run another container in the same network, such as a busybox container, to test communication.
   ```bash
   docker run --rm -it --network my-network busybox
   ```

4. **Communicate Between Containers**:
   Inside the `busybox` container, you can use `wget` or `curl` to access the exposed port of the `my-nginx` container.
   ```bash
   wget -qO- http://my-nginx:80
   ```
   - Since both containers are in the same network, they can communicate using the exposed port **80** of the `my-nginx` container.

### Exposing Ports and Port Mapping Together

To expose a port **and** make it accessible from the host (outside Docker), you can combine both port exposing and port mapping. For instance:

```bash
docker run -p 8080:80 --expose 80 nginx
```
- **Expose** port **80** inside the container.
- **Map** port **80** inside the container to port **8080** on the host. This allows external access via `http://localhost:8080`.

### Summary of Exposing vs Mapping Ports:
- **Exposing ports**: Opens ports inside the container for internal communication between containers in the same network. It does not make the service accessible from the host machine.
- **Port mapping**: Binds a container’s port to a port on the host, making it accessible from the host machine or external networks.

Exposing ports is useful for communication between containers, while port mapping is required when you want to access the container’s service from the outside world (e.g., your browser or another external system).

## What Are Environment Variables in Docker?

**Environment variables** are key-value pairs that are used to pass configuration values into your application or system. In Docker, environment variables allow you to configure a container's behavior at runtime without hardcoding those values inside the container image.

They are commonly used to:
- Set application settings (like database credentials, API keys, or environment types like `production`, `development`, etc.).
- Make containerized applications more portable and configurable.
- Ensure sensitive information like passwords isn't stored in Docker images.

### How to Pass Environment Variables in Docker

Docker allows you to pass environment variables to containers in several ways:

---

#### 1. **Using `-e` or `--env` in `docker run`**
You can pass environment variables when starting a container using the `-e` or `--env` option in the `docker run` command.

**Syntax**:
```bash
docker run -e VARIABLE_NAME=value <image>
```

**Example**:
```bash
docker run -e NODE_ENV=production -e DB_HOST=localhost my-node-app
```
- This passes two environment variables (`NODE_ENV` and `DB_HOST`) to the container running the `my-node-app` image.
- Inside the container, the environment variable `NODE_ENV` will be set to `production`, and `DB_HOST` will be set to `localhost`.

---

#### 2. **Using an `.env` File**
You can store environment variables in a separate file (typically named `.env`) and pass them to Docker using the `--env-file` option. This method is cleaner when dealing with many variables, especially for sensitive values like passwords.

**Syntax**:
```bash
docker run --env-file <file_name> <image>
```

**Example `.env` file**:
```
NODE_ENV=production
DB_HOST=localhost
DB_USER=admin
DB_PASSWORD=secretpassword
```

**Example Command**:
```bash
docker run --env-file ./my-env-file.env my-node-app
```
- This command loads all the environment variables from the `my-env-file.env` file and passes them to the container.

---

#### 3. **Setting Environment Variables in `Dockerfile`**
You can set default environment variables in a `Dockerfile` using the `ENV` instruction. These environment variables are built into the image, so any container started from the image will inherit them by default.

**Syntax in a `Dockerfile`**:
```Dockerfile
ENV VARIABLE_NAME=value
```

**Example `Dockerfile`**:
```Dockerfile
FROM node:14

# Set default environment variable
ENV NODE_ENV=production
ENV DB_HOST=localhost

# Copy application files and install dependencies
COPY . /app
WORKDIR /app
RUN npm install

CMD ["npm", "start"]
```
- In this example, `NODE_ENV` is set to `production` and `DB_HOST` is set to `localhost` by default.

**Note**: Environment variables set using `docker run` or an `.env` file will **override** those set in the `Dockerfile`.

---

#### 4. **Using `docker-compose.yml` to Pass Environment Variables**
If you're using **Docker Compose**, you can pass environment variables through the `docker-compose.yml` file either directly or via an `.env` file.

##### Directly in `docker-compose.yml`
```yaml
version: "3"
services:
  app:
    image: my-node-app
    environment:
      - NODE_ENV=production
      - DB_HOST=localhost
```
- This defines the environment variables `NODE_ENV` and `DB_HOST` for the `app` service.

##### Using an `.env` File with Docker Compose
You can use an `.env` file with Docker Compose to pass environment variables.

**Example `.env` file**:
```
NODE_ENV=production
DB_HOST=localhost
```

**docker-compose.yml**:
```yaml
version: "3"
services:
  app:
    image: my-node-app
    env_file:
      - ./my-env-file.env
```
- The `env_file` directive tells Docker Compose to load the environment variables from the specified `.env` file.

---

### Inspecting Environment Variables in a Running Container

Once a container is running, you can view the environment variables using the `docker exec` command.

**Example**:
```bash
docker exec <container_id> env
```
- This lists all environment variables set inside the running container.

You can also inspect a container’s configuration, including environment variables, using:
```bash
docker inspect <container_id>
```
Look for the `Env` section in the output, which will display all the environment variables passed to the container.

---

### Order of Precedence

When Docker sets environment variables, it follows this precedence (from highest to lowest):
1. **Values passed via `docker run -e` or `--env-file`.**
2. **Values defined in the `docker-compose.yml` file.**
3. **Values set via the `ENV` directive in the `Dockerfile`.**

This means that if you define an environment variable in multiple places, Docker will use the value from the highest precedence location.

---

### Summary:
- Environment variables are used to configure applications running in Docker containers.
- You can pass environment variables using `-e`, an `.env` file, in a `Dockerfile`, or via `docker-compose.yml`.
- Docker supports overriding default environment variables, and inspecting them is easy using `docker exec` or `docker inspect`.

Environment variables make Docker containers highly configurable and flexible, allowing for easy adjustments of settings between different environments (development, testing, production, etc.).
