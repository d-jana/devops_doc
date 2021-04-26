## SSH configuration between GIT and Jenkins

### Create ssh public and private key

```
ssh-keygen -t rsa -b 4096 -C "jenkins" -f /home/dipak/key/id_rsa
```
* **t** – type of algorithm
* **b** – bit size
* **C** – comment
* **f** – public and private key file location. Here **id_rsa** is filename

Public key and Private key file

![](https://github.com/dipakongit/devops_doc/blob/main/jenkins/images/j1.png)


### SSH setup to GIT

1) Go to **Git url** > **Settings** > **SSH and GPG keys**

  ![](https://github.com/dipakongit/devops_doc/blob/main/jenkins/images/j2.png)
  
  * Give a **Title** name
  * copy **id_rsa.pub** key content and past it into **Key**
  
  ![](https://github.com/dipakongit/devops_doc/blob/main/jenkins/images/j3.png)

2) then click **Add SSH Key**

### SSH setup to Jenkins

