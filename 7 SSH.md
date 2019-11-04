# I want to login one linux server into other Linux server 

 * create user (maha)
 * make maha user  as sudo
 * with out pem file with passwd.
 * with out passwd, key-gen on my maha user 

 ## On Master: stage1


```
 # adduser maha
 # visudo 
   under root user, you have to entry as below
   maha ALL=(ALL)  NOPASSWD: ALL
 # vi /etc/ssh/sshd_config
    PasswordAuthentication yes
  :wq!
 # service ssh restart
 
```


 ## On all NOde: stage2


```
 # adduser maha
 # visudo 
   under root user, you have to entry as below
   maha ALL=(ALL)  NOPASSWD: ALL
 # vi /etc/ssh/sshd_config
    PasswordAuthentication yes
  :wq!
 # service ssh restart
 
```

    
## On Master: stage3



```
on maha user home dir
$  ssh-keygen
$  ssh-copy-id <your private ip od node>

```
> then, wen can login my main server into any node by maha user and ssh connection