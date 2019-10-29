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
``



```

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