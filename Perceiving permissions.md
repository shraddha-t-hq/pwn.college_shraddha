# Changing File Ownership 
The challenge demanded that I change the ownership of file `/flag` to the hacker user and then run a command.

## My solve
**Flag:** `pwn.college{AKlnHXY0r2D2O3MaiVMb_qkA77f.QXxEjN0wSO5kjNzEzW}`
Using the knowledge of `chown` command i used the command with the user I wanted to change the owner to(here, hacker) to change the ownership of `/flag`
After doing that, the `/flag` file became `cat`-able. 
<br/>
TERMINAL WORKING : 
```
hacker@permissions~changing-file-ownership:~$ chown hacker /flag
hacker@permissions~changing-file-ownership:~$ cat /flag
pwn.college{practice}
pwn.college{AKlnHXY0r2D2O3MaiVMb_qkA77f.QXxEjN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The `chown` <username> <file> command is used to change ownership of a given file.
2. If one were to access the file without changing ownership, the flag would be generated as a sudo string-unreadable by the system.

## References 
The materials provided by my mentor.
<br/>

# Groups and Files  
The challenge demanded that I change the group ownership of `/flag` so the group that owns it can read the flag.

## My solve
**Flag:** `pwn.college{k_ADhLmjj_rpeGI_9O_r-HayYzk.QXxcjM1wSO5kjNzEzW}`
I used `chgrp` to change the group owner of `/flag` to `hacker` (the group that can read it). After changing the group, I read the file with cat.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~groups-and-files:~$ chgrp hacker /flag
hacker@permissions~groups-and-files:~$ cat /flag
pwn.college{k_ADhLmjj_rpeGI_9O_r-HayYzk.QXxcjM1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. chgrp <group> <file> changes group ownership.
2. File access can be granted by group membership, i.e. changing the group allowed group-read and thus revealed the flag.

## References 
The materials provided by my mentor.
<br/>

# Fun with Group Names
The challenge demanded that I discover my randomized primary group name with id, then use `chgrp with that group to read /flag.

