# Chaining with semicolon
The challenge demanded that I run two commands in sequence using the `;` operator.

## My solve
**Flag:** `pwn.college{U8-uiUlnQrvkg65G81_Lo9QZQi-.QX1UDO0wSO5kjNzEzW}`
I ran `/challenge/pwn` and then `/challenge/college` in one line **separated by a semicolon** so both commands executed one after the other.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn ; /challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{U8-uiUlnQrvkg65G81_Lo9QZQi-.QX1UDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The semicolon `;` runs commands sequentially regardless of the previous command's exit status.
2. It is used to carry out several commands in one line.

## References 
The materials provided by my mentor.
<br/>

# Building on success 
The challenge required using `&&` so the second command runs only if the first succeeds.

## My solve
**Flag:** `pwn.college{MN1NMESPGJFrgkHVvyjiBYylelQ.0lM0MDOxwSO5kjNzEzW}`
I chained `/challenge/first-success` and `/challenge/second` with `&&` so the second command is executed only after the first exited successfully.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~building-on-success:~$ /challenge/first-success && /challenge/second
Nice chaining! Flag: pwn.college{MN1NMESPGJFrgkHVvyjiBYylelQ.0lM0MDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `command1 && command2` runs command2 only if command1 exits with status 0.
2. `&&` is useful for conditional workflows where later steps depend on earlier success.
## References 
The materials provided by my mentor.
<br/>

# Handling failure 
This challenge required using `||` to run a fallback command when the first fails.

## My solve
**Flag:** `pwn.college{4DqMYq6fm0pdXIu5OU0vgxP4mrw.01M0MDOxwSO5kjNzEzW}}`
I used `/challenge/first-failure || /challenge/second` so the second command ran only when the first failed.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~handling-failure:~$ /challenge/first-failure || /challenge/second
Nice chaining! Flag: pwn.college{4DqMYq6fm0pdXIu5OU0vgxP4mrw.01M0MDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `command1 || command2` runs command2 only if command1 exits with a non-zero status.

## References 
The materials provided by my mentor.
<br/>

# Your First Shell Script
The challenge asked me to put two commands into a script and run it with bash.

## My solve
**Flag:** `pwn.college{0-Ldb4dF3cja1ES_oullsN4_p-q.QX4ETO0wSO5kjNzEzW}`
I created `script.sh` containing the two commands and executed it with `bash`.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~your-first-shell-script:~$ echo '/challenge/pwn ; /challenge/college' > x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{kZ1soe4e6Vn1PLIdMUfvAUkohnK.QXxcDO0wSO5kjNzEzW}`
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Scripts let you store multiple commands in a file and run them together with `bash <name of the script>`.

## References 
The materials provided by my mentor.
<br/>

# Redirecting script output 
This level required piping the combined output of a script into another command.
## My solve
**Flag:** `pwn.college{0-Ldb4dF3cja1ES_oullsN4_p-q.QX4ETO0wSO5kjNzEzW}`
I wrote a script that ran `/challenge/pwn` and `/challenge/college`, then piped the script’s output into `/challenge/solve`.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~redirecting-script-output:~$ echo '/challenge/pwn ; /challenge/college' > script.sh
hacker@chaining~redirecting-script-output:~$ bash script.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{0-Ldb4dF3cja1ES_oullsN4_p-q.QX4ETO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Redirection of script’s stdout can be done by a command: `bash <name of script> | other`.

## References 
The materials provided by my mentor.
<br/>

# Executable shell scripts 
The task was to make a script executable and run it directly **without** invoking `bash`.
## My solve
**Flag:** `pwn.college{wN8B0LQTPRuDTE8vLW17wllBoI-.QX0cjM1wSO5kjNzEzW}`
I wrote `script.sh` to call `/challenge/solve`, investigated the permissions of script.sh, set executable permissions, and ran it with `./script.sh`.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~executable-shell-scripts:~$ echo '/challenge/solve' > script.sh
hacker@chaining~executable-shell-scripts:~$ ls -l script.sh
-rw-r--r-- 1 hacker hacker 17 Oct  8 18:17 script.sh
hacker@chaining~executable-shell-scripts:~$ chmod u=rwx,g=rx,o=rx script.sh
hacker@chaining~executable-shell-scripts:~$ pwd
/home/hacker
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{wN8B0LQTPRuDTE8vLW17wllBoI-.QX0cjM1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Scripts can directly be called/accessed using ./<script_name>
2. Permissions of the scripts can be changed using `chmod`.

## References 
The materials provided by my mentor.
<br/>


# Understanding shebangs 
The challenge asked for a script at `/home/hacker/solve.sh` whose first line is a proper shebang and which prints hack the planet.
## My solve
**Flag:** `pwn.college{EmGSb2U3HWOiS0KUcOnqGkJACpD.0VOzMDOxwSO5kjNzEzW}`
I created `/home/hacker/solve.sh` with `#!/bin/bash` as the first line and `echo "hack the planet"` after it.
The file was written into using printf as it was the best method i could think of, then I made it executable and ran `/challenge/run`
<br/>
TERMINAL WORKING : 
```
hacker@chaining~understanding-shebangs:~$ touch solve.sh
hacker@chaining~understanding-shebangs:~$ printf '#!/bin/bash\n\necho "hack the planet"\n' > solve.sh
hacker@chaining~understanding-shebangs:~$ chmod a+x solve.sh
hacker@chaining~understanding-shebangs:~$ /challenge/run
Testing your script...
Perfect! Your flag:
Flag: pwn.college{EmGSb2U3HWOiS0KUcOnqGkJACpD.0VOzMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The shebang (`#!`) must be the very first line and specifies the interpreter (e.g., `/bin/bash`).
2. The kernel uses the shebang to run the file with the specified interpreter when executed directly.

## References 
The materials provided by my mentor.
<br/>

# Scripting with arguments
This level required a script that takes two arguments and prints them in reverse order.
## My solve
**Flag:** `pwn.college{wg1TP7WIYDjXRN0OTASBdURuHat.0VNzMDOxwSO5kjNzEzW}`

I wrote `/home/hacker/solve.sh` that echoes `$2 $1`, then ran it with two arguments.
<br/>
TERMINAL WORKING : 
```
hacker@chaining~scripting-with-arguments:~$ touch solve.sh
hacker@chaining~scripting-with-arguments:~$ printf '#!/bin/bash\n\necho "$2 $1"' > solve.sh
hacker@chaining~scripting-with-arguments:~$  bash /home/hacker/solve.sh hacker home
home hacker
hacker@chaining~scripting-with-arguments:~$ /challenge/run
Correct! Your script properly reversed the arguments.
Here's your flag:
pwn.college{wg1TP7WIYDjXRN0OTASBdURuHat.0VNzMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `$1` and `$2` refer to the first and second script arguments respectively.

## References 
The materials provided by my mentor.
<br/>

# Scripting with conditions
The challenge required printing `college` when the single argument is `pwn`, otherwise printing nothing.
## My solve
**Flag:** `pwn.college{YtmKXGVLjLg03CIMn5BrbJmUfvY.0lNzMDOxwSO5kjNzEzW}`

I used an `if` statement checking `$1 == "pwn"` and echoing `college` when **true**.
<br/>
SCRIPT :
```
#!/bin/bash

if  [ "$1" == "pwn" ]
then
	echo  "college"
fi
```
TERMINAL WORKING : 
```
hacker@chaining~scripting-with-conditionals:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-conditionals:~$ /challenge/run
Correct! Your script properly handles all the conditions.
Here's your flag:
pwn.college{YtmKXGVLjLg03CIMn5BrbJmUfvY.0lNzMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Bash `if` syntax requires spaces around `[` and `]`, and then and `fi` to delimit the block.
2. Conditions can control whether a script outputs anything at all.

## References 
The materials provided by my mentor.
<br/>

# Scripting with default cases
This task extended the previous one by requiring an `else` to print `nope` for other inputs.
## My solve
**Flag:** `pwn.college{4_tVxrHLdUKUVZdf9Aa3BE9EXFD.01NzMDOxwSO5kjNzEzW}`

I added an `else` branch to print `nope` when the argument is **not** `pwn`.
<br/>
SCRIPT :
```
if  [ "$1" == "pwn" ]
then
	echo  "college"
else
	echo "nope"
fi
```
<br/>
TERMINAL WORKING : 
```
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-default-cases:~$ bash /home/hacker/solve.sh college
nope
hacker@chaining~scripting-with-default-cases:~$ /challenge/run
Correct! Your script properly handles the if/else conditions.
Here's your flag:
pwn.college{4_tVxrHLdUKUVZdf9Aa3BE9EXFD.01NzMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `else` provides a default action when the `if` condition is **false**.

## References 
The materials provided by my mentor.
<br/>

# Scripting with multiple cases
This level required `elif` branches to handle multiple inputs with different outputs.
## My solve
**Flag:** `pwn.college{Y7589bfpIPPA4QVgwTwMdXw9848.0FOzMDOxwSO5kjNzEzW}`

I implemented `if` , `elif` , `else` to cover `hack`, `pwn`, `learn`, and a default `unknown` case.
<br/>
SCRIPT :
```
#!/bin/bash

if [ "$1" == "hack" ]
then
    echo "the planet"
elif [ "$1" == "pwn" ]
then
    echo "college"
elif [ "$1" == "learn" ]
then
    echo "linux"
else
    echo "unknown"
fi
```
TERMINAL WORKING : 
```
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh hack
the planet
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh pwn
college
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh learn
linux
hacker@chaining~scripting-with-multiple-conditions:~$ bash /home/hacker/solve.sh hey
unknown
hacker@chaining~scripting-with-multiple-conditions:~$ /challenge/run
Correct! Your script properly handles all the conditions with elif.
Here's your flag:
pwn.college{Y7589bfpIPPA4QVgwTwMdXw9848.0FOzMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `elif` allows checking multiple exclusive conditions in order.
2. Order matters: the first matching branch runs and subsequent elifs are skipped.

## References 
The materials provided by my mentor.
<br/>

# Scripting with conditions
This challenge asked me to inspect `/challenge/ru`n to find the hardcoded password and provide it as input.
## My solve
**Flag:** `pwn.college{oolN2yAVdyKpmwpOHKA33BJU7ur.0lMwgDOxwSO5kjNzEzW}`

I used `cat` to read the script, found the correct password - `hack the PLANET`, then ran `/challenge/run` and provided that input to get the flag.
<br/>

TERMINAL WORKING : 
```
hacker@chaining~reading-shell-scripts:~$ cat /challenge/run
#!/opt/pwn.college/bash

read GUESS
if [ "$GUESS" == "hack the PLANET" ]
then
        echo "CORRECT! Your flag:"
        cat /flag
else
        echo "Read the /challenge/run file to figure out the correct password!"
fi
hacker@chaining~reading-shell-scripts:~$ /challenge/run
hack the PLANET
CORRECT! Your flag:
pwn.college{oolN2yAVdyKpmwpOHKA33BJU7ur.0lMwgDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Many challenges are implemented as readable shell scripts and `cat` can be used on the file to inspect behavior and secrets.
2. In order to run certain challenges, one must know how to read scripts carefully.

## References 
The materials provided by my mentor.
<br/>

# NOTE 
Due to certain access issues, i had to create and write into files using the terminal (*Your first shell script* ---> *Executable shell scripts*).
There onwards, it was a bit difficult to write into the files using terminal, so I used the *Desktop* of pwn.college to solve them.
(*Understanding shebangs* -->*Scripting with Multiple Conditions*)
Personally, I tried using shebang on my WSL system, without logging in with the key, and as far as my system is concerned, it works.

# DOUBTS 
If possible, I would really like to discuss why I could not access my files, as i did not find any answers on the internet.
I have a few doubts regarding the concept of accessing files from my system when I am logged into the pwn.college server. 
