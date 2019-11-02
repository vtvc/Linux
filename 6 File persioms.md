
# File permissions
---


```
-rwxrw-r-- 1 maha maha   0 Nov  2 05:09 f3


rwx           rw-             r--
U              G              O

7             6               4

R: read = 4
W: write = 2
X: executable = 1

Total = 7

rw           rwx             rw-
6            7                6

chmod 676 <filename>



```

* Owner or User level (u)
* Group level(g)
* Others level(o)

## Access modes are of three types:-
*  r  read only
*  w write/edit/delete/append
* x execute/run a command

* Read=4
* Write=2
* Execute=1     
* total =7

```
-rwx-rw-r-- 1 maha maha   0 Nov  2 05:09 f3
$chmod 676 f3
-rw-rwxrw- 1 maha maha   0 Nov  2 05:09 f3
$ chmod 774 f3
-rwxrwxr-- 1 maha maha   0 Nov  2 05:09 f3
```


## Absolute method:
```
#chmod 764 <filename>
#chmod 777 <filename>
#chmod 600 <filename>

```

## Symbolic method:
```

#chmod u=rwx,g=rw,o=r <filename>
# chmod ugo=rwx <filename>

ex:
$ chmod ugo=rwx f3
$ chmod u=rw,g=rwx,o=r f3
$ chmod  u=r f3

```

