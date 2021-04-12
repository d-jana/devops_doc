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

Docker Compose is used to run multiple containers as a single service. For example, suppose you have two microservice **mic1,mic2** and one **mongodb** database,
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

I have 3 microservice eureka,product-service,zuul and one mongo database.

Create Dockerfile to each microservice.

![](https://github.com/dipakongit/devops_doc/blob/main/docker/images/3.png)


