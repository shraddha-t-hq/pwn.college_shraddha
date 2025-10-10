# The PATH Variable
The challenge required manipulating the `PATH` variable to prevent `/challenge/run` from deleting the flag.
## My solve
**Flag:** `pwn.college{8oElOFbAoGfW_2XbGuUgrHQ2jEf.QX2cDM1wSO5kjNzEzW}`

I cleared the `PATH` variable using `PATH=""` and then ran `/challenge/run`. Since the `rm` command could not be found, the flag file was not deleted.
TERMINAL WORKING : 
```
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{8oElOFbAoGfW_2XbGuUgrHQ2jEf.QX2cDM1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1.The `PATH` variable determines where the shell looks for executable commands.
2. Modifying or clearing PATH can prevent commands from being found and executed.


## References 
The materials provided by my mentor.
<br/>

# Setting PATH
The challenge required updating the `PATH` variable to include the directory containing the `win` command.
## My solve
**Flag:** `pwn.college{8eEBfCNiZfYl3k17V1T7Zgxi8Nh.QX1cjM1wSO5kjNzEzW}`

I set the `PATH` variable to `/challenge/more_commands/` and ran `/challenge/run`. The win command executed successfully and returned the flag.
TERMINAL WORKING : 
```
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{8eEBfCNiZfYl3k17V1T7Zgxi8Nh.QX1cjM1wSO5kjNzEzW}
```

## What I learned
I learned the following from this challenge : 
1. Adding directories to `PATH` allows the shell to locate commands in non-standard locations.

## References 
The materials provided by my mentor.
<br/>

# Finding Commands
The challenge required locating the directory of a command using the `which` command.
## My solve
**Flag:** `pwn.college{IG4Nwin0kM482RhDHYW8g3WYq_2.01NzEzNxwSO5kjNzEzW}`

I ran `which win` to find its location, then navigated to the directory and displayed the flag file using `cat flag`. 
TERMINAL WORKING : 
```
hacker@path~finding-commands:~$ which win
/challenge/paths/32329/win
hacker@path~finding-commands:~$ cd /challenge/paths/32329
hacker@path~finding-commands:/challenge/paths/32329$ cat flag
pwn.college{IG4Nwin0kM482RhDHYW8g3WYq_2.01NzEzNxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `which` shows the full path of a command found in $PATH.

## References 
The materials provided by my mentor.
<br/>

# Adding Commands
The challenge required creating a `win` command, adding its location to `PATH`, and enabling `/challenge/run` to find it.
## My solve
**Flag:** `pwn.college{UDHYbjZDnGRLqRL4ZakWCKnpg-m.QX2cjM1wSO5kjNzEzW}`
<br/>
Firstly, I located cat with `which cat`, created a win script that invokes the absolute `/run/dojo/bin/cat /flag`, made it executable, then I set `PATH=/home/hacker` (where I placed win), and then ran `/challenge/run`.
TERMINAL WORKING : 
```
hacker@path~adding-commands:~$ which cat
/run/dojo/bin/cat
hacker@path~adding-commands:~$ touch win
hacker@path~adding-commands:~$ printf '#!/bin/bash\n\n/run/dojo/bin/cat /flag' > win
hacker@path~adding-commands:~$ chmod a+x win
hacker@path~adding-commands:~$ PATH=/home/hacker
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{UDHYbjZDnGRLqRL4ZakWCKnpg-m.QX2cjM1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. You can create simple scripts and expose them by adding their directory to PATH.
2. Using absolute paths for standard utilities (e.g., `/run/dojo/bin/cat`) avoids problems PATH is overwritten.

## References 
SENSAI
<br/>

# Hijack Commands
The challenge required preventing `/challenge/run` from deleting the flag by providing a non-malicious `rm` in a directory on `PATH`.
## My solve
**Flag:** `pwn.college{Ujmh4lwWe_euCvRL9Gh2RKblvt-.QX3cjM1wSO5kjNzEzW}`
<br/>
I created a fake `rm` script in my home directory that actually cats /flag via `/run/dojo/bin/cat /flag`, made it executable, set `PATH=/home/hacker` so my rm is found first, and ran `/challenge/run`. The program invoked my rm.
TERMINAL WORKING : 
```
hacker@path~hijacking-commands:~$ touch rm
hacker@path~hijacking-commands:~$ printf '#!/bin/bash\n\n/run/dojo/bin/cat /flag' > rm
hacker@path~hijacking-commands:~$ chmod a+x rm
hacker@path~hijacking-commands:~$ PATH=/home/hacker
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
pwn.college{Ujmh4lwWe_euCvRL9Gh2RKblvt-.QX3cjM1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Placing a program with the same name as a common utility earlier in PATH lets you “hijack” calls to that utility.

## References 
SENSAI
<br/>