## My solve
**Flag:** `pwn.college{wO5peEPH8djOQ6orAf0OZ8S9ZZW.QXycjM1wSO5kjNzEzW}`
I ran `id` to find my user’s group (gid and group name), used `chgrp` to change the group and then then cat /flag.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~fun-with-groups-names:~$ id
uid=1000(hacker) gid=1000(grp21982) groups=1000(grp21982)
hacker@permissions~fun-with-groups-names:~$ chgrp grp21982 /flag
hacker@permissions~fun-with-groups-names:~$ cat flag
cat: flag: No such file or directory
hacker@permissions~fun-with-groups-names:~$ cat /flag
pwn.college{wO5peEPH8djOQ6orAf0OZ8S9ZZW.QXycjM1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `id` shows the user’s UID/GID and group names.

## References 
The materials provided by my mentor.
<br/>

# Changing permissions
The challenge demanded that I change the permission bits of `/flag` (using `chmod`) to make it readable.

## My solve
**Flag:** `pwn.college{oK1u-8QRq_TrYFpc7UzL0C0f1tt.QXzcjM1wSO5kjNzEzW}`
I used `chmod o+r /flag` to add read permission for others (since this level allowed chmod for me). After that, I `cat`'d the file to read the flag.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~changing-permissions:~$ chmod o+r /flag
hacker@permissions~changing-permissions:~$ cat /flag
pwn.college{oK1u-8QRq_TrYFpc7UzL0C0f1tt.QXzcjM1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `chmod` changes permission bits. `o+r` adds read for `others`.
2. Permissions alone can permit access even when ownership remains root

## References 
The materials provided by my mentor.
<br/>

# Executable Files
The challenge required making `/challenge/run` executable.

## My solve
**Flag:** `pwn.college{IO6L-QXaaWXL4nxWvFt18rxOoDa.QXyEjN0wSO5kjNzEzW}`
I used `chmod u+x /challenge/run` to give execute permission to the owning user, then ran `/challenge/run`.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~executable-files:~$ chmod u+x /challenge/run
hacker@permissions~executable-files:~$ /challenge/run
Successful execution! Here is your flag:
pwn.college{IO6L-QXaaWXL4nxWvFt18rxOoDa.QXyEjN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Execute bits determine whether a file can be **run** like, chmod u+x sets `user` execute.

## References 
The materials provided by my mentor.
<br/>

# Permission Tweaking Practise
The challenge required repeatedly changing `/challenge/pwn` permissions through 8 correct rounds.After success the challenge would have allowed me to `chmod /flag`.

## My solve
**Flag:** `pwn.college{IO6L-QXaaWXL4nxWvFt18rxOoDa.QXyEjN0wSO5kjNzEzW}`
I followed whatever criteria was needed to tweak the permission for 8 rounds, then followed the instruction to change the permissions of the flag file.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~permission-tweaking-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-r-----
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod uo-r /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": -w-r-----
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxr-----
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+x /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": -wxr-----
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -wxrw----
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod g+w /ch
allenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": -wxrw----
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrw----
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod u+r /ch
allenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": rwxrw----
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrw--w-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+w /ch
allenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": rwxrw--w-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrw-rw-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+r /ch
allenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": rwxrw-rw-
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwxrw-rwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod o+x /ch
allenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": rwxrw-rwx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ------rwx
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ug-rwx
/challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permission-tweaking-practice:~$ chmod ugo+rwx /flag
hacker@permissions~permission-tweaking-practice:~$ cat flag
cat: flag: No such file or directory
hacker@permissions~permission-tweaking-practice:~$ cat /flag
pwn.college{YSdpnJVA5t3UfVhWnwoXSBjGNSr.QXwEjN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Chaining and targeted `chmod` changes (u, g, o with +, -, =) are powerful for constructing precise permission sets.

## References 
The materials provided by my mentor.
<br/>

# Executable Files
This challenge required setting `/challenge/pwn` permissions to exact target modes (using chained chmod modes with =, -, and grouped targets) through several rounds 
until the challenge allowed me to change the permissions of `/flag`.

## My solve
**Flag:** `pwn.college{IgjxHdTaHRm2dZiYq6ZyXqjxWPg.QXzETO0wSO5kjNzEzW}`
For each round I read the current vs needed permission layout and used chained chmod modes to match the exact requirement. 
After completing all rounds the challenge let me `chmod` `/flag`.After correcting some typos during attempts (e.g., /falg), the /flag was readable and I cat'd it.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~permissions-setting-practice:~$ /challenge/run
Round 1 of 8!

Current permissions of "/challenge/pwn": rw-r--r--
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,o=- /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": -w-r-----
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=x,o=-
 /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": --xr-----
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g+x,o=- /challenge/pwn
NEEDED, BUT UNMET permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

CURRENT, INCORRECT permissions of "/challenge/pwn": -w-r-x---
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

You set the permissions incorrectly! Restarting the game!
hacker@permissions~permissions-setting-practice:~$ chmod u=x,g+x
,o=- /challenge/pwn
You set the correct permissions!
Round 2 of 8!

Current permissions of "/challenge/pwn": --xr-x---
- the user doesn't have read permissions
- the user doesn't have write permissions
* the user does have execute permissions
* the group does have read permissions
- the group doesn't have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": -w-rw--w-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=w,g=rw,o=w /challenge/pwn
You set the correct permissions!
Round 3 of 8!

Current permissions of "/challenge/pwn": -w-rw--w-
- the user doesn't have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": r--rw-r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=r,o=rx /challenge/pwn
You set the correct permissions!
Round 4 of 8!

Current permissions of "/challenge/pwn": r--rw-r-x
* the user does have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wxrwx--x
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=
rwx,o=x /challenge/pwn
You set the correct permissions!
Round 5 of 8!

Current permissions of "/challenge/pwn": -wxrwx--x
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
* the group does have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": ----w--w-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=-,g=w,o=w /challenge/pwn
You set the correct permissions!
Round 6 of 8!

Current permissions of "/challenge/pwn": ----w--w-
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rwx----wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rwx,g
=-,o=wx /challenge/pwn
You set the correct permissions!
Round 7 of 8!

Current permissions of "/challenge/pwn": rwx----wx
* the user does have read permissions
* the user does have write permissions
* the user does have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
* the world does have write permissions
* the world does have execute permissions

Needed permissions of "/challenge/pwn": -wxrw-r--
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=wx,g=
rw,o=r /challenge/pwn
You set the correct permissions!
Round 8 of 8!

Current permissions of "/challenge/pwn": -wxrw-r--
- the user doesn't have read permissions
* the user does have write permissions
* the user does have execute permissions
* the group does have read permissions
* the group does have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions

Needed permissions of "/challenge/pwn": rw----rwx
* the user does have read permissions
* the user does have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
* the world does have read permissions
* the world does have write permissions
* the world does have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod u=rw,g=
-,o=rwx /challenge/pwn
You set the correct permissions!
You've solved all 8 rounds! I have changed the ownership
of the /flag file so that you can 'chmod' it. You won't be able to read
it until you make it readable with chmod!

Current permissions of "/flag": ---------
- the user doesn't have read permissions
- the user doesn't have write permissions
- the user doesn't have execute permissions
- the group doesn't have read permissions
- the group doesn't have write permissions
- the group doesn't have execute permissions
- the world doesn't have read permissions
- the world doesn't have write permissions
- the world doesn't have execute permissions
hacker@permissions~permissions-setting-practice:~$ chmod o-rx /falg
chmod: cannot access '/falg': No such file or directory
hacker@permissions~permissions-setting-practice:~$ chmod o-rx /flag
hacker@permissions~permissions-setting-practice:~$ cat flag
cat: flag: No such file or directory
hacker@permissions~permissions-setting-practice:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~permissions-setting-practice:~$ chmod o+rx /f
lag
hacker@permissions~permissions-setting-practice:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~permissions-setting-practice:~$ chmod uo+rx /
flag
hacker@permissions~permissions-setting-practice:~$ cat /flag
pwn.college{IgjxHdTaHRm2dZiYq6ZyXqjxWPg.QXzETO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Through this challenge, I tried to master `chmod` chaining using =, +, for precise permission layouts.

## References 
The materials provided by my mentor.
<br/>

# The SUID Bit
The challenge required setting the SUID bit on `/challenge/getroot` so that when run it executes with root privileges, giving me a root shell to read `/flag`.

## My solve
**Flag:** `pwn.college{c_oZEJmhg0sOcJwKaENp5WgkM72.QXzEjN0wSO5kjNzEzW}`
I attempted to set SUID on `/flag` but the challenge restricted chmod to only work on `/challenge/getroot`.
I set the SUID bit on `/challenge/getroot` using `chmod u+s /challenge/getroot`, executed `/challenge/getroot` to get a root shell, then cat /flag as root to read the flag.
<br/>
TERMINAL WORKING : 
```
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ ls -l
total 32
-rw-r--r-- 1 hacker hacker   4 Sep 30 06:17 COLLEGE
drwxr-xr-x 1 hacker hacker   0 Sep 22 09:47 Desktop
-rw-r--r-- 1 hacker hacker   8 Sep 30 06:19 PWN
-rw-r--r-- 1 root   hacker  60 Sep 23 17:42 f
-rw-r--r-- 1 hacker hacker   0 Sep 26 16:35 foo.1x.dvi
-rw-r--r-- 1 hacker hacker 829 Sep 28 13:04 instructions
-rw-r--r-- 1 hacker hacker  95 Sep 28 13:04 myflag
lrwxrwxrwx 1 hacker hacker   5 Sep 30 17:48 not-the-flag -> /flag
-rw-r--r-- 1 root   hacker  77 Sep 30 17:25 pwn
-rw-r--r-- 1 root   hacker   0 Sep 29 15:23 pwn_output
drwxr-xr-x 1 hacker hacker   6 Sep 25 05:31 temp
-rw-r--r-- 1 hacker hacker 437 Sep 28 12:59 the-flag
drwxr-xr-x 1 hacker hacker   6 Sep 25 05:35 tmp
hacker@permissions~the-suid-bit:~$ cat /flag
cat: /flag: Permission denied
hacker@permissions~the-suid-bit:~$ chmod u+s /challenge/getroot
hacker@permissions~the-suid-bit:~$ /challenge/getroot
SUCCESS! You have set the suid bit on this program, and it is running as root!
Here is your shell...
root@permissions~the-suid-bit:~# cat /flag
pwn.college{c_oZEJmhg0sOcJwKaENp5WgkM72.QXzEjN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The SUID bit (`s`) allows an executable to run with the file owner’s (here root’s) privileges — a powerful and potentially dangerous capability.
## References 
The materials provided by my mentor.
<br/>
