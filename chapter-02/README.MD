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


