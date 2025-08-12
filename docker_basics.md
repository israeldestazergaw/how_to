# Basic tools while working with docker.

## 1. Removing Docker Containers and Images

- 1. **List running containers**

> docker ps

- 2. **Stop the container**

> docker stop <container_id>

- Replace <container_id> with the ID from the first column

- 3. **Remove the container**

> docker rm <container_id>

- 4. **Remove the image**

> docker rmi <container image name>

> docker rmi postgres:15.1-alpine


- 5. One-liner to remove everything in one go (if you don’t care about other containers/images):

> docker rm -f $(docker ps -aq) && docker rmi -f $(docker images -q)
