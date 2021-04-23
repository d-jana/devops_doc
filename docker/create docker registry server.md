## Create your own docker registry server

1. Before you can deploy a registry, you need to install Docker on the host.

2. pull **registry** image from docker hub
```
docker pull registry
```

### Use self-signed certificates

3. Generate your own certificate
```
mkdir certs

openssl req -newkey rsa:4096 -nodes -sha256 -keyout certs/ca.key -x509 -days 365 -out certs/ca.crt
```
