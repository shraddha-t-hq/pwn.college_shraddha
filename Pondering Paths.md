# The Root 
The challenge demanded to invoke the /pwn program using its absolute pat

## My solve
**Flag:** `pwn.college{0qFpKvnrkqWnsO7XEiMkIGUst0j.QX4cTO0wSO5kjNzEzW}`
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





