# Launching Screen
The challenge required launching a screen session to retrieve the flag.
## My solve
**Flag:** `pwn.college{UotTMbUgIWiNQBOpArV2yCvh5_4.0VN4IDOxwSO5kjNzEzW}`

I started a screen session by running `screen` command. 
TERMINAL WORKING : 
```
Congratulations! You're inside a screen session!
Here's your flag:
pwn.college{UotTMbUgIWiNQBOpArV2yCvh5_4.0VN4IDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `screen` launches a virtual terminal session.

## References 
The materials provided by my mentor.
<br/>

# Detaching and Attaching
The challenge required detaching from a screen session, running a command that sends the flag to the detached session, then reattaching to read it.
## My solve
**Flag:** `pwn.college{M2Z9jTuI2QeZOvs3nRCrgnSLGXg.0lN4IDOxwSO5kjNzEzW}`

I launched screen and detached using `Ctrl-A d`.
I then ran /challenge/run which detected the detached screen session and sent the flag to it. 
I reattached with `screen -r` and read the flag in the reattached session.
TERMINAL WORKING : 
```
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen
[detached from 139.pts-0.terminal-multiplexing~detaching-and-attaching]
hacker@terminal-multiplexing~detaching-and-attaching:~$ /challenge/run
Found detached screen session: 139.pts-0.terminal-multiplexing~detaching-and-attaching
Sending flag to your screen session...

Flag sent! Now reattach to your screen session with:

  screen -r

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching:~$ screen -r
[screen is terminating]
```
SCREEN WORKING :
```
hacker@terminal-multiplexing~detaching-and-attaching:~$
hacker@terminal-multiplexing~detaching-and-attaching:~$ echo Yes! Flag is: pwn.college{M2Z9jTuI2QeZOvs3nRCrgnSLGXg.0lN4IDOxwSO5kjNzEzW}
Yes! Flag is: pwn.college{M2Z9jTuI2QeZOvs3nRCrgnSLGXg.0lN4IDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `Ctrl-A d` is used to detach a screen session and `screen -r` is used to reattach.

## References 
The materials provided by my mentor.
<br/>

# Finding Sessions
The challenge required listing existing screen sessions and attaching to the one that contains the flag.
## My solve
**Flag:** `pwn.college{I4TVkVvB9H8HwhykYOLWGLcP8QO.01N4IDOxwSO5kjNzEzW}`

I listed screen sessions with `screen -ls`, identified the available session names, and attached to the session that contained the flag using `screen -r <session>`. 

TERMINAL WORKING : 
```
hacker@terminal-multiplexing~finding-sessions:~$ screen -ls
There are screens on:
        144.session_18007d2966be2ec2    (Detached)
        147.session_55235e4300678193    (Detached)
        150.session_1d4d2c9ab010b486    (Detached)
3 Sockets in /home/hacker/.screen.
hacker@terminal-multiplexing~finding-sessions:~$ screen -r session_18007d2966be2ec2
[screen is terminating]
hacker@terminal-multiplexing~finding-sessions:~$ screen
[detached from 193.pts-3.terminal-multiplexing~finding-sessions]

Flag :pwn.college{I4TVkVvB9H8HwhykYOLWGLcP8QO.01N4IDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `screen -ls` lists active screen sessions with identifiers.
2. Specific sessions can be attached using its name or PID (e.g., screen -r <session_name>).

## References 
The materials provided by my mentor.

<br/>

# Switching Windows 
The challenge required switching windows inside a screen session to find the flag in a specific window.
## My solve
**Flag:** `pwn.college{srAppfBPIiKnD6sidaNspwx_Srl.0FO4IDOxwSO5kjNzEzW}`

I attached to the provided screen session and switched to the target window using `Ctrl-A 0`. The flag was present in the indicated window.
TERMINAL WORKING : 
```
hacker@terminal-multiplexing~switching-windows:~$ screen -r
[screen is terminating]

hacker@terminal-multiplexing~switching-windows:~$  cat <<MSG
> Excellent work! You found window 0!
> Here is your flag: pwn.college{srAppfBPIiKnD6sidaNspwx_Srl.0FO4IDOxwSO5kjNzEzW}
```

## What I learned
I learned the following from this challenge : 
1. `Ctrl-A 0..9` switch windows in screen to the nth window.
2. `Ctrl-A "` brings up a window-selection menu.
3. `Ctrl-A c/n/p` are used to create a new window, move to the next window and go to the previous window respectively.

## References 
The materials provided by my mentor.
<br/>

# Detaching and Attaching (tmux)
The challenge required detaching from a `tmux` session, running a command that sends the flag to the detached session, then reattaching to see it.
## My solve
**Flag:** `pwn.college{4gwZxtcj43W0cAHHKnAaeeBNRBh.0VO4IDOxwSO5kjNzEzW}`

I launched a tmux session and detached it using `Ctrl-B d`. Then, I ran `/challenge/run` which sent the flag to it. 
I reattached with `tmux a` and read the flag.
TERMINAL WORKING : 
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux
[detached (from session 0)]
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ /challenge/run
Found detached tmux session: 0
Sending flag to your tmux session...

Flag sent! Now reattach to your tmux session with:
  tmux attach

You'll find the flag waiting for you there!
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$ tmux a

```

TMUX WORKING :
```
hacker@terminal-multiplexing~detaching-and-attaching-tmux:~$  echo Congratulations, here is your flag: pwn.college{4gwZxtcj43W0cAHHKnAaeeBNRBh.0VO4IDOxwSO5kjNzEzW}

```


## What I learned
I learned the following from this challenge : 
1. tmux uses `Ctrl-B` as its command prefix (e.g., `Ctrl-B d` to detach).
2. `tmux attach` (or `tmux a`) can be used to reattach to detached sessions.

## References 
The materials provided by my mentor.
<br/>

# Switching Windows(tmux)
The challenge required switching windows inside a tmux session to find the flag in the target window.
## My solve
**Flag:** `pwn.college{cftw5lfLHjJxKalgVGo6EusYSL_.0FM5IDOxwSO5kjNzEzW}`

I used tmux window navigation Ctrl-B 0 to traverse to the window that contained the flag. The flag was printed there.
TERMINAL WORKING : 
```
hacker@terminal-multiplexing~switching-windows-tmux:~$ Here is your flag: pwn.college{cftw5lfLHjJxKalgVGo6EusYSL_.0FM5IDOxwSO5kjNzEzW}
```

## What I learned
I learned the following from this challenge : 
1. `Ctrl-B 0..9` switch windows in tmux.
2. For all other commands tmux just uses Ctrl-B instead of A.

## References 
The materials provided by my mentor.
<br/>
