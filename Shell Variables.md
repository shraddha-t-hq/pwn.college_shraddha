# Printing variables 
The challenge demanded that I print the contents of the environment variable named `FLAG`.

## My solve
**Flag:** `pwn.college{Q8GkWhGm_6a37Hl7Usn-BVOV55J.QX3UTN0wSO5kjNzEzW}`

I printed the `FLAG` variable using `echo $FLAG`.
<br/>
TERMINAL WORKING : 
```
hacker@variables~printing-variables:~$ echo $FLAG
pwn.college{Q8GkWhGm_6a37Hl7Usn-BVOV55J.QX3UTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `$VAR` is used to expand and print a variable’s value.
2. `echo` is the simplest way to display simple variable contents.

## References 
The materials provided by my mentor.
<br/>


# Setting variables 
The challenge required setting a shell variable named `PWN` with the exact value `COLLEGE`.

## My solve
**Flag:** `pwn.college{YlhUEQLJ1QbrKHFZNNA-hiGJTuB.QX5UTN0wSO5kjNzEzW}`

I assigned the value by using `PWN=COLLEGE`.
<br/>
TERMINAL WORKING : 
```
hacker@variables~setting-variables:~$ PWN=COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{YlhUEQLJ1QbrKHFZNNA-hiGJTuB.QX5UTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Variable assignment uses `NAME=value` with **no spaces** around `=`.
   
## References 
The materials provided by my mentor.
<br/>

# Multi-word variables 
The challenge required setting `PWN` to the multi-word value `"COLLEGE YEAH"`.

## My solve
**Flag:** `pwn.college{UD6uehYNTinAdEDsB3KseX22g3U.QXwYTN0wSO5kjNzEzW}`
I set the multi-word value using double quotes. The challenge accepted the quoted multi-word string.
<br/>
TERMINAL WORKING : 
```
hacker@variables~multi-word-variables:~$ PWN="COLLEGE YEAH"
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{UD6uehYNTinAdEDsB3KseX22g3U.QXwYTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Quotes (`""`) are used to include spaces inside variable values.
2. Without quotes, the shell treats tokens separated by spaces as separate words and commands.

## References 
The materials provided by my mentor.
<br/>

# Exporting variables 
The challenge required exporting variable `PWN` with value `COLLEGE` so child processes inherit it, 
while setting `COLLEGE=PWN` only in the current shell (not exporting it) and then run `/challenge/run` to verify.

## My solve
**Flag:** `pwn.college{01GpJc9z3-UMnIg70ew1eEJKW1C.QXyYTN0wSO5kjNzEzW}`
I set `COLLEGE=PWN` (not exported) and exported `PWN=COLLEGE` using the export command. Then I started a child shell (`sh`), echoed PWN and ran `/challenge/run`.
<br/>
TERMINAL WORKING : 
```
hacker@variables~exporting-variables:~$ COLLEGE=PWN
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ export PWN=COLLEGE
You've set the PWN variable to the proper value!
You've set the COLLEGE variable to the proper value!
hacker@variables~exporting-variables:~$ sh
sh-5.2$ echo "PWN is $PWN"
PWN is COLLEGE
sh-5.2$ /challenge/run
CORRECT!
You have exported PWN=COLLEGE and set, but not exported, COLLEGE=PWN. Great
job! Here is your flag:
pwn.college{01GpJc9z3-UMnIg70ew1eEJKW1C.QXyYTN0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `export NAME=value` creates an environment variable propagated to child processes.
2. Variables set without `export` remain local to the current shell.

## References 
The materials provided by my mentor.
<br/>

# Printing exported variables 
The challenge asked to list exported variables (to find FLAG) using `env`.

## My solve
**Flag:** `pwn.college{wIgQcG6eCVt4WZ8GzL3icmDN6uL.QX4UTN0wSO5kjNzEzW}`
I ran `env` to print all exported environment variables; `FLAG` appeared in the output, revealing the flag.
<br/>
TERMINAL WORKING : 
```
hacker@variables~printing-exported-variables:~$ env
SHELL=/run/dojo/bin/bash
HOSTNAME=variables~printing-exported-variables
PWD=/home/hacker
MANPATH=/run/dojo/share/man:
DOJO_AUTH_TOKEN=2c8a549ad1c461bad645b5ccf37cc1c26d643185f0836c5ca224a4932820d4b1
HOME=/home/hacker
LANG=C.UTF-8
FLAG=pwn.college{wIgQcG6eCVt4WZ8GzL3icmDN6uL.QX4UTN0wSO5kjNzEzW}
TERMINFO=/run/dojo/share/terminfo
TERM=xterm-256color
SHLVL=2
LC_CTYPE=C.UTF-8
SSL_CERT_FILE=/run/dojo/etc/ssl/certs/ca-bundle.crt
PATH=/run/challenge/bin:/run/dojo/bin:/root/.cargo/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DEBIAN_FRONTEND=noninteractive
_=/run/dojo/bin/env

```

## What I learned
I learned the following from this challenge : 
1. `env` prints all exported environment variables visible to the current shell.

## References 
The materials provided by my mentor.
<br/>

# Storing command output
The challenge required capturing the stdout of `/challenge/run` directly into a shell variable `PWN` using command substitution.

## My solve
**Flag:** `pwn.college{Mit_IoCqu6naKvFbwmrk3AwQHuH.QX1cDN1wSO5kjNzEzW}`
I executed `/challenge/run` inside `$()` and assigned it to PWN.Then I echoed `PWN`.
<br/>
TERMINAL WORKING : 
```
Storing command output
hacker@variables~storing-command-output:~$ PWN=$(/challenge/run)
Congratulations! You have read the flag into the PWN variable. Now print it out
and submit it!
hacker@variables~storing-command-output:~$ echo "$PWN"
pwn.college{Mit_IoCqu6naKvFbwmrk3AwQHuH.QX1cDN1wSO5kjNzEzW}
```

## What I learned
I learned the following from this challenge : 
1. Command substitution `VAR=$(command)` captures command's stdout into `VAR`.

## References 
The materials provided by my mentor.
<br/>

# Reading input
The challenge required using `read` to capture input (from stdin) into `PWN`.

## My solve
**Flag:** `pwn.college{wd6lZ4gEnqES1iipbk1v1uCqh70.QX4cTN0wSO5kjNzEzW}`
I ran `read PWN` and supplied `COLLEGE` as input. 
<br/>
TERMINAL WORKING : 
```
hacker@variables~reading-input:~$ read PWN
COLLEGE
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{wd6lZ4gEnqES1iipbk1v1uCqh70.QX4cTN0wSO5kjNzEzW}
```

## What I learned
I learned the following from this challenge : 
1. `read` VAR reads a line from stdin into VAR.

## References 
The materials provided by my mentor.
<br/>

# Reading files
The challenge required reading the contents of `/challenge/read_me` into the `PWN` variable in a single command using input redirection.

## My solve
**Flag:** `pwn.college{035RwvVNc9U5lp2Ln5QU1b_-ahV.QXwIDO0wSO5kjNzEzW}`
I used input redirection(`<`) with `read`.
<br/>
TERMINAL WORKING : 
```
hacker@variables~reading-files:~$ read PWN < /challenge/read_me
You've set the PWN variable properly! As promised, here is the flag:
pwn.college{035RwvVNc9U5lp2Ln5QU1b_-ahV.QXwIDO0wSO5kjNzEzW}

```

## What I learned
I learned the following from this challenge : 
1. `read VAR < file` reads the first line of file into the shell variable VAR in the current shell.

## References 
The materials provided by my mentor.
