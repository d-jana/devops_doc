#### Linux root directory
```
/
```

## Linux file handling command

list directory
```
 ls
```
list of directory with detail
```
 ll
```
list of directory with hidden files
```
 ll -a
```
change directory
```
 cd dirname
```
go to root directory. first go to root login and then
```
 cd /
```
go to user directory from any open directory
```
 cd
```
make directory
```
 mkdir dirname
```
remove empty directory
```
 rmdir dirname
```
remove non empty directory
```
 rm -rf dir-name
```
move file or directory
```
 mv source-path destination-path
```
copy file or directory
```
 cp -avr source-path destination-path
```
extract tar file
```
 tar -xvf *.tar
```
Kill running port
```
 fuser -k 8080/tcp
```

## Working on FTP

install ftp client in linux
```
 yum install lftp
```
connect ftp server
```
 ftp xxx.xxx.xxx.xxx
```
show files and folder of ftp server
```
 ls
```
print current working directory iside ftp
```
 lpwd
```
change local directory from ftp
```
 lcd path-of-directory  //Ex: lcd /home/docker
```
download file from ftp to local directory
```
 pget file-name //Ex: pget mysql.ta
```
takes file from local directory and upload to ftp server
```
 put file-name //Ex: put mysql.tar
```

## Working on USB

show block list device with details. They show UUID, LABEL, NAME
```
 blkid
```
mount usb device which show on blkid command
```
  mount -L HP /media (..using label name)
  mount -U BXXX-XXXX (..using UUID)
  mount -t auto /dev/sda /media (..using name)
```
enter in usb device
```
  cd /media
```

## Scrolling inside terminal

see more lines in terminal
```
 your_command | less
```
scroll up
```
 shift - page up OR Up Arrow
```
scroll down
```
 shift - page down OR Down Arrow
```
exit from scroller
```
q
```

## Working with text editor in linux terminal

open a file command
```
 vi filename
```
insert in file vid editror
```
 press i
```
close insert option
```
 press Esc
```
exit from editor
```
 press :x then Enter
```
exit with save
```
 press :wq then enter
```
force exit
```
 press :q! then enter
```
Position the cursor at the beginning of the text you want to cut/copy.
```
 Press v to begin character-based visual selection, or V to select whole lines
```
Move the cursor to the end of the text to be cut/copied
```
 Press d (delete) to cut, or y (yank) to copy.
```
Move the cursor to the desired paste location.
```
 Press p to paste after the cursor, or P to paste before.
```

## Create linux service

create unit file name.service in /lib/systemd/system location
```
[Unit]
Description=Example systemd service.

**this is description of service which show on [systemctl status]

[Service]
ExecStart=/bin/bash /usr/bin/test_service.sh 
 
**The critical part is the ExecStart directive, which specifies the command that will be run to start the service.

[Install]
WantedBy=multi-user.target

**WantedBy= directive is the most common way to specify how a unit should be enabled
**multi-user.target means that the systemd-service will start when the system reach runlevel 2.In linux have 7 runlevel. 
**A runlevel is one of the modes that a Unix-based operating system will run in. 
Each runlevel has a certain number of services stopped or started, giving the user control over the behavior of the machine
```
start and enable service
```
systemctl status service_name  **check status of service is running or not
          start                **start a service
          restart              **restart a service
          stop                 **stop a service
          enable               **start service on boot
```
show list of service
```
systemctl list-unit-files **use --state=enabled show list of enabled service
```


## Linux user management

to see details of file/dir like permissions, group, owner type bellow command
```
ls -l

-rw-r--r-- 12 linuxize users 12.0K Apr  8 20:51 filename.txt
|[-][-][-]    [------] [---]
| |  |  |        |       |
| |  |  |        |       +-----------> 7. Group
| |  |  |        +-------------------> 6. Owner
| |  |  |
| |  |  +----------------------------> 4. Others Permissions. Three tiplle indecats read, write and execute.
| |  +-------------------------------> 3. Group Permissions. Three tiplle indecats read, write and execute.
| +----------------------------------> 2. Owner Permissions. Three tiplle indecats read, write and execute.
|
+------------------------------------> 1. File Type. Regular file (-), directory (d),
```

* **rw-** - read, write, not executeble
* **-wx** - not readble, write and execute
* **r-x** - read, not writble, execute
* **rwx** - read, write and execute

show list of group
```
getent group

|---------------structure---------------------|
|  adm:x:4:ec2-user                           |
|  group name:password:GID:list of users      |
|---------------------------------------------|
```

show list of user
```
getent passwd

|------------------------structure-------------------------------|
| ec2-user:x:1000:1000:Cloud User:/home/ec2-user:/bin/bash       |
| username:password:UID:GID:comment:home directory:default shell |
|----------------------------------------------------------------|
```
change owner of file
```
 chown OWNER(a user name or numeric user id):GROUP(a group name or numeric group id) filename
```
change owner of file
```
 chown user sample.txt
```
change group of file
```
 chown :mygroup sample.txt
```
change both the owner and group of file
```
 chown user:mygroup sample.txt
```
change access permissions or mode of file
```
chmod mode filename
```
```
 chmod 400 filename
       |||__________ [third digit]  - for others
       ||___________ [second digit] - for group
       |____________ [first digit]  - for user
```

* **0** = No Permission      
* **1** = Execute            
* **2** = Write              
* **4** = Read               
* **7** = Read & Write & Execute
* **3** = Write & Execute
* **5** = Read & Execute
* **6** = Read & Write

Read by owner only
```
 chmod 400 sample.txt 
```    
Read by group only
```
 chmod 040 sample.txt 
```
Read by anyone
```
 chmod 004 sample.txt
```
Write by owner only
```
 chmod 200 sample.txt 
```
Write by group only
```
 chmod 020 sample.txt
```
Write by anyone
```
 chmod 002 sample.txt 
```
Execute by owner only
```
 chmod 100 sample.txt 
```
Execute by group only
```
 chmod 010 sample.txt 
```
Execute by anyone
```
 chmod 001 sample.txt 
```
Allow read permission to owner and group and anyone.
```
 chmod 444 sample.txt
```
Allow everyone to read, write, and execute file.
```
 chmod 777 sample.txt
```


## SSH Connection

connect remote mechine
```
 ssh username@hostname or ip
```
create ssh key for secure connection. create key in local mechine and copy it on remote mechine
  * Generate Key on local machine
   ```
    ssh-keygen -t rsa -b 4096

    [-t type of encription, -b bits]
   ```
  * copy key to remote mechine
   ```
    ssh-copy-id username@hostname or ip
   ```

Create ssh connection using identity file (like aws ec2)
  * Generate ssh key on remote machine
  ```
   ssh-keygen -t rsa -b 4096 -C "kvm"
   
   [-t type of encription, -b bits, -C comment]
  ```
