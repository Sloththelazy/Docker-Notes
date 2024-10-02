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
Containerizing an application in Docker involves creating a Docker image of the application, which includes all the necessary components like the code, dependencies, and configurations. Below are the steps to containerize a basic Node.js application, but the process is similar for most programming languages or frameworks.

## Steps to Containerize an Application

Let’s walk through an example of how to containerize a simple **Node.js** application.

---

### 1. **Set Up the Application**

First, create a simple Node.js application if you don’t already have one.

**Example Directory Structure**:
```
my-node-app/
|-- app.js
|-- package.json
|-- Dockerfile
```

**app.js** (Sample application):
```js
// app.js
const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
  res.send('Hello, Dockerized World!');
});

app.listen(port, () => {
  console.log(`App running on port ${port}`);
});
```

**package.json** (Define the app's dependencies):
```json
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "app.js",
  "dependencies": {
    "express": "^4.17.1"
  },
  "scripts": {
    "start": "node app.js"
  }
}
```

---

### 2. **Create a `Dockerfile`**

A `Dockerfile` is a script that contains instructions for building a Docker image of your application. Create a file named `Dockerfile` in the root directory of your application.

**Sample Dockerfile**:
```Dockerfile
# 1. Use a base image that has Node.js installed
FROM node:14

# 2. Set the working directory inside the container
WORKDIR /app

# 3. Copy the package.json and package-lock.json files
COPY package*.json ./

# 4. Install dependencies
RUN npm install

# 5. Copy the application code to the container
COPY . .

# 6. Expose the application port (3000 by default)
EXPOSE 3000

# 7. Set the command to run the application
CMD ["npm", "start"]
```

- **FROM node:14**: This tells Docker to use the official Node.js 14 image as the base.
- **WORKDIR /app**: This sets `/app` as the working directory inside the container.
- **COPY package*.json ./**: This copies the `package.json` and `package-lock.json` files to the container.
- **RUN npm install**: This runs `npm install` to install dependencies.
- **COPY . .**: This copies the rest of the app’s code into the container.
- **EXPOSE 3000**: This exposes port 3000, which the app listens on.
- **CMD ["npm", "start"]**: This runs `npm start` to start the Node.js application.

---

### 3. **Build the Docker Image**

Once you have the `Dockerfile` ready, build the Docker image using the `docker build` command.

**In your terminal**:
```bash
docker build -t my-node-app .
```

- `-t my-node-app`: Tags the image with the name `my-node-app`.
- `.`: Refers to the current directory where the `Dockerfile` is located.

Docker will execute the steps in the `Dockerfile`, and after the build is complete, you’ll have a Docker image for your application.

---

### 4. **Run the Docker Container**

Now that the image is built, you can run a container based on the image using the `docker run` command.

```bash
docker run -p 4000:3000 my-node-app
```

- `-p 4000:3000`: Maps port **3000** in the container to port **4000** on the host. This allows you to access the application via `http://localhost:4000`.
- `my-node-app`: The name of the image to run.

Once the container is running, you should see output similar to:
```
App running on port 3000
```

You can now open your web browser and navigate to `http://localhost:4000` to see the message: **"Hello, Dockerized World!"**.

---

### 5. **Check Running Containers**

You can view all running containers using the `docker ps` command:
```bash
docker ps
```
This will display a list of running containers, including the one running your application.

---

### 6. **Stopping the Container**

To stop a running container, first find the **container ID** using `docker ps`, and then use `docker stop`:
```bash
docker stop <container_id>
```

---

### 7. **Push the Image to Docker Hub (Optional)**

If you want to share the image, you can push it to Docker Hub or any other container registry. Here’s how you can push it to Docker Hub.

**Step 1**: Log in to Docker Hub:
```bash
docker login
```

**Step 2**: Tag the image with your Docker Hub username:
```bash
docker tag my-node-app <your-dockerhub-username>/my-node-app
```

**Step 3**: Push the image to Docker Hub:
```bash
docker push <your-dockerhub-username>/my-node-app
```

---

### 8. **Docker Compose (Optional)**
If your application has multiple services (e.g., a web app and a database), you can use **Docker Compose** to manage them.

**Example `docker-compose.yml`**:
```yaml
version: "3"
services:
  app:
    build: .
    ports:
      - "4000:3000"
    environment:
      - NODE_ENV=production
```

Run the application with Docker Compose using:
```bash
docker-compose up
```

---

### Summary

- **Set up your application**: Ensure the application code and dependencies are in place.
- **Create a `Dockerfile`**: Define the instructions for building the Docker image.
- **Build the Docker image**: Use the `docker build` command to create the image.
- **Run the Docker container**: Use `docker run` to start a container from the image.
- **Optional steps**: Push the image to Docker Hub and use Docker Compose for multi-service setups.

By following these steps, you can containerize your application and make it portable, easily shareable, and scalable!

## Caching the Layers

**Caching layers** in Docker is an essential feature that optimizes the build process, allowing you to reuse previously built layers to speed up the creation of Docker images. Docker builds images in layers, where each instruction in the `Dockerfile` creates a new layer. Docker caches these layers and reuses them if they haven't changed between builds, reducing build times significantly.

### How Docker Layer Caching Works

When you build a Docker image, Docker executes the `Dockerfile` line by line. For each instruction, Docker checks if there’s an existing cache (from previous builds) that can be reused. If the context (like files or commands) for a layer hasn't changed, Docker reuses the cached version instead of rebuilding it from scratch. However, as soon as a change is detected, Docker rebuilds the subsequent layers.

### Key Factors Affecting Caching:
1. **Unchanged commands**: Docker reuses the cache only if the command and its context (files, dependencies) haven’t changed.
2. **Order of instructions**: Changing a single layer will invalidate all subsequent layers, so putting frequently changed instructions lower in the `Dockerfile` helps with caching.
3. **Build context**: The context includes files and directories sent to Docker during the build. If the context changes, Docker will invalidate layers that depend on those files.

---

### Best Practices for Layer Caching

1. **Separate Dependencies and Application Code**:
   - The most common optimization is to separate dependencies installation from copying the application code. This way, Docker can cache the dependencies layer unless the `package.json` (or equivalent file) changes.

   **Example (Node.js)**:
   ```Dockerfile
   # Use a base image with Node.js
   FROM node:14

   # Set the working directory
   WORKDIR /app

   # 1. Copy package.json and install dependencies (CACHEABLE)
   COPY package*.json ./
   RUN npm install

   # 2. Copy the rest of the application files (LESS CACHEABLE)
   COPY . .

   # Expose port and run the app
   EXPOSE 3000
   CMD ["npm", "start"]
   ```

   - In this example:
     - `COPY package*.json ./` and `RUN npm install` are cached if `package.json` doesn’t change.
     - `COPY . .` will be run again only if any application files change, avoiding reinstalling dependencies every time.

2. **Minimize `COPY` and `ADD` Directives**:
   - The `COPY` or `ADD` instructions reset the cache for all subsequent layers, so try to copy only what’s necessary at each stage.
   - Avoid copying unnecessary files (e.g., documentation, large assets, or temp files) by using a `.dockerignore` file.

   **Example `.dockerignore`**:
   ```
   node_modules
   npm-debug.log
   .git
   ```

3. **Install Dependencies Before Copying the Code**:
   - Copy only `package.json` (or `requirements.txt` for Python, etc.) to install dependencies first. This way, dependencies don’t get reinstalled if only the application code changes.

   **Example (Python)**:
   ```Dockerfile
   # Use a Python base image
   FROM python:3.9

   # Set the working directory
   WORKDIR /app

   # 1. Install Python dependencies
   COPY requirements.txt ./
   RUN pip install --no-cache-dir -r requirements.txt

   # 2. Copy the rest of the application code
   COPY . .

   CMD ["python", "app.py"]
   ```

   - Docker can cache the `RUN pip install` command as long as `requirements.txt` doesn't change, significantly speeding up builds.

4. **Order Layers by Frequency of Change**:
   - Place instructions that are more likely to change (e.g., copying application code) at the bottom of the `Dockerfile`. The less frequently the instruction changes, the higher it should be placed to leverage caching better.

5. **Multi-Stage Builds**:
   - For applications where you build something (like binaries or assets), you can use multi-stage builds to separate build dependencies from runtime dependencies, reducing the size of the final image and maximizing caching.

   **Example (Go application)**:
   ```Dockerfile
   # Build stage
   FROM golang:1.16 AS builder
   WORKDIR /app
   COPY go.mod ./
   RUN go mod download
   COPY . .
   RUN go build -o myapp

   # Final stage (smaller image)
   FROM alpine:latest
   WORKDIR /app
   COPY --from=builder /app/myapp .
   CMD ["./myapp"]
   ```

   - Only the build stage needs to be rebuilt if Go code changes, while the final runtime stage remains cached.

---

### Building the Image with Cache Enabled

By default, Docker uses caching during image builds. If you need to force Docker to rebuild the entire image without using the cache, you can use the `--no-cache` option.

**Example**:
```bash
docker build --no-cache -t my-node-app .
```

---

### Inspecting Docker Image Layers

You can inspect the layers of a built Docker image using the `docker history` command to see the impact of each instruction in the `Dockerfile`.

**Example**:
```bash
docker history my-node-app
```

This command shows all the layers of the image, including their size and creation time.

---

### Summary of Layer Caching Best Practices:

- **Install dependencies first**: Separate dependency installation (`npm install`, `pip install`, etc.) from copying application code to maximize caching.
- **Use `.dockerignore`**: Exclude unnecessary files to avoid cache invalidation.
- **Optimize layer order**: Place frequently changing layers (like code) at the bottom of the `Dockerfile`.
- **Use multi-stage builds**: To separate build dependencies from runtime dependencies for smaller, optimized images.
- **Check build context**: Ensure the build context is as small as possible to avoid cache invalidation.

Effective caching can significantly reduce build times, especially in CI/CD pipelines, and make development workflows smoother.

## Docker Compose
**Docker Compose** is a tool for defining and running multi-container Docker applications. It allows you to define all your application’s services (containers), networks, and volumes in a single YAML file (`docker-compose.yml`), making it easier to manage multi-container environments.

### Key Benefits of Docker Compose:
- **Manage multiple containers**: Define multiple containers in one file and manage them as a group.
- **Networking**: Docker Compose automatically sets up communication between services defined in the same file.
- **Reusable configuration**: You can reuse configurations, volumes, and networks across different environments (development, testing, production).
- **Simplified commands**: One command can start, stop, and manage multiple containers.

### Typical Use Cases:
- Applications that require multiple services, such as a web server (e.g., Node.js) and a database (e.g., MySQL, MongoDB).
- Orchestrating different components of your stack (e.g., backend API, frontend UI, databases, message queues).

---

### Basic Example of Docker Compose

Let’s create a simple application with **Node.js** and **MongoDB** services.

#### 1. **Set Up the Application**
Create a project directory with the following structure:

```
my-app/
|-- app.js
|-- package.json
|-- Dockerfile
|-- docker-compose.yml
```

**app.js** (Node.js example):
```javascript
// app.js
const express = require('express');
const mongoose = require('mongoose');
const app = express();
const port = process.env.PORT || 3000;

// Connect to MongoDB
mongoose.connect('mongodb://db:27017/mydatabase', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('Connected to MongoDB'))
  .catch(err => console.log('Failed to connect to MongoDB:', err));

app.get('/', (req, res) => {
  res.send('Hello from Node.js app!');
});

app.listen(port, () => {
  console.log(`App running on port ${port}`);
});
```

**package.json**:
```json
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "app.js",
  "dependencies": {
    "express": "^4.17.1",
    "mongoose": "^5.10.0"
  },
  "scripts": {
    "start": "node app.js"
  }
}
```

---

#### 2. **Create a `Dockerfile`**

Create a Dockerfile to containerize the Node.js application.

**Dockerfile**:
```Dockerfile
# Base image
FROM node:14

# Set working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package*.json ./
RUN npm install

# Copy the app source code
COPY . .

# Expose the application port
EXPOSE 3000

# Start the application
CMD ["npm", "start"]
```

---

#### 3. **Create a `docker-compose.yml` File**

This file will define the **Node.js app** and the **MongoDB database** as separate services.

**docker-compose.yml**:
```yaml
version: "3"
services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - PORT=3000
    depends_on:
      - db
    networks:
      - app-network

  db:
    image: mongo:latest
    ports:
      - "27017:27017"
    volumes:
      - mongo-data:/data/db
    networks:
      - app-network

volumes:
  mongo-data:

networks:
  app-network:
```

In this file:
- **app** service:
  - **build: .**: Tells Docker Compose to build the Node.js app from the current directory using the `Dockerfile`.
  - **ports: "3000:3000"**: Exposes port 3000 on both the host and the container.
  - **depends_on**: Ensures that the `db` service (MongoDB) starts before the `app` service.
  - **networks**: The app and database services are connected via a custom network (`app-network`).

- **db** service (MongoDB):
  - **image: mongo**: Pulls the official MongoDB image from Docker Hub.
  - **ports: "27017:27017"**: Exposes MongoDB’s default port.
  - **volumes**: A named volume (`mongo-data`) is used to persist MongoDB data.
  - **networks**: Shares the same network as the Node.js app.

- **volumes**: Declares the `mongo-data` volume to store MongoDB data persistently.

- **networks**: A custom network (`app-network`) is defined to allow communication between the `app` and `db` services.

---

#### 4. **Running the Application with Docker Compose**

To start the application, use the `docker-compose up` command.

```bash
docker-compose up
```

This command:
- Builds the **Node.js app** image.
- Starts both the **Node.js** and **MongoDB** containers.
- Connects the two services via the defined network (`app-network`).

---

#### 5. **Verify the Setup**

Once the application is running, you can open your browser and navigate to:

```
http://localhost:3000
```

You should see the message:
```
Hello from Node.js app!
```

The application is connected to MongoDB at `mongodb://db:27017/mydatabase`, where `db` is the hostname of the MongoDB service defined in `docker-compose.yml`.

---

#### 6. **Useful Docker Compose Commands**

- **Start containers**:
  ```bash
  docker-compose up
  ```
  Use `-d` to run in detached mode (in the background):
  ```bash
  docker-compose up -d
  ```

- **Stop containers**:
  ```bash
  docker-compose down
  ```

- **Rebuild images** (if the Dockerfile or dependencies change):
  ```bash
  docker-compose build
  ```

- **View logs from containers**:
  ```bash
  docker-compose logs
  ```

- **Scale services** (e.g., run multiple instances of a service):
  ```bash
  docker-compose up --scale app=3
  ```
  This will run three instances of the `app` service.

---

### Why Use Docker Compose?

- **Simplified Configuration**: Define your entire application stack (e.g., app, database, cache, message queue) in one file.
- **Versioning**: Different environments (like development, testing, production) can have different `docker-compose.yml` files.
- **Networking**: Automatically handles communication between services without manual networking setup.
- **Easy Scaling**: Docker Compose allows you to scale services with a single command.
- **Volume Management**: Easily manage persistent data storage between container restarts.

---

### Summary:

- **Docker Compose** is a powerful tool for managing multi-container Docker applications.
- It allows you to define services, networks, and volumes in a `docker-compose.yml` file.
- You can easily manage the lifecycle of multiple containers with simple commands (`docker-compose up`, `docker-compose down`).
- Compose is great for local development, testing environments, or small-scale production deployments.

Using Docker Compose helps manage complex setups and ensures consistent environments across development and production.

## Docker Networking
Docker networking is a key feature that enables containers to communicate with each other, either on the same host or across different hosts. Docker automatically sets up networking for containers, but you can customize and control the networks based on your needs.

### Types of Docker Networks

Docker provides several types of networks to connect containers:

1. **Bridge Network (Default)**:
   - The most common network type.
   - Each container on the same bridge network can communicate with each other by their container names or IP addresses.
   - By default, when you run a container with `docker run`, it’s attached to the `bridge` network unless specified otherwise.
   - Containers in different bridge networks can’t communicate with each other without extra configuration.

   **Use case**: Useful for containers running on a single host that need to communicate with each other, such as a web app and a database.

   **Example**:
   ```bash
   docker network create my-bridge-network
   docker run -d --name app1 --network my-bridge-network nginx
   docker run -d --name app2 --network my-bridge-network nginx
   ```
   In this example, `app1` and `app2` can communicate with each other through the `my-bridge-network` bridge network.

2. **Host Network**:
   - The container shares the host’s networking stack, meaning there’s no network isolation between the container and the host.
   - The container’s services run directly on the host machine's IP address.

   **Use case**: Useful when you need the highest performance and don’t want any network translation (e.g., for performance-critical applications).

   **Example**:
   ```bash
   docker run --network host nginx
   ```
   The NGINX container will run directly on the host’s network without its own IP address.

3. **Overlay Network**:
   - Used in **Docker Swarm** or **Kubernetes** to enable multi-host networking.
   - Allows containers on different hosts to communicate with each other securely.
   - You can create an overlay network to connect containers running on different Docker hosts.

   **Use case**: Useful for creating a multi-container, multi-host setup, such as microservices spread across different servers in a cluster.

   **Example** (in Docker Swarm mode):
   ```bash
   docker network create --driver overlay my-overlay-network
   ```
   Containers across multiple nodes in the Swarm can now communicate with each other via this overlay network.

4. **None Network**:
   - The container has no network access.
   - Useful if you want to isolate the container entirely from networking.

   **Use case**: Useful for highly secure environments or running services that don’t need networking.

   **Example**:
   ```bash
   docker run --network none nginx
   ```

5. **Macvlan Network**:
   - Allows containers to have their own MAC addresses on the physical network, essentially behaving like physical devices on the local network.
   - The container is treated as a separate device on the network with its own IP.

   **Use case**: Useful when you need full control over the network setup or want containers to behave like physical devices on the network.

   **Example**:
   ```bash
   docker network create -d macvlan \
   --subnet=192.168.1.0/24 \
   --gateway=192.168.1.1 \
   -o parent=eth0 my-macvlan-network
   ```

---

### Networking in Docker Compose

In **Docker Compose**, you can define custom networks, and services will automatically be connected to these networks.

#### Example: Custom Docker Compose Network

**docker-compose.yml**:
```yaml
version: "3"
services:
  app:
    image: nginx
    networks:
      - frontend
      - backend

  db:
    image: mongo
    networks:
      - backend

networks:
  frontend:
  backend:
```

- **app** is connected to both the `frontend` and `backend` networks.
- **db** is connected only to the `backend` network.
- **frontend** and **backend** are custom networks created by Docker Compose.

**Running the Compose file**:
```bash
docker-compose up
```

In this setup, the `app` service can communicate with both the `frontend` and `backend` networks, while the `db` service can only communicate with the `backend` network.

---

### Inspecting Docker Networks

To view and inspect Docker networks, you can use the following commands:

1. **List networks**:
   ```bash
   docker network ls
   ```
   This command will list all Docker networks, including `bridge`, `host`, `none`, and any custom networks you've created.

2. **Inspect a network**:
   ```bash
   docker network inspect <network_name>
   ```
   This command provides detailed information about a specific network, including the connected containers and their IP addresses.

3. **Connect a container to a network**:
   ```bash
   docker network connect <network_name> <container_name>
   ```
   Use this to manually connect a running container to a network.

4. **Disconnect a container from a network**:
   ```bash
   docker network disconnect <network_name> <container_name>
   ```

---

### Exposing Ports and Networking

Docker containers have internal ports that need to be mapped to the host machine to be accessible. This is done using the `-p` flag with the `docker run` command or in `docker-compose.yml`.

**Example**: Exposing an internal container port (`80`) to a host port (`8080`):
```bash
docker run -d -p 8080:80 nginx
```
- This command maps port 8080 on the host to port 80 inside the container, making the NGINX web server accessible on `http://localhost:8080`.

---

### Example: Networking in Action

Let’s create a multi-container setup using Docker Compose that involves a **web application** (Node.js) and a **database** (MongoDB) communicating over a Docker network.

**docker-compose.yml**:
```yaml
version: "3.7"
services:
  web:
    image: node:14
    command: node app.js
    volumes:
      - ./app:/app
    working_dir: /app
    ports:
      - "3000:3000"
    networks:
      - webnet

  db:
    image: mongo
    networks:
      - webnet

networks:
  webnet:
```

- Both `web` (Node.js) and `db` (MongoDB) services are connected via the `webnet` network.
- The Node.js app can connect to MongoDB at the hostname `db` on the `webnet` network.

To run this setup, simply execute:
```bash
docker-compose up
```

---

### Summary of Docker Networking Concepts

- **Bridge Network**: Default network, isolates containers, but allows communication between containers on the same network.
- **Host Network**: The container shares the host's network stack directly.
- **Overlay Network**: Enables communication between containers on different Docker hosts (multi-host).
- **Macvlan Network**: Assigns a MAC address to the container, allowing it to appear as a physical device on the network.
- **Networking in Docker Compose**: Easily set up custom networks for multi-container applications.

Docker networking allows containers to communicate in flexible and secure ways, whether they are on the same host or spread across a distributed cluster.

# Volumes

**Volume mounting** in Docker is a powerful feature that allows you to persist data generated by and used by Docker containers. Unlike the container's filesystem, which is ephemeral and disappears when the container is removed, volumes provide a way to store data outside of the container’s lifecycle.

### Key Benefits of Using Docker Volumes

1. **Data Persistence**: Volumes keep data safe even when containers are stopped or deleted, making it ideal for databases or other applications that require persistent storage.
2. **Performance**: Volumes are optimized for performance, as they bypass the container's filesystem and are managed by Docker.
3. **Ease of Backup and Restore**: You can easily back up or migrate volumes.
4. **Sharing Data Between Containers**: Multiple containers can access the same volume, making it easy to share data.
5. **Better Management**: Volumes can be managed more easily than files in containers.

### Types of Mounts in Docker

Docker supports three types of mounts:

1. **Volumes**: Managed by Docker and stored in a part of the host filesystem which is managed by Docker (`/var/lib/docker/volumes/` by default). They are preferred for persistent storage.

2. **Bind Mounts**: Directly link a host file or directory to a container file or directory. Changes made in either the host or the container are reflected in the other.

3. **tmpfs Mounts**: Store data in the host system's memory only, making it ephemeral. It is useful for sensitive information that doesn’t need to persist.

### Using Docker Volumes

#### Creating a Volume

You can create a volume using the `docker volume create` command:

```bash
docker volume create my-volume
```

#### Mounting a Volume to a Container

You can mount a volume to a container when running it using the `-v` or `--mount` option. 

1. **Using the `-v` flag**:

```bash
docker run -d \
  --name my-container \
  -v my-volume:/data \
  nginx
```

- In this example, the volume `my-volume` is mounted to the `/data` directory inside the container.

2. **Using the `--mount` flag**:

```bash
docker run -d \
  --name my-container \
  --mount source=my-volume,target=/data \
  nginx
```

- This achieves the same result as the previous command but uses a more explicit syntax.

#### Inspecting a Volume

You can inspect the details of a volume using:

```bash
docker volume inspect my-volume
```

This command will show you information like the mountpoint, creation date, and any labels associated with the volume.

#### Listing All Volumes

To list all existing volumes on your system, use:

```bash
docker volume ls
```

#### Removing a Volume

To remove a volume, use:

```bash
docker volume rm my-volume
```

**Note**: You can only remove volumes that are not currently being used by a container. To remove all unused volumes, you can run:

```bash
docker volume prune
```

### Using Bind Mounts

Bind mounts allow you to specify an exact path on the host to link to the container. This is useful for development purposes, as it allows you to edit files on your host and see changes in the container immediately.

**Example**:
```bash
docker run -d \
  --name my-container \
  -v /path/on/host:/path/in/container \
  nginx
```

In this example, `/path/on/host` is a directory on the host machine, and `/path/in/container` is where it will be accessible inside the container.

### Using tmpfs Mounts

To create a tmpfs mount, use the `--tmpfs` option:

```bash
docker run -d \
  --name my-container \
  --tmpfs /tmp \
  nginx
```

In this case, the `/tmp` directory inside the container is mounted as a tmpfs, meaning it will not persist data after the container is stopped.

### Example: Using Volumes with Docker Compose

You can define volumes directly in your `docker-compose.yml` file for easier management of services.

**docker-compose.yml**:
```yaml
version: "3.8"

services:
  web:
    image: nginx
    volumes:
      - web-data:/usr/share/nginx/html
    ports:
      - "8080:80"

volumes:
  web-data:
```

In this example:
- The `web` service uses a volume called `web-data` to persist web content in the `/usr/share/nginx/html` directory.
- The volume `web-data` is defined at the bottom of the file, allowing Docker Compose to manage it automatically.

### Running the Docker Compose File

To start the services defined in the `docker-compose.yml` file, run:

```bash
docker-compose up
```

### Summary

- **Volumes**: Docker-managed storage, best for persistent data.
- **Bind Mounts**: Directly link host directories or files with containers, useful for development.
- **tmpfs Mounts**: Temporary storage in memory for ephemeral data.

Using volume mounting is crucial for managing stateful applications in Docker, ensuring data persistence and efficient data sharing between containers.
## Multi-Stage Build
**Multi-stage builds** in Docker allow you to create smaller, more efficient images by separating the build environment from the runtime environment. This technique reduces the final image size and minimizes the number of dependencies included in the image, leading to faster deployments and better security.

### Key Benefits of Multi-Stage Builds

1. **Smaller Image Sizes**: By copying only the necessary files from the build stage to the final image, you can significantly reduce the size of your Docker images.
2. **Improved Security**: Smaller images mean fewer potential vulnerabilities, as unnecessary packages and files are not included in the final image.
3. **Cleaner Build Process**: You can have multiple build steps without cluttering the final image with build tools and dependencies.

### How Multi-Stage Builds Work

In a multi-stage build, you define multiple `FROM` statements in a single `Dockerfile`. Each `FROM` creates a new stage, and you can specify which files to copy from one stage to another.

### Example: Building a Node.js Application

Let's walk through an example of a multi-stage build for a Node.js application.

#### Directory Structure

```
my-node-app/
|-- Dockerfile
|-- package.json
|-- app.js
```

**app.js** (Simple Node.js application):
```javascript
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello from Node.js app!');
});

app.listen(port, () => {
  console.log(`App running on port ${port}`);
});
```

**package.json**:
```json
{
  "name": "my-node-app",
  "version": "1.0.0",
  "main": "app.js",
  "dependencies": {
    "express": "^4.17.1"
  },
  "scripts": {
    "start": "node app.js"
  }
}
```

#### Dockerfile with Multi-Stage Build

Here’s how you can create a `Dockerfile` that utilizes multi-stage builds:

```Dockerfile
# Stage 1: Build the application
FROM node:14 AS builder

# Set the working directory
WORKDIR /app

# Copy package.json and install dependencies
COPY package.json ./
RUN npm install

# Copy the rest of the application source code
COPY . .

# Build the application (if needed)
# RUN npm run build

# Stage 2: Create the final image
FROM node:14

# Set the working directory in the final image
WORKDIR /app

# Copy only the necessary files from the builder stage
COPY --from=builder /app .

# Expose the application port
EXPOSE 3000

# Command to run the application
CMD ["npm", "start"]
```

### Explanation of the Dockerfile

1. **Stage 1: Builder Stage**:
   - The first `FROM node:14 AS builder` sets up the builder environment.
   - The working directory is set to `/app`, and the `package.json` file is copied.
   - The `RUN npm install` command installs the dependencies.
   - The rest of the application code is copied into the container.

2. **Stage 2: Final Image**:
   - The second `FROM node:14` sets up the final runtime environment.
   - The working directory is set to `/app` again.
   - The line `COPY --from=builder /app .` copies only the built application files from the builder stage into the final image.
   - The `EXPOSE` instruction specifies the port on which the application will run.
   - Finally, the command to run the application is defined with `CMD`.

### Building the Docker Image

To build the Docker image with the multi-stage build, run:

```bash
docker build -t my-node-app .
```

### Running the Application

Once the image is built, you can run the application with:

```bash
docker run -d -p 3000:3000 my-node-app
```

### Verifying the Application

You can check if the application is running by visiting:

```
http://localhost:3000
```

You should see the message:
```
Hello from Node.js app!
```

### Best Practices for Multi-Stage Builds

1. **Minimize the Number of Layers**: Combine commands when possible to reduce the number of layers and make the image smaller.
2. **Only Copy Necessary Files**: In the final stage, only copy the files needed to run the application, excluding development dependencies and files.
3. **Use Specific Base Images**: Specify the version of base images (like `node:14`) to avoid unexpected changes when the base image is updated.
4. **Use Build Arguments**: If you need to pass dynamic values during the build process, use `ARG` and `ENV` for build arguments.

### Summary

- **Multi-stage builds** allow you to create smaller and more secure Docker images by separating the build environment from the runtime environment.
- You define multiple stages in a single `Dockerfile` using multiple `FROM` statements, allowing you to copy only necessary files to the final image.
- This approach is particularly useful for applications built with frameworks like Node.js, Go, or Java, where the build process often generates additional files that are not needed in production.
