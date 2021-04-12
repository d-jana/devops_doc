## Deploying Spring Boot Microservices on Docker

create **Dockerfile** in project root

![](https://github.com/dipakongit/devops_doc/blob/main/docker/images/1.png)

write script in **Dockerfile**

![](https://github.com/dipakongit/devops_doc/blob/main/docker/images/2.png)

Build image from Dockerfile
```
docker build -t dockeradmin .
```

### We using docker-compose and why?

Docker Compose is used to run multiple containers as a single service. For example, suppose you have two microservice **mic1,mic2** and **mongodb**,
you could create one file which would start both the containers as a service without the need to start each one separately.

Install Compose on Linux systems
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
Apply executable permissions to the binary:
```
sudo chmod +x /usr/local/bin/docker-compose
```

#### Docker compose for microservice

I have 3 microservice eureka,product-service,zuul.

Create Dockerfile to each microservice.

![](https://github.com/dipakongit/devops_doc/blob/main/docker/images/3.png)

Then create docker-compose.yml file. Click on this link [docker-compose.yml](https://github.com/dipakongit/devops_doc/blob/main/docker/docker-compose.yml) to see docker-compose file content

docker-compose run all container as a one singale service.

This is an microservice project and this have a docker-compose.yml file

![](https://github.com/dipakongit/devops_doc/blob/main/docker/images/4.png)


#### Keep in Mind :
In docker container name is the **host name**.
So, when run microservice project in docker you must see the link which use in microservice **application.properties**
file like **eureka server url,config server url** . At devlopment time this url structure is like this
```
	eureka.client.serviceUrl.defaultZone  = http://localhost:8761/eureka
```
but when you deploye it on docker you must change this url like this
```
	eureka.client.serviceUrl.defaultZone  = http://eureka:8761/eureka
```
the eureka is the name of docker container where eureka is running.



