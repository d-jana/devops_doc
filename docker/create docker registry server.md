## Create your own docker registry server

1. Before you can deploy a registry, you need to install Docker on the host.

2. First check domain name. If you have no purchase domain name then your host name is domain name.Use following command to get hostname
```
[root@jenkins /]# hostname
jenkins.server
```
jenkins.server is my hostname

3. pull **registry** image from docker hub
```
docker pull registry
```

### Use self-signed certificates

4. Generate your own certificate
```
mkdir certs

openssl req -newkey rsa:4096 -nodes -sha256 -keyout certs/ca.key -x509 -days 365 -out certs/ca.crt
```
must be use your host name ```jenkins.server``` as a CN (Common Name)

5. Use following command to start registry container
```
docker run -d --restart=always --name registry -v /certs:/certs -e REGISTRY_HTTP_TLS_CERTIFICATE=/certs/ca.crt -e REGISTRY_HTTP_TLS_KEY=/certs/ca.key -p5000:5000 registry
```

### Setup other Docker host from which we do pull and push operation

6. Define registry server **host name** and **ip address** to **/etc/hosts** file on every Docker host. 
```
sudo vi /etc/hosts

add line: 
172.18.0.2 jenkins.server
```

7. Copy the **ca.crt** file to **/etc/docker/certs.d/jenkins.server:5000/ca.crt** on every Docker host
```
$ mkdir -p /etc/docker/certs.d/[registry server host name]:[port]
$ cp ca.crt /etc/docker/certs.d/jenkins.server:5000/ca.crt
```

### Now pull a docker image to registry server

8. 1st change tag of docker image like this : 
```
dipak@dipak-HP:~$ docker images
quarkus/officechat                            latest              b040bf4e94bf        2 weeks ago         156MB

dipak@dipak-HP:~$ docker tag quarkus/officechat jenkins.server:5000/quarkus/officechat

dipak@dipak-HP:~$ docker images
quarkus/officechat                            latest              b040bf4e94bf        2 weeks ago         156MB
jenkins.server:5000/quarkus/officechat        latest              b040bf4e94bf        2 weeks ago         156MB
```
  * Structure is - docker tag [image name] [registry server host name]:[port]/[image name] 

9. then push image to registry server
```
dipak@dipak-HP:~$ docker push jenkins.server:5000/quarkus/officechat
```
10. If want to pull from registry server
```
dipak@dipak-HP:~$ docker pull jenkins.server:5000/quarkus/officechat
```

