# Intro to Commands
The challenge demanded to invoke my first command. The command should have been 'hello'.

## My solve
**Flag:** `pwn.college{Uw-M_2BSnbwDubk5bGXAnedPe0S.QX3YjM1wSO5kjNzEzW}`

This challenge was solved using the SSH route. 
After setting up the SSH with the system terminal the `hello` command was entered.
TERMINAL WORKING : 
```
hacker@hello~intro-to-commands:~$ hello
Success! Here is your flag:
pwn.college{Uw-M_2BSnbwDubk5bGXAnedPe0S.QX3YjM1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. On the command line, when any writing a command line and hitting enter, invokes the command.
2. The command `whoami` , yields the name of the user (hacker, in this case)
3. Commands are case-sensitive i.e. `hello` is different from `HELLO`   

## References 
The materials provided by my mentor.
<br/>

# Intro to Arguments 
The challenge demanded to add to the command and use an argument(which is the additional data passed along with the command).

## My solve
**Flag:** `pwn.college{483anqetBbkD3mp-P7eYz593y6s.QX4YjM1wSO5kjNzEzW}`

I first typed in the command `hello`, followed by the argument `hackers`. 
TERMINAL WORKING : 
```
hacker@hello~intro-to-arguments:~$ hello hackers
Success! Here is your flag:
pwn.college{483anqetBbkD3mp-P7eYz593y6s.QX4YjM1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed.


## What I learned
I learned the following from this challenge : 
1. A command can also be followed by another entity called an argument.
2. The first word of the sentence entered is interpreted by the shell as a command while the second word is interpreted as the argument that comes with it.
3. The `echo` command is simply used to echo the arguments back onto the terminal (display it again onto the terminal).
4. Commands like `hello` can also have arguments.  

<br/>

# Command History 
The challenge aimed to teach that the shell maintains a history of all the commands used. Keys like upward and downward arrows can be used to scroll up and down the history.

## My solve
**Flag:** `pwn.college{g-ga50-qGe9tJvfMOgrBjJEXsTS.0lNzEzNxwSO5kjNzEzW}`

As instructed, I pressed the upward arrow on the keyboard. As the flag was injected into the command history, I could see it after pressing the upward arrow.

TERMINAL WORKING : 
```
hacker@hello~command-history:~$ the flag is pwn.college{g-ga50-qGe9tJvfMOgrBjJEXsTS.0lNzEzNxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed.


## What I learned
I learned the following from this challenge : 
1. The shell keeps a history of all the commands used.
2. This reduces the effort that the user has to put in organising the flow and recalling the chain of events. It also reduces the time taken in manually writing the arguments.


