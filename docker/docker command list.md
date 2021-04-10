### Start docker in linux

start docker demon
```
systemctl start docker
```
enable docker demon
```
systemctl enable docker
```
### Docker image

create docker image. Remember when create docker image must add docker ignore(.dockerignore) file
[check .dockerignore file sample](https://github.com/dipakongit/devops_doc/blob/main/docker/.dockerignore)
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

### Docker container

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


### Docker network

create a network
```
docker network create [name]
```
show list of network
```
docker network ls
```
show details about of a network
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
