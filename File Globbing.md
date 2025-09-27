# Mathching with *
The challenge demanded to invoke the /pwn program using its absolute pat

## My solve
**Flag:** `pwn.college{oC6AAYZgX06mfyUkJ02ycmUuDjj.QXxIDO0wSO5kjNzEzW}`

TERMINAL WORKING : 
```
hacker@globbing~matching-with-:~$ cd /cha*
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{oC6AAYZgX06mfyUkJ02ycmUuDjj.QXxIDO0wSO5kjNzEzW}

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
