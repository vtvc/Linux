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

```
   vi /etc/passwd
    tcpdump:x:72:72::/:/sbin/nologin
    ec2-user:x:1000:1000:EC2 Default User:/home/ec2-user:/bin/bash
    Maha:x:1001:1001:myuser:/home/maha:/bin/bash

The above fields are

maha =name
x= link to password file i.e. /etc/shadow
1001= UID (user id)
100 1=GID (group id)
myuser= comment (brief information about the user)
/home/maha = home directory of the user
/bin/bash = shell

```

  


```
 vi /etc/shadow
 maha:$6$iPmA:18166:0:99999:7:::
 The fields are as follows,
1. maha = User name
2. $6$iPmA = Encrypted password 
3. 18166 = Days since that password was last changed. 
4. 0 = Days after which password must be changed.
5. 99999 = Days before password is to expire that user is warned. 
6. 7 = Days after the password is expires that the user is disabled.
7. A reserved field.

```

## Creating a user
```
 # useradd <option> <username>

options are
-u user id
-G Secondary group id
-g primary group id
-d home directory
-c comment
-s shell

# adduser -d /home/sai -c mysaiuser -s /bin/bash -u 505 sai

# passwd 

```
## Modifying the user’s attribute

```
# usermod <options> <username>
-l  to change login name
-L  to LOCK account
-U  to UNLOCK account

# usermod -L maha 
# usermod -U maha

```

> Note: - when an account is locked it will show ! (Exclamation mark) in /etc/shadow file

## Password parameters


 * For any user we can set the parameters for the password, like min and max password age, password expiration warnings and a/c expiration date etc

 ```
#chage -l < username>
#chage -l maha

 ```
* Last password change: When the password was change last time.
* Password expires: Password expiry date
* Password inactive: After password expiry grace period before the account gets locked.
* Account expires: Date on which the account expires.
* Minimum number of days b/w password change: once the password is changed, it cannot be changed until a min period of specified date. [0] means never.
* Max number of days b/w password change: After changing the password how long it will be valid for.
* Number of days of warning before password expires: start of warnings to change the password, no. of days before the password expires.


## Changing the password parameters
* Changing of the password parameters can be done by two ways.
```
#chage <user name >
#chage <option> <value> <username>

```

* -m for Min password age
* -M for Max password age
* -d for last time the password is changed.
* -W Password expiration warnings
* -I Password inactive [-1 means inactive].
* -E A/C expiration date


## Deleting a User:

* To delete a user the syntax used is:
```
#userdel <username>    : without home dir
#userdel –r < user name >  : with home dir 

```
