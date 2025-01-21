## Running the Dockerfile

### 1. Create Dockerfile

### 2, Build Image from Dockerfile
- Open the folder where the Dockerfile is.
- Run on terminal: docker build -t node_app .

### 3. Verify if the image was created
- Run on terminal: docker images

### 4. Run a container from the created image
- Run on terminal: docker run -p 3000:80 node_app

### 5. Verify if your container is running
- Run on terminal: docker ps

### 6. Kill your container
- Run on terminal: docker stop <container_name>

## Attached and Detached Mode
- Attached mode 
    - Means that we are listening to the container output.
    - By default, `docker run` uses attached mode. 
    - We can attach to a running container, running `docker attach <container_name>`.

- Detached Mode
    - Means that we are not listening to the container output.
    - By default, `docker start` uses detached mode.
    - We can see the container outputs with `docker logs <container_name>`.