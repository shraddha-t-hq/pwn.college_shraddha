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

