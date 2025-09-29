# Redirecting output
The challenge demanded the redirection of stdout to a file so that the exact text PWN is written to a file named COLLEGE.

## My solve
**Flag:** `pwn.college{odvgiZlJBEDD31c8fhb8HgGOmuV.QX0YTN0wSO5kjNzEzW}`

Using the command `echo` and the symbol `>` I redirected the text output `PWN` to the file `COLLEGE`
<br/>
TERMINAL WORKING : 
```
hacker@piping~redirecting-output:~$ echo PWN > COLLEGE
Correct! You successfully redirected 'PWN' to the file 'COLLEGE'! Here is your
flag:
pwn.college{odvgiZlJBEDD31c8fhb8HgGOmuV.QX0YTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Using `>` redirects a command's standard output into a file.
2. The redirection operator `>` overwrites the target file if it already exists.  

## References 
The materials provided by my mentor.
<br/>

# Redirecting more output
The challenge required redirecting the standard output (stdout) of `/challenge/run` into a file named `myflag`.

## My solve
**Flag:** `pwn.college{klzevlFOBEEVG03JBoLUfcOoboe.QX1YTN0wSO5kjNzEzW}`

This challenge was solved by redirecting the stdout of `/challenge/run` into the file `myflag`. 
After the run completed I used `cat myflag` to read the flag.
<br/>
TERMINAL WORKING : 
```
hacker@piping~redirecting-more-output:~$ /challenge/run > myflag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : myflag
[INFO] - the challenge will output a reward file if all the tests pass : /flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /flag file.

[TEST] You should have redirected my stdout to a file called myflag. Checking...

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~redirecting-more-output:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{klzevlFOBEEVG03JBoLUfcOoboe.QX1YTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. 
2. 

## References 
The materials provided by my mentor.
<br/>
