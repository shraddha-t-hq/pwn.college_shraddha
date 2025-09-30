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

# Redirecting input
The challenge demanded redirecting a file named `PWN` into the stdin of `/challenge/run` so that the program reads the exact text `COLLEGE` from that file.

## My solve
**Flag:** `pwn.college{QMnjLvZy5WWBfdaWSdZksI9cW0j.QXwcTN0wSO5kjNzEzW}`
</br>
I created the file `PWN` containing the exact text `COLLEGE` using `echo` with output redirection, then redirected that file into `/challenge/run` using `<` so the program read COLLEGE from its standard input.
<br/>
TERMINAL WORKING : 
```
hacker@piping~redirecting-input:~$ echo COLLEGE > PWN
hacker@piping~redirecting-input:~$ /challenge/run < PWN
Reading from standard input...
Correct! You have redirected the PWN file into my standard input, and I read
the value 'COLLEGE' out of it!
Here is your flag:
pwn.college{QMnjLvZy5WWBfdaWSdZksI9cW0j.QXwcTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Using `< filename` redirects a file's contents into a command's standard input, allowing programs that read stdin to receive input from files.

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

# Grepping live outputs
The challenge required piping the stdout of `/challenge/run` into another program so that the flag could be found in the live stream of output.

## My solve
**Flag:** `pwn.college{Eh2rMEvdU-h2MEarkeO2m5q3fLa.QX5EDO0wSO5kjNzEzW}`
</br>
I ran `/challenge/run` and piped its stdout into `grep pwn.college` using `|`.
<br/>
TERMINAL WORKING : 
```
hacker@piping~grepping-live-output:~$ /challenge/run | grep pwn.college
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stdout : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stdout to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stdout!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{Eh2rMEvdU-h2MEarkeO2m5q3fLa.QX5EDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The pipe operator `|` connects stdout (fd 1) of the left-hand command to stdin (fd 0) of the right-hand command.
2. Piping allows you to search live output without storing it first which is very useful for very large or streaming output.

## References 
The materials provided by my mentor.
<br/>

# Grepping errors
The challenge demanded that I make the program’s standard error visible to another process so I could grep through the error output and find the flag. Since | only pipes stdout, I had to redirect stderr (fd 2) into stdout (fd 1) first and then pipe the combined stream into grep.

## My solve
**Flag:** `pwn.college{ULLpJNlHBLTKqi1C3P8qWaykNRr.QX1ATO0wSO5kjNzEzW}`
</br>
I redirected stderr into stdout using `2>&1`, then piped the combined stream to `grep` to filter for the flag string.
<br/>
TERMINAL WORKING : 
```
hacker@piping~grepping-errors:~$ /challenge/run 2>&1 | grep 'pwn.college'
[INFO] WELCOME! This challenge makes the following asks of you:
[INFO] - the challenge checks for a specific process at the other end of stderr : grep
[INFO] - the challenge will output a reward file if all the tests pass : /challenge/.data.txt

[HYPE] ONWARDS TO GREATNESS!

[INFO] This challenge will perform a bunch of checks.
[INFO] If you pass these checks, you will receive the /challenge/.data.txt file.

[TEST] You should have redirected my stderr to another process. Checking...
[TEST] Performing checks on that process!

[INFO] The process' executable is /nix/store/8b4vn1iyn6kqiisjvlmv67d1c0p3j6wj-gnugrep-3.11/bin/grep.
[INFO] This might be different than expected because of symbolic links (for example, from /usr/bin/python to /usr/bin/python3 to /usr/bin/python3.8).
[INFO] To pass the checks, the executable must be grep.

[PASS] You have passed the checks on the process on the other end of my stderr!
[PASS] Success! You have satisfied all execution requirements.
pwn.college{ULLpJNlHBLTKqi1C3P8qWaykNRr.QX1ATO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `2>&1` redirects stderr (fd 2) to the same destination as stdout (fd 1), allowing stderr to flow into a pipe.
2. After `2>&1` can be piped (`|`) the combined stream to another program (`grep` in this case) to filter error messages.

## References 
The materials provided by my mentor.
<br/>

# Filtering with grep -v
The challenge demanded filtering out lines containing the string `DECOY` from the mixed output of `/challenge/run` so that the single real flag remains visible.

## My solve
**Flag:** `pwn.college{wye404Yrtqv0VovLetSP_IYUXni.0FOxEzNxwSO5kjNzEzW}`
</br>
Using `grep -v` I filtered the output of `/challenge/run` to remove all lines containing the substring  `DECOY`, leaving only the genuine flag line.
<br/>
TERMINAL WORKING : 
```
hacker@piping~filtering-with-grep-v:~$ /challenge/run | grep -v DECOY
pwn.college{wye404Yrtqv0VovLetSP_IYUXni.0FOxEzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `grep -v PATTERN` prints only the lines that do not match PATTERN, which is handy when unwanted lines are easier to describe.

## References 
The materials provided by my mentor.
<br/>

# Writing to multiple programs
The challenge demanded duplicating the output of `/challenge/hack` and delivering it directly and simultaneously as stdin to both `/challenge/the` and `/challenge/planet`.

## My solve
**Flag:** `pwn.college{4GsN8pyyQ5qPn71uLRjGNxnmPCW.QXwgDN1wSO5kjNzEzW}`
</br>
I used `tee` together with output process substitution `>` so that tee wrote the stream into each command's stdin.
<br/>
TERMINAL WORKING : 
```
hacker@piping~writing-to-multiple-programs:~$ /challenge/hack | tee >( /challenge/the ) >( /challenge/planet )
This secret data must directly and simultaneously make it to /challenge/the and
/challenge/planet. Don't try to copy-paste it; it changes too fast.
6047255262329914861
Congratulations, you have duplicated data into the input of two programs! Here
is your flag:
pwn.college{4GsN8pyyQ5qPn71uLRjGNxnmPCW.QXwgDN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Combining `tee` with `>` lets you fan out a stream to multiple consumer processes (and not just files).

## References 
The materials provided by my mentor.
<br/>

# Split piping stdout and stderr 
The challenge demanded routing the stdout of `/challenge/hack` to `/challenge/planet` while simultaneously routing stderr to `/challenge/the`, without merging the two streams.

## My solve
**Flag:** `pwn.college{EAW6OruT69j8AC5rQA863i5FW-X.QXxQDM2wSO5kjNzEzW}`
</br>
I used process substitution for both file descriptors, redirecting stdout and stderr separately to different commands.
<br/>
TERMINAL WORKING : 
```
hacker@piping~split-piping-stderr-and-stdout:~$ /challenge/hack > >( /challenge/planet ) 2> >( /challenge/the )
Congratulations, you have learned a redirection technique that even experts
struggle with! Here is your flag:
pwn.college{EAW6OruT69j8AC5rQA863i5FW-X.QXxQDM2wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `> >(command)` attaches stdout to command's stdin and `2> >(command)` attaches stderr to command's stdin which allows separate routing.

## References 
The materials provided by my mentor.
<br/>

# Named pipes
The challenge demanded creating a FIFO at `/tmp/flag_fifo` and redirecting `/challenge/run`'s stdout to that FIFO so that reading from the FIFO reveals the flag.

## My solve
**Flag:** `pwn.college{0sOuE79Mw3qGEiYPbSDZpKIIUAU.01MzMDOxwSO5kjNzEzW}`
</br>
I created a named pipe with mkfifo, then wrote the writer and reader in a way that they could synchronize. One way I ran it was:
<br/>
TERMINAL WORKING 1 : 
```
hacker@piping~named-pipes:~$ mkfifo /tmp/flag_fifo
hacker@piping~named-pipes:~$ /challenge/run > /tmp/flag_
fifo
You're successfully redirecting /challenge/run to a FIFO at /tmp/flag_fifo!
Bash will now try to open the FIFO for writing, to pass it as the stdout of
/challenge/run. Recall that operations on FIFOs will *block* until both the
read side and the write side is open, so /challenge/run will not actually be
launched until you start reading from the FIFO!
```
This opens a reader in the background and then runs the writer which unblocks and writes into the FIFO.
TERMINAL WORKING 2 : 
```
hacker@piping~named-pipes:~$ cat /tmp/flag_fifo
You've correctly redirected /challenge/run's stdout to a FIFO at
/tmp/flag_fifo! Here is your flag:
pwn.college{0sOuE79Mw3qGEiYPbSDZpKIIUAU.01MzMDOxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `mkfifo` creates a named FIFO which behaves like a file path but blocks writers/readers until the other side opens the pipe.

## References 
The materials provided by my mentor.
<br/>
