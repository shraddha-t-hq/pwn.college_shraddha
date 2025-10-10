# Becoming root with su 
The challenge demanded that run the `su` command to access the directory as root and then extract the flag.

## My solve
**Flag:** `pwn.college{YV4Db82pyWdgUWHuQPknBek1lup.QX1UDN1wSO5kjNzEzW}`
<br/>
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

# Other users with su   
The challenge demanded that run the `su` command with the argument of a username to become the user `zardus` to access the directory as `zardus and then extract the flag.

## My solve
**Flag:** `pwn.college{Y7_p0Xe9a23xmrDOi3BsJ02U-AE.QX2UDN1wSO5kjNzEzW}`
<br/>
I ran the `su` command with the username `zardus` and then entered the password provided. 
<br/>
TERMINAL WORKING : 
```
hacker@users~other-users-with-su:~$ su zardus
Password:
zardus@users~other-users-with-su:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{Y7_p0Xe9a23xmrDOi3BsJ02U-AE.QX2UDN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `su` is used to access the terminal as any other user when paired with the username of that user.

## References 
The materials provided by my mentor.
<br/>

# Cracking passwords 
The challenge demanded that I crack a leaked `/etc/shadow` hash (provided as /challenge/shadow-leak) using **John the Ripper**, recover the user zardus's password, `su` to that user, and run `/challenge/run` to obtain the flag.

## My solve
**Flag:** `pwn.college{wlBpmSK1TagcxQ_3z-q9r1jLWvi.QX3UDN1wSO5kjNzEzW}`
<br/>
I ran `john /challenge/shadow-leak` to crack the leaked hash (it revealed **aardvark** as zardus' password), then used `su zardus` and supplied the cracked password, and finally executed `/challenge/run` to read the flag.
<br/>
TERMINAL WORKING : 
```
hacker@users~cracking-passwords:~$ john /challenge/shadow-leak
Created directory: /home/hacker/.john
Loaded 1 password hash (crypt, generic crypt(3) [?/64])
Press 'q' or Ctrl-C to abort, almost any other key for status
aardvark         (zardus)
1g 0:00:00:20 100% 2/3 0.04837g/s 281.7p/s 281.7c/s 281.7C/s Johnson..buzz
Use the "--show" option to display all of the cracked passwords reliably
Session completed
hacker@users~cracking-passwords:~$ su zardus
Password:
zardus@users~cracking-passwords:/home/hacker$ /challenge/run
Congratulations, you have become Zardus! Here is your flag:
pwn.college{wlBpmSK1TagcxQ_3z-q9r1jLWvi.QX3UDN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. John the Ripper can crack password hashes from leaked files. 

## References 
The materials provided by my mentor.
<br/>

# Using sudo 
The challenge demanded that I use `sudo` to read files as root, specifically to list root-owned files and retrieve the flag via a read of flag file.
## My solve
**Flag:** `pwn.college{MzT5KkVM_rWbjQ6DCqXWHVp48ww.QX4UDN1wSO5kjNzEzW}`
<br/>
I used to `sudo` command to run `ls` and `ls -al`. Then I found the file containing flag from the list and ran `cat` coupled with sudo command. 
<br/>
TERMINAL WORKING : 
```
hacker@users~using-sudo:~$ sudo ls
COLLEGE  Desktop  PWN  f  foo.1x.dvi  instructions  myflag  not-the-flag  pwn  pwn_output  temp  the-flag  tmp
hacker@users~using-sudo:~$ sudo ls -al
total 56
drwxr-xr-x 1 hacker hacker   298 Oct  7 19:59 .
drwxr-xr-x 1 root   root    4096 Sep 26 17:24 ..
-rw------- 1 hacker hacker  1206 Sep 22 10:15 .ICEauthority
-rw------- 1 hacker hacker 10975 Oct  7 19:59 .bash_history
drwxr-xr-x 1 hacker hacker   104 Sep 29 15:20 .cache
drwxr-xr-x 1 hacker hacker    32 Sep 22 10:15 .config
drwx------ 1 hacker hacker    22 Sep 22 10:15 .dbus
drwx------ 1 hacker hacker    32 Oct  7 19:53 .john
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
hacker@users~using-sudo:~$ sudo cat not-the-flag
pwn.college{MzT5KkVM_rWbjQ6DCqXWHVp48ww.QX4UDN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `sudo` is a modern command which lets an authorized user run commands as root.

## References 
The materials provided by my mentor.
<br/>
