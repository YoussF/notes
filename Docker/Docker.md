## Docker install
```bash
# Install Docker
curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh
# Add user to docker group
sudo usermod -aG docker $USER
```

## Docker Images
```bash
# List images ls
docker image ls
# Retag existing image
docker image tag nginx btraversy/nginx
# Build image from DockerFile
docker image build -t [REPONAME] .
# Add tag to push to Dockerhub
docker image tag nginx-website:latest btraversy/nginx-website:latest
# Upload image to dockerhub
docker image push bradtraversy/nginx
# Login to Dockerhub
docker login
# Add tag to new image
docker image tag bradtraversy/nginx bradtraversy/nginx:testing
# Pull down mysql image to test
docker pull mysql
# Inspect and see image
docker image inspect mysql
# Visualise docker image history
docker history image_name
# Search for an image on Dockerhub
docker search mysql
```

## Docker Networks
```bash
# Create network
docker network create [NETWORK_NAME]
# Create container on network
docker container run -d --name [NAME] --network [NETWORK_NAME] nginx
# Connect existing container to network
docker network connect [NETWORK_NAME] [CONTAINER_NAME]
# Disconnect existing container to network
docker network disconnect [NETWORK_NAME] [CONTAINER_NAME]
# List all Networks
docker network ls
# Inspect Network
docker network inspect [NETWORK_NAME]
# Remove unused Networks
docker network prune
# Get All Instances IP Addresses
docker ps -q | xargs -n 1 docker inspect --format '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}} {{ .Name }}' | sed 's/ \// /'
```
## Docker Volumes
```bash
# List all Volumes
docker volume ls
# Remove specific Volume
docker volume rm [VOLUME_NAME]
# Remove all unused Volume
docker volume rm $(docker volume ls -q)
```

## Docker Containers
```bash
# Stop all running containers:
docker container stop $(docker container ls -aq)
# Remove all running containers:
docker container rm $(docker container ls -aq)
# Stop and remove all containers:
docker stop $(docker container ls -aq) && docker rm $(docker container ls -aq)
# Stop and remove all containers (shorthand):
docker rm -f [container_name]
#Remove all caches images:
docker rmi $(docker images -a -q)
# Get interactive shell on specified container
docker exec -it [container_name or container_ID] bash
# Rename container
docker rename old_name new_name
```

## Docker compose
```bash
# To run docker-compose
docker-compose up
# Run in background
docker-compose up -d
# down
docker-compose down
```
