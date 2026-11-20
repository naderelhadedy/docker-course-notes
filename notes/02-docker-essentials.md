# Docker Essentials: Basic Commands & Container Management

## 1. Container Execution & Lifecycle Management

* **`docker run` / `docker container run`**: Creates and starts a container from a specified image.

  * **`-i`**: Keeps STDIN open for interactive mode.

  * **`-t`**: Allocates a pseudo-TTY terminal session.

  * **`-it`**: Combines interactive and terminal flags (e.g., `docker run -it ubuntu bash`).

  * **`-d`**: Runs the container in **detached mode** (in the background).

  * **`-p <host_port>:<container_port>`**: Maps a port on the host machine to a port inside the container (e.g., `-p 8080:80`).

  * **`--name <name>`**: Assigns a custom name to the container.

  * **`--rm`**: Automatically deletes the container upon exit.

* **`docker ps` / `docker container ls` / `docker container ps`**: Lists active running containers.

  * **`-a` / `--all`**: Shows all containers, including stopped, exited, or crashed ones.

* **`docker stop`**: Stops a running container cleanly.

* **`docker rm`**: Deletes a stopped container.

  * **`-f` / `--force`**: Forcefully stops and removes a running container in one step.

---

## 2. Image Operations

* **`docker images` / `docker image ls`**: Lists all locally cached Docker images on your machine.

* **`docker pull`**: Downloads an image from a container registry (such as Docker Hub).

* **`docker commit`**: Saves changes made to a running container as a new custom Docker image.

  * **`-m`**: Specifies a commit message.

  * **`-a`**: Sets the author name.

  * **`--help`**: Displays available flags and options for committing.

---

## 3. Debugging, Inspection & File Management

* **`docker exec`**: Executes a new command inside a running container (e.g., opening an interactive shell: `docker exec -it <container_id> bash` or `sh`).

* **`docker logs`**: Retrieves and views standard logs output by a container.

  * **`-f`**: Continuously streams/follows logs in real-time.

* **`docker cp`**: Copies files or directories between the host filesystem and a container in either direction.

* **`docker stats`**: Displays a live streaming view of container resource consumption (CPU %, memory usage, limits, and process IDs).

* **`docker info`**: Shows engine-wide status, including total counts of containers (running, paused, stopped), local images, and system architecture details.
