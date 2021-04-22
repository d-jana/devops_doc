### Start docker in linux

start docker demon
```
systemctl start docker
```
enable docker demon
```
systemctl enable docker
```

##

### Docker image

A Docker image is a read-only template that contains a set of instructions for creating a container that can run on the Docker platform.


create docker image.
```
>> for by default filename (Dockerfile)

  docker build -t [image name] .
  
  Ex: docker build -t demoapp .
  
>> If filename is different (Dockerfile.dock)

  docker build -t [image name] -f [docker filename] .
  
  Ex: docker build -t demoapp -f Dockerfile.dock .
```
show image list
```
docker images
```
change image name or change version
  * change image name
  ```
  docker tag [old image name] [new image name]
  
  Ex: docker tag demoapp testapp
  ```
  * change version
  ```
  docker tag [image name:old tag] [image name:new tag]
  
  Ex: docker tag demoapp:1 demoapp:2
  ```
show history of an images. like last uploaded date and context and size
```
docker image history [image id or name]
```
show details about of an image
```
docker image inspect [image id or name]
```
remove docker image
```
docker image remove [image id or name]
```
Remove daggling image. A image ehich name and tag is none
```
docker image prune
```
pull a image
```
>> pull a image from docker registry

  docker pull [image name]
  
>> pull a image from others registry or your own created registry

  docker pull [registry url/image name]
  
  EX: docker pull localhost:8080/demoapp
```
push a image
```
>> push a image to docker registry

  docker push [image name]
  
>> push a image to others registry or your own created registry

  docker push [registry url/image name]
  
  EX: docker push localhost:8080/demoapp
```
##

### Docker container

A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.


run docker image as a container
```
docker run --name [assign a name of container] -d -p [host port:containerport] -e [enviorment variable name=value] 
-v [host file or dir path:container file or dir path] --net [network name]  --restart=always [name of image]:[tag]
```
  * **--name** assign name of a container
  * **-d** dituch mode. if want to run the container background
  * **-p host port:container port** Publish a container's port to the host port
  * **-e** set enviorment variable for docker container. ex: -e MYSQL_ROOT_PASSWORD=123
  * **-v** to mount container volume to the host volume. ex: -v /home/abc/file.key:/data/file.key
  * **--net** assign a network for container. if we don't use **--net** then it by default take bridge network
  * **--restart=always** docker container restart automatically when docker is restart

show running container
```
docker ps
```
show all container
```
docker ps -a
```
start, stop and restart a container
```
docker start [container id or name]
       stop
       restart
```
push and unpush a container
```
docker container pause [container id or name]
                 unpause
```
show details about of an container
```
docker container inspect [container id or name]
```
delete a container
```
docker rm -f [container id or name]
```
  * **-f** for force delete. If a container is running then it force delete

to remove all the stop container
```
docker container prune
```
show details about of a container
```
docker container inspect [container id or name]
```
copy file from local drive to docker container
```
docker cp [local file path] [container id or name]:[path in docker container where paste the file]

Ex: docker cp app.txt db280a3413f5:/home/dipak/app.txt
```
copy file from docker container to local drive
```
docker cp [container id or name]:[path in docker container where paste the file] [local file path]

Ex: docker cp db280a3413f5:/home/dipak/app.txt app.txt
```
change name of docker container
```
docker rename [container id or old name] [new name]
```
show logs of container
```
docker logs [container id or name]
```
show current logs of container
```
docker logs -f [container id or name]
```
execute an interactive bash shell on the container.
```
docker exec -it [container id or name] bash
```
  * this will create a new bash session in the container 

##

### Docker network

##### A network is created to create communication between containers. If each container have in same network then they can communicate between each other

create a network
```
docker network create [name]
```
show list of network
```
docker network ls
```
show details of a network
```
docker network inspect [network id or name]
```
delete a network
```
docker network remove [network id or name]
```
clean up unuse network's
```
docker network prune
```
connect a container with existing network
```
docker network connect [network name or id] [container name or id]
```
disconnect a container with existing network
```
docker network disconnect [network name or id] [container name or id]
```
##

### Docker volume

##### Volumes are the preferred way to persist data in Docker containers. Some use cases for volumes is Sharing data among multiple running containers

create a volume
```
docker volume create [name]
```
show list of volume
```
docker volume ls
```
show details of a volume
```
docker volume inspect [name]
```
delete a volume
```
docker volume remove [name]
```
clean up unuse volume
```
docker volume prune
```

##

### Why use dockerignore?

dockerignore is used to reduce image size and to decrese build time. [check .dockerignore file sample](https://github.com/dipakongit/devops_doc/blob/main/docker/.dockerignore)


##

### Save & Load

back up image
```
docker save -o [path for generated tar file] [image name or id]
```
load an existing image
```
docker load -i [path to image tar file]
```


##

### MySql on DOCKER

```
docker run --name mysql -d -p 3306:3306 -e MYSQL_ROOT_PASSWORD=123 mysql:latest
```
  * Here we give **MYSQL_ROOT_PASSWORD** at runtime
  
go to mysql sell
```
docker exec -it mysql bash
        or
docker exec -it mysql sh (if above is not working then try it)
```

### MongoDB on DOCKER

```
docker run -d --name mongo -p27017:27017 --restart=always mongo --auth
```
  * **--auth** use to enable mongodb authentication
  
go to mongodb sell
```
docker exec -it mongo bash
        or
docker exec -it mongo sh (if above is not working then try it)
```

### run centos docker container image

```
docker run -d --tmpfs /tmp --tmpfs /run -v /sys/fs/cgroup:/sys/fs/cgroup:ro --cap-add=NET_ADMIN --cap-add=NET_RAW --restart=always --name centos --stop-signal SIGRTMIN+3 centos
```
  * if want to run docker in docker then use **--privileged**

