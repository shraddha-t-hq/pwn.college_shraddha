# The Root 
The challenge demanded to invoke the /pwn program using its absolute pat

## My solve
**Flag:** `pwn.college{0qFpKvnrkqWnsO7XEiMkIGUst0j.QX4cTO0wSO5kjNzEzW}`
<br/>
After logging in, I ran the /pwn command directly.
TERMINAL WORKING : 
```
hacker@paths~the-root:~$ /pwn
BOOM!!!
Here is your flag:
pwn.college{0qFpKvnrkqWnsO7XEiMkIGUst0j.QX4cTO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Programs can be invoked by typing their absolute path.
2. An absolute path starts with / and refers to locations from the root of the filesystem.
3. / is the root directory containing all files and subdirectories. 

## References 
The materials provided by my mentor.
<br/>

# Program and absolute paths 
The challenge demanded to invoke the /challenge/run program using its absolute path.

## My solve
**Flag:** `pwn.college{0jc8hQXf0gQmIzLLbk3hiPGe-Sv.QX1QTN0wSO5kjNzEzW}`
<br/>
I used the absolute path `/challenge/run` directly.
TERMINAL WORKING : 
```
hacker@paths~program-and-absolute-paths:~$ cd /challenge
hacker@paths~program-and-absolute-paths:/challenge$ cd ..
hacker@paths~program-and-absolute-paths:/$ /challenge/run
Correct!!!
/challenge/run is an absolute path! Here is your flag:
pwn.college{0jc8hQXf0gQmIzLLbk3hiPGe-Sv.QX1QTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Absolute paths can refer to programs located in subdirectories, such as /challenge/run
2.No matter where you are in the filesystem, an absolute path works.
3. / is the root directory containing all files and subdirectories. 

## References 
The materials provided by my mentor.
<br/>


# Position thy self 
The challenge demanded to change into a specific directory using cd and then run /challenge/run.

## My solve
**Flag:** `pwn.college{UnBQ_XcnNdnWHDFAv5oNzuIphv0.QX2QTN0wSO5kjNzEzW}`
<br/>
After entering the command `/challenge/run` the shell gave me the directory that I was required to go to. I first navigated into the required directory with `cd`, then invoked `/challenge/run`.
TERMINAL WORKING : 
```
hacker@paths~position-thy-self:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-thy-self:~$ cd /var
hacker@paths~position-thy-self:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{UnBQ_XcnNdnWHDFAv5oNzuIphv0.QX2QTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The `cd` command changes the current working directory.
2. Running programs may sometimes require being in a particular directory.


## References 
The materials provided by my mentor.
<br/>

# Position elsewhere
The challenge demanded to cd into a different directory and then invoke the /challenge/run program.

## My solve
**Flag:** `pwn.college{4VdnJiJPMvq32QBu-DoXARa8ihA.QX4QTN0wSO5kjNzEzW}`
<br/>
After entering the command `/challenge/run` the shell gave me the directory that I was required to go to. I first navigated into the required directory with `cd`, then invoked `/challenge/run`.
TERMINAL WORKING : 
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var
hacker@paths~position-yet-elsewhere:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4VdnJiJPMvq32QBu-DoXARa8ihA.QX4QTN0wSO5kjNzEzW}


```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1.Multiple directory changes may be required before executing a file.
2.cd is always relative to your current position unless you use an absolute path.


## References 
The materials provided by my mentor.
<br/>


# Position yet elsewhere
The challenge demanded to cd yet again to another specified directory and run the /challenge/run program.

## My solve
**Flag:** `pwn.college{4VdnJiJPMvq32QBu-DoXARa8ihA.QX4QTN0wSO5kjNzEzW}`
<br/>
After entering the command `/challenge/run` the shell gave me the directory that I was required to go to. I first navigated into the required directory with `cd`, then invoked `/challenge/run`.
TERMINAL WORKING : 
```
hacker@paths~position-yet-elsewhere:~$ /challenge/run
Incorrect...
You are not currently in the /var directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~position-yet-elsewhere:~$ cd /var
hacker@paths~position-yet-elsewhere:/var$ /challenge/run
Correct!!!
/challenge/run is an absolute path, invoked from the right directory!
Here is your flag:
pwn.college{4VdnJiJPMvq32QBu-DoXARa8ihA.QX4QTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1.Multiple directory changes may be required before executing a file.
2.cd is always relative to your current position unless you use an absolute path.


## References 
The materials provided by my mentor.
<br/>


# Implicit relative paths, from /
The challenge demanded running /challenge/run using a relative path from /.

## My solve
**Flag:** `pwn.college{4VdnJiJPMvq32QBu-DoXARa8ihA.QX4QTN0wSO5kjNzEzW}`
<br/>
I initially struggled with what this question asked of me. Ater multiple failed attempts of getting into /challenge/run, I figured out that we I was required to go into the root directory `/` first in order to use the relative path, after which I used the relative path to complete the challenge.
TERMINAL WORKING : 
```
hacker@paths~implicit-relative-paths-from-:~$ /challenge/run
Incorrect...
You are not currently in the / directory.
Please use the `cd` utility to change directory appropriately.
hacker@paths~implicit-relative-paths-from-:~$ challenge/run
bash: challenge/run: No such file or directory
hacker@paths~implicit-relative-paths-from-:~$ cd challenge/run
bash: cd: challenge/run: No such file or directory
hacker@paths~implicit-relative-paths-from-:~$ cd /
hacker@paths~implicit-relative-paths-from-:/$ cd challenge/run
bash: cd: challenge/run: Not a directory
hacker@paths~implicit-relative-paths-from-:/$ hacker@paths~implicit-relative-paths-from-:/hacker@paths~implicit-relative-paths-from-:/$hacker@paths~implicit-relative-paths-from-:/$hacker@paths~implicit-relative-paths-from-:/$hacker@paths~implichackhacker@phacker@phahacker@paths~implicit-relative-paths-from-:/$ challenge/run
Correct!!!
challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{Ed-zFzoS73jRbFWn__rCNqEesVW.QX5QTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Relative paths depend on the current working directory.
2. If we are in /, the relative path omits the leading /.

## References 
The materials provided by my mentor.
<br/>

# Explicit relative paths, from /
The challenge demanded to use . in the relative path to run the challenge.

## My solve
**Flag:** `pwn.college{kWmOWx0r72n-zjgGNKEFGPkGfcP.QXwUTN0wSO5kjNzEzW}`
<br/>
I used `.` to invoke /challenge/run
TERMINAL WORKING : 
```
hacker@paths~explicit-relative-paths-from-:/$ ./challenge/run
Correct!!!
./challenge/run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{kWmOWx0r72n-zjgGNKEFGPkGfcP.QXwUTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `.` refers to the current directory.
2. Commands like ./challene/run ensure execution from the current folder.


## References 
The materials provided by my mentor.
<br/>

# Implicit relative path
The challenge demanded to run `run` from inside the /challenge directory.

## My solve
**Flag:** `pwn.college{M6elF_JhCszzgWIJ74-S9KwRR-8.QXxUTN0wSO5kjNzEzW}`
<br/>
I first entered the directory `/challenge` after which I used the relative path using `.` to execute /run.
TERMINAL WORKING : 
```
hacker@paths~implicit-relative-path:~$ cd /challenge
hacker@paths~implicit-relative-path:/challenge$ ./run
Correct!!!
./run is a relative path, invoked from the right directory!
Here is your flag:
pwn.college{M6elF_JhCszzgWIJ74-S9KwRR-8.QXxUTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Linux does not run files in the current directory unless explicitly specified with ./.

## References 
The materials provided by my mentor.
<br/>

# Home sweet home 
The challenge demanded to give /challenge/run a writable file inside the home directory as an argument (3 characters or less).

## My solve
**Flag:** `pwn.college{EZsnJsayVVsLps4urmWy0hi3E_9.QXzMDO0wSO5kjNzEzW}`
<br/>
Initially, i did not understand which argument I should have used which would have been 3 words or else. I took to the internet to find such an argument. I found  `~/f` and used it as an argument.
TERMINAL WORKING : 
```
hacker@paths~home-sweet-home:/$ /challenge/run /usr
The argument you provided must not have been longer than 3 characters (it's
currently 4 characters long)!
hacker@paths~home-sweet-home:/$ /challenge/run ~/f
Writing the file to /home/hacker/f!
... and reading it back to you:
pwn.college{EZsnJsayVVsLps4urmWy0hi3E_9.QXzMDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. ~ expands to the absolute path of the home directory.
2. Arguments can be paths, and constraints may apply (like length).

## References 
The materials provided by my mentor.
<br/>
