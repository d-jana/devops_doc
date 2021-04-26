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

* Go to **jenkins** 
* create free style project 
* configure
* Source Code Management tab 
* Select Git 
* Give Repository Url(ssh). Ex: git@github.com:dipakongit/devops_doc.git
* Click Add dropdown 
* Click Jenkins

then you can see this popup window

![](https://github.com/dipakongit/devops_doc/blob/main/jenkins/images/j4.png)

* Select **Kind** - SSH Username and private key 
* **Username** - any name – 
* **Private key** - Select Enter directly 
* Click **Add** 
* Copy id_rsa (private key) content and past it 
* Add

## Git webhook setup for Jenkins

1) Get webhook Url from Jenkins
  * Go to jenkins
  * Manage Jenkins
  * Configure System 
  * Go to GitHub Section 
  * Click Advanced 
  * Check **Specify another hook URL for GitHub configuration** 
  * Copy webhook URL

2) Goto your github repository > Go **Setting** Tab > Click **Webhooks** > Click **Add Webhook** >
  * Past **webhook Url** in **Payload URL**
  * Set **Content type = application/json**
  * Choose **Just the push event**
  
 Then click **Add Webhook**
