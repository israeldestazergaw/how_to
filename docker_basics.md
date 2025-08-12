# Basic tools while working with docker.

## 1. Removing Docker Containers and Images

- 1. **List running containers**

    - docker ps

    - docker ps -a

    - docker images

    - docker image ls

- 2. **Stop the container**

    - docker stop <container_id>

    - Replace <container_id> with the ID from the first column

- 3. **Remove the container**

    - docker rm <container_id>

- 4. **Remove the image**

    - docker rmi <container image name>

    - docker rmi postgres:15.1-alpine


```plaintext

root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker ps -a

CONTAINER ID   IMAGE                  COMMAND                  CREATED          STATUS                     PORTS     NAMES
698f8e64ffbc   postgres:15.1-alpine   "docker-entrypoint.s…"   13 minutes ago   Exited (0) 4 minutes ago             adoring_pike
0b59f6f84888   ubuntu                 "bash"                   2 hours ago      Exited (127) 2 hours ago             practical_goodall
dbf5fef1b475   hello-world            "/hello"                 2 hours ago      Exited (0) 2 hours ago               cool_hermann
869a6279b7df   hello-world            "/hello"                 2 hours ago      Exited (0) 2 hours ago               keen_mcclintock


root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker stop 698f8e64ffbc
698f8e64ffbc

root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker rm 698f8e64ffbc
698f8e64ffbc

root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker ps -a

CONTAINER ID   IMAGE         COMMAND    CREATED       STATUS                     PORTS     NAMES
0b59f6f84888   ubuntu        "bash"     2 hours ago   Exited (127) 2 hours ago             practical_goodall
dbf5fef1b475   hello-world   "/hello"   2 hours ago   Exited (0) 2 hours ago               cool_hermann
869a6279b7df   hello-world   "/hello"   2 hours ago   Exited (0) 2 hours ago               keen_mcclintock

root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker images
REPOSITORY    TAG           IMAGE ID       CREATED        SIZE
ubuntu        latest        65ae7a6f3544   4 weeks ago    78.1MB
hello-world   latest        74cc54e27dc4   6 months ago   10.1kB
postgres      15.1-alpine   f8428074961e   2 years ago    243MB

root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker rmi postgres:15.1-alpine

Untagged: postgres:15.1-alpine
Untagged: postgres@sha256:f19eede5a214c0933dce30c2e734b787b4c09193e874cce3b26c5d54b8b77ec7
Deleted: sha256:f8428074961ed299e3897ae0737f21761f64e29a473de2d5ebcda117ff443760
Deleted: sha256:9423ed0f8856b1effa168eea0b2f8fd6298d281071f8c087234a90f0ca611ee9
Deleted: sha256:3480eb1dc25f4c9c2cac1644481e0311bcaf7ff32c9fe809afe92769eda48146
Deleted: sha256:84bd77368eb33a264141c185e6c20a7e7218d28d509dc2f7ee0053d32b0ad1ed
Deleted: sha256:20fbc6f93b15db7778c88b8547b2c3023a2f2838db2ee3efc7f6cb50777adf8f
Deleted: sha256:59743a27c1831d8d514cb7a465e4d3d97cbb9460258ac0c54b1a5e51eda4e265
Deleted: sha256:669e79cf9b6f33dd85e341375997dc906f330f76b4c7b63d649d7a39634ea1df
Deleted: sha256:a58feb16b8d9f65dc8fdb339208d35bd3c5fcfe8beaec0faddfa1bd8ddc252c1
Deleted: sha256:8e012198eea15b2554b07014081c85fec4967a1b9cc4b65bd9a4bce3ae1c0c88

root@admin-Standard-PC-i440FX-PIIX-1996:/home/admin# docker images

REPOSITORY    TAG       IMAGE ID       CREATED        SIZE
ubuntu        latest    65ae7a6f3544   4 weeks ago    78.1MB
hello-world   latest    74cc54e27dc4   6 months ago   10.1kB

```

- 5. **One-liner to remove everything in one go (if you don’t care about other containers/images):**

    -  docker rm -f $(docker ps -aq) && docker rmi -f $(docker images -q)
