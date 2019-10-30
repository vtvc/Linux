# User management:

* One or more than one users in Linux at a time.
* Users on a system are identified by a username and a userid. 
* The username is something that users would normally refer to, but as far as the operating system is concerned this is referred to using the user id (or uid)
* He user id numbers should be unique (one number per user)
* If you had two usernames with the same user id, effectively there permissions would be the same and the files that they create would appear to have been created by the same user.
* This should not be allowed and the useradd command will not allow usernames to share the same userid.
 
 ```
    1  adduser maha
    2  cd /home/
    3  ls
    4  tail /etc/passwd
    5  cd
    6  adduser maha

 ```

* Users and groups are used to control access to files and resources
* Users login to the system by supplying their username and password
* Every file on the system is owned by a user and associated with a group
* Every process has an owner and group affiliation, and can only access the resources its owner or group can access.
* Every user of the system is assigned a unique user ID number ( the UID)
* Users name and UID are stored in /etc/passwd
* User’s password is stored in /etc/shadow in encrypted form.
* Users are assigned a home directory and a program that is run when they login (Usually a shell)
* Users cannot read, write or execute each other’s files without permission

```
    #   less /etc/passwd
    #   less /etc/shadow

 as root user:

    apt-get install apache2
    apt-get update
    adduser maha
    visudo
     * udder root privileged 
    maha ALL=(ALL) NOPASSWD: ALL
    :wq!
    su maha

As normal user:

    apt-get install apache2
    sudo apt-get install apache2
    service  apache2 status


```


## Types of users:


| Type | Example | UserID | GroupID | HomeDir |Shell |
| :---: | :---: | :---: | :---: | :---: | :---: |
|Super user|root|0|0|/root|/bin/bash|
|system users|jenkin,mail|0-499|0-499|/var/ftp| /sbin/nologin|
|Normal users| maha,Raj| 500-60000|500- 60000|/home/username| /bin/bash|


___
# 30-oct-19:


### Super user or root user 
 * Super user or the root user is the most powerful user. He can do anything as  admin user. 

### System user 
* System users are the users created by the softwares or applications. For example if we install Apache it will create a user apache. These kinds of users are known as system users. 

### Normal user
 * Normal users are the users created by **root** user. They are normal users like maha, raj etc. Only the root user has the permission to create or remove a user. **_We can make normal user as sudo user by root_**.


## Whenever a user is created in Linux, what are things created by default:-
* A home directory is created(/home/username)
* A mail box is created(/var/spool/mail)
* unique UID,
* unique GID are given to user

## Linux uses UPG (User Private Group) scheme
* It means that whenever a user is created is has its own private group
> For Example if a user is created with the name maha, then a primary group for that user will be **maha** only

## Important files for user
 * /etc/passwd  : in this file  maintain **username** information 
 * /etc/shadow :  in this file maintain  **password** information

