# GROUP ADMINISTRATION

---

* Users are assigned to groups with unique group ID numbers (the GID)
* The group name and GID are stored in /etc/group
* Each user is given their own private group
* They can also be added to their groups to gain additional access
* All users in a group can share files that belong to the group

## Important files for groups
*  **_/etc/group_**  : in this file  maintain group’s informations, like group name,GID
*  **_/etc/gshadow_** : in this file maintain  group’s password related informations  

* A user’s primary group is defined in the /etc/passwd file 
* A user’s Secondary groups are defined in the /etc/group file.
* The primary group is important because files created by this user will inherit that group affiliation(other groups).
* Each user is a member of at least one group, called a primary group.
* In addition, a user can be a member of an unlimited number of secondary groups. 
* Group membership can be used to control the files that a user can read and edit. 

> For example,
If two users are working on the same project you might put them in the same group so they can edit a particular file that other users cannot access


## Creating a Group with default options

* To create a group the syntax is

```
#groupadd <name for the group>
#groupadd mahagrp

```
## Creating a group with user specified group id (GID)

```
#groupadd <option> <name for the group>
#groupadd -g 595 mahagroup

```

## Adding single or multiple users in to the group with various attributes

```
#gpasswd < option> <arguments> <group name>
Options:
-M For Adding Multiple users to a group
-A for Adding a group Administrator
-a for Adding a single user to a group
-d removing a user from a group


Ex: #gpasswd –M <user>,<user>,<user> <group>
Ex: #gpasswd –M sai,raj  mahagrp


```



## Modifying the properties of the group

```
#groupmod <option> <arguments> <group name>
The options are
-g to change the group id
-o to override the previous assigned id, if it matches with the new one.
-n to change the group name
Ex: #groupmod –g 600 mahagroup
#groupmod –n <new name > < existing name >
Ex: #groupmod -n mahanewgrp mahagroup

```


## Adding and Removing Members to a Group

```
To add single user to the group
#usermod –G <group name > < user name>
#usermod –G mahagrp  sai


```


