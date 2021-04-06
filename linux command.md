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

