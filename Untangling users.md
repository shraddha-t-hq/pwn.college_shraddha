# Becoming root with su 
The challenge demanded that run the `su` command to access the directory as root and then extract the flag.

## My solve
**Flag:** `pwn.college{YV4Db82pyWdgUWHuQPknBek1lup.QX1UDN1wSO5kjNzEzW}`
I ran the `su` command and then entered the password provided. Then I listed all the directories present to identify the flag file.
<br/>
TERMINAL WORKING : 
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# ls -al
total 56
drwxr-xr-x 1 hacker hacker   288 Oct  7 18:53 .
drwxr-xr-x 1 root   root    4096 Sep 26 17:24 ..
-rw------- 1 hacker hacker  1206 Sep 22 10:15 .ICEauthority
-rw------- 1 hacker hacker 11009 Oct  7 18:53 .bash_history
drwxr-xr-x 1 hacker hacker   104 Sep 29 15:20 .cache
drwxr-xr-x 1 hacker hacker    32 Sep 22 10:15 .config
drwx------ 1 hacker hacker    22 Sep 22 10:15 .dbus
-rw------- 1 hacker hacker    83 Sep 30 17:39 .lesshst
drwxr-xr-x 1 hacker hacker    10 Sep 22 09:45 .local
-rw-r--r-- 1 hacker hacker     4 Sep 30 06:17 COLLEGE
drwxr-xr-x 1 hacker hacker     0 Sep 22 09:47 Desktop
-rw-r--r-- 1 hacker hacker     8 Sep 30 06:19 PWN
-rw-r--r-- 1 root   hacker    60 Sep 23 17:42 f
-rw-r--r-- 1 hacker hacker     0 Sep 26 16:35 foo.1x.dvi
-rw-r--r-- 1 hacker hacker   829 Sep 28 13:04 instructions
-rw-r--r-- 1 hacker hacker    95 Sep 28 13:04 myflag
lrwxrwxrwx 1 hacker hacker     5 Sep 30 17:48 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker    77 Sep 30 17:25 pwn
-rw-r--r-- 1 root   hacker     0 Sep 29 15:23 pwn_output
drwxr-xr-x 1 hacker hacker     6 Sep 25 05:31 temp
-rw-r--r-- 1 hacker hacker   437 Sep 28 12:59 the-flag
drwxr-xr-x 1 hacker hacker     6 Sep 25 05:35 tmp
root@users~becoming-root-with-su:/home/hacker# cat not-the-flag
pwn.college{YV4Db82pyWdgUWHuQPknBek1lup.QX1UDN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `su` is used to access the terminal as the root and not the user.
2. it gives access to files that would have been restricted for users or others accessing the system.

## References 
The materials provided by my mentor.
<br/>

# Becoming root with su 
The challenge demanded that run the `su` command to access the directory as root and then extract the flag.

## My solve
**Flag:** `pwn.college{YV4Db82pyWdgUWHuQPknBek1lup.QX1UDN1wSO5kjNzEzW}`
I ran the `su` command and then entered the password provided. Then I listed all the directories present to identify the flag file.
<br/>
TERMINAL WORKING : 
```
hacker@users~becoming-root-with-su:~$ su
Password:
root@users~becoming-root-with-su:/home/hacker# ls -al
total 56
drwxr-xr-x 1 hacker hacker   288 Oct  7 18:53 .
drwxr-xr-x 1 root   root    4096 Sep 26 17:24 ..
-rw------- 1 hacker hacker  1206 Sep 22 10:15 .ICEauthority
-rw------- 1 hacker hacker 11009 Oct  7 18:53 .bash_history
drwxr-xr-x 1 hacker hacker   104 Sep 29 15:20 .cache
drwxr-xr-x 1 hacker hacker    32 Sep 22 10:15 .config
drwx------ 1 hacker hacker    22 Sep 22 10:15 .dbus
-rw------- 1 hacker hacker    83 Sep 30 17:39 .lesshst
drwxr-xr-x 1 hacker hacker    10 Sep 22 09:45 .local
-rw-r--r-- 1 hacker hacker     4 Sep 30 06:17 COLLEGE
drwxr-xr-x 1 hacker hacker     0 Sep 22 09:47 Desktop
-rw-r--r-- 1 hacker hacker     8 Sep 30 06:19 PWN
-rw-r--r-- 1 root   hacker    60 Sep 23 17:42 f
-rw-r--r-- 1 hacker hacker     0 Sep 26 16:35 foo.1x.dvi
-rw-r--r-- 1 hacker hacker   829 Sep 28 13:04 instructions
-rw-r--r-- 1 hacker hacker    95 Sep 28 13:04 myflag
lrwxrwxrwx 1 hacker hacker     5 Sep 30 17:48 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker    77 Sep 30 17:25 pwn
-rw-r--r-- 1 root   hacker     0 Sep 29 15:23 pwn_output
drwxr-xr-x 1 hacker hacker     6 Sep 25 05:31 temp
-rw-r--r-- 1 hacker hacker   437 Sep 28 12:59 the-flag
drwxr-xr-x 1 hacker hacker     6 Sep 25 05:35 tmp
root@users~becoming-root-with-su:/home/hacker# cat not-the-flag
pwn.college{YV4Db82pyWdgUWHuQPknBek1lup.QX1UDN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `su` is used to access the terminal as the root and not the user.
2. it gives access to files that would have been restricted for users or others accessing the system.

## References 
The materials provided by my mentor.
<br/>
