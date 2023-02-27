# Docker commands cheatsheet

## Tutorial from docker
```shell
docker run --name repo alpine/git clone https://github.com/docker/getting-started.git
docker cp repo:/git/getting-started/ .
cd gettint-started
docker build -t docker101tutorial .

docker run -d -p 80:80 --name docker-tutorial docker101tutorial

docker stop docker-tutorial

docker container ls  
```

## Images
Build image
```shell
docker image build -t name/repo:ctr --no-cache .
```
List images
```shell
docker image ls 
```
Push image to registry
```shell
docker image push dockerhub_Id/repo_name:image_name

#In case of access denied
docker login 
```

Remove local image
```shell
docker image rm dockerhub_Id/repo_name:image_name
```

## Containers
Run container detach terminal
```shell
docker container run -d --name web -p 8000:8080 \
ml14/gsd:first-ctr

# -d for detach from terminal in the background, can be -it for interactive on terminal
# -p port mapping (host: listening in the container)
```

Run container attach terminal
```shell
docker container run -it --name test alpine sh

exit # exists the terminal and kills the container

ctrl+p+q --> out of terminal without killing the process
```

List containers
```shell
docker container ls

docker container ls -a # show all containers, event exited ones that can be restarted
```

Stop
```shell
docker container stop web 
```

Restart
```shell
docker container stop web 
```

Remove container
```shell
docker container rm web 
```

## Docker compose

declarative way in a config file
```shell
docker-compose up -d # calls the docker-compose.yml

docker-compose down 
```
[Docker compose example](https://github.com/nigelpoulton/gsd/blob/master/multi-container/docker-compose.yml)
## Docker swarm, docker services
multiple docker host into a secure avail cluster
```shell
docker swarm init

docker service create --name web -p 8080:8080 --replicas 3 docker_hub_id/repo:container

docker service ls

docker service ps <service_name>
```

## Docker stacks
Needs to be build before hand
```shell
docker image build -t docker_hub_id/repo:container

docker push

docker stack deploy -c docker-compose.yml counter

docker stack ls

docker stack services counter

docker stack ps counte
```

Resources: 

[Lab play with docker](https://labs.play-with-docker.com/)

[Getting Started with Docker](https://app.pluralsight.com/library/courses/getting-started-docker/table-of-contents)

[Docker docs](https://docs.docker.com/engine/reference/commandline/stop/)