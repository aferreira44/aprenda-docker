# Get Started with Docker

## Cheat Sheet

### Containers

```sh
# Create image using this directory's Dockerfile
docker build -t friendlyname .

# Run "friendlyname" mapping port 4000 to 80
docker run -p 4000:80 friendlyname

# Same thing, but in detached mode
docker run -d -p 4000:80 friendlyname

# See a list of all running containers
docker ps

# Gracefully stop the specified container
docker stop <hash>

# See a list of all containers, even the ones not running
docker ps -a

# Force shutdown of the specified container
docker kill <hash>

# Remove the specified container from this machine
docker rm <hash>

# Remove all containers from this machine
docker rm $(docker ps -a -q)

# Show all images on this machine
docker images -a

# Remove the specified image from this machine
docker rmi <imagename>

# Remove all images from this machine
docker rmi $(docker images -q)

# Log in this CLI session using your Docker credentials
docker login

# Tag <image> for upload to registry
docker tag <image> username/repository:tag

# Upload tagged image to registry
docker push username/repository:tag

# Run image from a registry
docker run username/repository:tag
```

### Services

```sh
# List all running applications on this Docker host
docker stack ls

# Run the specified Compose file
docker stack deploy -c <composefile> <appname>

# List the services associated with an app
docker stack services <appname>

# List the running containers associated with an app
docker stack ps <appname>

# Tear down an application
docker stack rm <appname>
```