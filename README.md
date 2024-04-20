# ITI - Docker Lab 🐋

## Task 1: Working with Docker Hello-world Image
### Objective
Learn how to run a container using the hello-world image and manage containers and images.

### Steps
#### 1. Run a Container with hello-world Image
```bash
docker pull hello-world
docker run hello-world
```
#### 2. Check Container Status and Explain
```bash
docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
----------------------------------------------------------------
docker ps -a
CONTAINER ID   IMAGE         COMMAND    CREATED         STATUS                     PORTS     NAMES
32dc12af1ecf   hello-world   "/hello"   2 minutes ago   Exited (0) 2 minutes ago             goofy_mayer
```
#### 3. Start the Stopped Container
```bash
docker start 32dc12af1ecf
```
#### 4. Remove the Container
```bash
docker rm 32dc12af1ecf
```
#### 5. Remove the Image
```bash
docker rmi d2c94e258dcb
Error response from daemon: conflict: unable to delete d2c94e258dcb (must be forced) - image is being used by stopped container 32dc12af1ecf
----------------------------------------------------------------
docker rmi -f d2c94e258dcb
Untagged: hello-world:latest
Untagged: hello-world@sha256:a26bff933ddc26d5cdf7faa98b4ae1e3ec20c4985e6f87ac0973052224d24302
Deleted: sha256:d2c94e258dcb3c5ac2798d32e1249e42ef01cba4841c2234249495f87264ac5a    
```
---

## Task 2: Running Container with Ubuntu Image
### Objective
Run an Ubuntu container in interactive mode, create a file inside it, and manage containers.

### Steps
#### 1. Run Ubuntu Container in Interactive Mode
```bash
docker run -it ubuntu
```
#### 2. Create a File inside the Container
```bash
echo "My name is Ahmed" > ahmed.txt
```
#### 3. Stop and Remove the Container
```bash
exit
docker stop 8a29e7328f24
docker rm 8a29e7328f24
```
#### 4. Check File Status
```bash
I won't be able to access the file.
```
#### 5. What happened to hello-docker file?
```bash
the container was removed in the previous step
```
#### 6. Remove All Stopped Containers
```bash
docker container prune
WARNING! This will remove all stopped containers.
Are you sure you want to continue? [y/N] y
Deleted Containers:
8a29e7328f24724e74d46c3797555e501539270403caffb4e25fbacd612dd562
32dc12af1ecf0872ba7d729167c9ccb2e47bcccc311dbe2429a308dff98deb1b

Total reclaimed space: 93B
```
#### 7. Bonus: Remove All Containers in One Command
```bash
docker container prune -f
```

---
## Task 3: Creating a Custom Nginx Docker Image
### Objective
Create a custom Docker image using Nginx and a local HTML file.

### Steps
#### 1. Create a Local HTML File
```bash
touch  index.html
```
#### 2. Write Dockerfile and Copy the HTML file to the Docker Image
```bash
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
```
#### 3. Run Container with New Image
```bash
docker build -t nginx-coustom.
```

#### 4. Test the Container, open your browser and navigate to http://localhost:8088 to check if everything is okay
```bash
docker run -d -p 8088:80 nginx-coustom
```

