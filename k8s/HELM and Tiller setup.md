### what is HELM?

HELM is a tool for kubernetes that help you to install and manage applications

### Architecture of HELM

HELM have two component 
1) HELM CLI - Which can be install on any machine
2) Tiller - will be deployed inside kubernetes cluster

## Config HELL in jenkins and Tiller in kubernetes cluster
Helm is configure in jenkins because we write the pipeline in jenkins and that pipeline whenever going to deploy helm packages inside the kubernetes master that's the region and it will comunicate with the kubernetes cluster with the help of Tiller so that's the region Tiller is configure inside kubernetes master  

### Installing HELM on Jenkins server

##### Ennable 10250 port (firewall) on master and worker node for HELM communication
```
port: 10250
```

