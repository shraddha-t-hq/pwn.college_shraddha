# Redirecting output
The challenge demanded the redirection of stdout to a file so that the exact text PWN is written to a file named COLLEGE.

## My solve
**Flag:** `pwn.college{odvgiZlJBEDD31c8fhb8HgGOmuV.QX0YTN0wSO5kjNzEzW}`
</br>
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
</br>
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
1. `>` redirects stdout only.
2. Path to a file can also be used as an argument.

## References 
The materials provided by my mentor.
<br/>

# Appending output
The challenge required redirecting a program’s stdout in append mode (`>>`) to `/home/hacker/the-flag` so that two separate writes: one directly to the file and one to stdout, combine into a single complete flag inside the file. If truncate mode (`>`) is used, the second write would overwrite the first and half the flag would be lost.

## My solve
**Flag:** `pwn.college{Mt4Y3WeCkle0ZEx60e3eUe8DJU5.QX3ATO0wSO5kjNzEzW}`
</br>
I ran `/challenge/run` with append redirection into `/home/hacker/the-flag` so the program’s first write and its second write were both preserved in the file. I then inspected the file with cat to read the full flag.
<br/>
TERMINAL WORKING : 
```
hacker@piping~appending-output:~$ /challenge/run >> /home/hacker/the-flag
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /home/hacker/the-flag

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] Good luck!

[TEST] You should have redirected my stdout to a file called /home/hacker/the-flag. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
I will write the flag in two parts to the file /home/hacker/the-flag! I'll do
the first write directly to the file, and the second write, I'll do to stdout
(if it's pointing at the file). If you redirect the output in append mode, the
second write will append to (rather than overwrite) the first write, and you'll
get the whole flag!
hacker@piping~appending-output:~$ echo /home/hacker/the-flag
/home/hacker/the-flag
hacker@piping~appending-output:~$ cat /home/hacker/the-flag
 |
\|/ This is the first half:
 v
pwn.college{Mt4Y3WeCkle0ZEx60e3eUe8DJU5.QX3ATO0wSO5kjNzEzW}
                              ^
     that is the second half /|\
                              |

If you only see the second half above, you redirected in *truncate* mode (>)
rather than *append* mode (>>), and so the write of the second half to stdout
overwrote the initial write of the first half directly to the file. Try append
mode!

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `>>` appends to a file, preserving previous contents whereas  `>` truncates the file.

## References 
The materials provided by my mentor.
<br/>

# Redirecting errors
The challenge required redirecting the standard output (stdout) of `/challenge/run` into a file named `myflag`.

## My solve
**Flag:** `pwn.college{4WkQUi5BCwd2qgUj30qMzp4n8BU.QX3YTN0wSO5kjNzEzW}`
</br>
I ran `/challenge/run` while redirecting stdout to `myflag` and stderr to `instructions`. Because both streams were redirected, the terminal stayed silent.Then I inspected the `myflag` file.
<br/>
TERMINAL WORKING : 
```
hacker@piping~redirecting-errors:~$ /challenge/run > myflag 2> instructions
hacker@piping~redirecting-errors:~$ cat myflag

[FLAG] Here is your flag:
[FLAG] pwn.college{4WkQUi5BCwd2qgUj30qMzp4n8BU.QX3YTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. File descriptors are : FD 0 = stdin, FD 1 = stdout, FD 2 = stderr.
2. `>` is shorthand for `1>` and redirects stdout; `2>` redirects stderr.
3. Redirecting both streams simultaneously is possible by doing : command > out.txt 2> err.txt.

## References 
The materials provided by my mentor.
<br/>

# Grepping stored results
The challenge demanded to redirect the stdout of `/challenge/run` into `/tmp/data.txt`, then search (`grep`) the stored output for the flag.

## My solve
**Flag:** `pwn.college{kemQAGl0MHmdLLou8JWdxR1wCzU.QX4EDO0wSO5kjNzEzW}`
</br>
I redirected `/challenge/run`’s stdout into `/tmp/data.txt` and then used `grep` to find the flag(as learnt before, all flags start with pwn.college) inside that file.
<br/>
TERMINAL WORKING : 
```
hacker@piping~grepping-stored-results:~$ /challenge/run > /tmp/data.txt
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge will check that output is redirected to a specific file path : /tmp/data.txt
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to a file called /tmp/data.txt. Checking...

[HINT] File descriptors are inherited from the parent, unless the FD_CLOEXEC is set by the parent on the file descriptor.
[HINT] For security reasons, some programs, such as python, do this by default in certain cases. Be careful if you are
[HINT] creating and trying to pass in FDs in python.

[PASS] The file at the other end of my stdout looks okay!
[PASS] Success! You have satisfied all execution requirements.
hacker@piping~grepping-stored-results:~$  grep pwn.college /tmp/data.txt
pwn.college{kemQAGl0MHmdLLou8JWdxR1wCzU.QX4EDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Large program output can be searched after the fact with grep pattern filename.


## References 
The materials provided by my mentor.
<br/>
