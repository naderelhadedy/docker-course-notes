# Dockerfile

file example:

![Course screenshot](../images/20261119194910.png)

![Course screenshot](../images/20261119141350.png)

- build > context : means the Dockerfile you need to build will exist in that context folder.

![Course screenshot](../images/20261119141525.png)

- For the network, rather than leaving everything on one network, we need it to be isolated. The frontend can communicate only with the backend, and only the backend can communicate with the database.

![Course screenshot](../images/20261119195220.png)

![Course screenshot](../images/20261119195526.png)

![Course screenshot](../images/20261119195411.png)

## Changing the root user

> Use the command `ps auxf`

- The user is root.
![Course screenshot](../images/20261119200611.png)

> Changing the owner and user

![Course screenshot](../images/20261119200338.png)
1. Created a group and a user.
2. Changed the owner of the source code file.
3. Switched to that user before executing the command.

- The user ID changed to 1001.
![Course screenshot](../images/20261119200135.png)

## Use the dependency to control the order

![Course screenshot](../images/20261119201048.png)

- `frontend` depends on `backend` and `backend` depends on `db`, so `db` starts first, then `backend` then `frontend`.

## Using healthcheck

![Course screenshot](../images/20261119202715.png)

![Course screenshot](../images/20261119202906.png)

- When a container is unhealthy, the following occurs
	- **The container keeps running.** Docker marks the container status as `(unhealthy)` in `docker ps` and fires a `health_status: unhealthy` Docker event, without killing or restarting the process.
	- **Dependent services block or abort.** If another service uses `depends_on` with `condition: service_healthy`, Docker Compose will wait until the dependency is healthy. If the dependency transitions to `unhealthy` during startup, Compose halts startup and reports an error (`dependency failed to start: container is unhealthy`).

## Protect your credentials

- using env file is unsafe at all if repo is compromised ❌

![Course screenshot](../images/20261119203141.png)

- instead, use secrets and save that file on your server ✅

![Course screenshot](../images/20261119203506.png)

> Grant the container access to the secret like this:

```yaml
services:
  db:
    image: postgres:16
    secrets:
      - db_password
```

> `.dockerignore` file prevents things from being passed to my image.

![Course screenshot](../images/20261119204543.png)

## Use multi-stage builds

- You can use a multi-stage build to separate the build from runtime and reduce the size of your Docker image.

original

![Course screenshot](../images/20261119213217.png)

optimized

![Course screenshot](../images/20261119213147.png)

> This can save time in your pipeline.

(Compare the two sizes.)
![Course screenshot](../images/20261119213329.png)

- You can use some commands to check your image for vulnerabilities like `scout` or `trivy`.
- You can limit resource usage for some apps or containers as shown below:

  ![Course screenshot](../images/20261119214221.png)

- To store your image privately, create a private repository on `docker hub` or `github container registry` or `AWS ECR` or any other platform, so you can push and pull your image from.
