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

### Swarms

```sh
# Create a VM (Mac, Win7, Linux)
docker-machine create --driver virtualbox myvm1

# Win10
docker-machine create -d hyperv --hyperv-virtual-switch "myswitch" myvm1

# View basic information about your node
docker-machine env myvm1

# List the nodes in your swarm
docker-machine ssh myvm1 "docker node ls"

# Inspect a node
docker-machine ssh myvm1 "docker node inspect <node ID>"

# View join token
docker-machine ssh myvm1 "docker swarm join-token -q worker"

# Open an SSH session with the VM; type "exit" to end
docker-machine ssh myvm1

# Make the worker leave the swarm
docker-machine ssh myvm2 "docker swarm leave"

# Make master leave, kill swarm
docker-machine ssh myvm1 "docker swarm leave -f"

# Start a VM that is currently not running
docker-machine start myvm1

# Stop all running VMs
docker-machine stop $(docker-machine ls -q)

# Delete all VMs and their disk images
docker-machine rm $(docker-machine ls -q)

# Copy file to node's home dir
docker-machine scp docker-compose.yml myvm1:~

# Deploy an app
docker-machine ssh myvm1 "docker stack deploy -c <file> <app>"
```