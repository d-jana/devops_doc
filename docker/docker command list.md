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
