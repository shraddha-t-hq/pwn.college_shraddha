# Learning from documentation
The challenge required reading the program documentation and invoking the documented flag option.

## My solve
**Flag:** `pwn.college{c0rBkTwDp_IxKPD6wTFlf9fHfAC.QX0ITO0wSO5kjNzEzW}`
I inspected the challenge docs and ran /challenge/challenge `--giveflag`, which the program accepted and printed the flag.
</br>
TERMINAL WORKING : 
```
hacker@man~learning-from-documentation:~$ /challenge/challenge --giveflag
Correct argument! Here is your flag:
pwn.college{c0rBkTwDp_IxKPD6wTFlf9fHfAC.QX0ITO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `--giveflag` yields the flag.
   

## References 
pwn.college
<br/>

# Learning complex usage 
The challenge required using a documented option that accepts a file path as an argument.

## My solve
**Flag:** `pwn.college{A80tesL00Kt7YZBTGvfpfmb5YDr.QX1ITO0wSO5kjNzEzW}`
I used the documented print option to request /flag.
</br>
TERMINAL WORKING : 
```
hacker@man~learning-complex-usage:~$ /challenge/challenge --printfile /flag
Correct argument! Here is the /flag file:
pwn.college{A80tesL00Kt7YZBTGvfpfmb5YDr.QX1ITO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. An argument command can be executed on a file using its absolute path.
2. --printfile is used to print the contents of a file. 

## References 
The materials provided by my mentor.
<br/>

# Reading manuals 
It demands using the `man` command to read the manuals of any command.

## My solve
**Flag:** `pwn.college{Ug1r7wdr_GJfpJlaUbUfCSlZSDf.QX0EDO0wSO5kjNzEzW}`
After reading the manual for `challenge`, the manual instructed to use the `--grwdrf VALUE` the value was also given as 170.
</br>
TERMINAL WORKING : 
```
hacker@man~reading-manuals:~$ man challenge

hacker@man~reading-manuals:~$ /challenge/challenge --grwdrf 170
Correct usage! Your flag: pwn.college{Ug1r7wdr_GJfpJlaUbUfCSlZSDf.QX0EDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `man` enables careful reading of the file to avoid trial-and-error to go staright to the necessary commands.

## References 
pwn.college
<br/>

# Searching manuals 
The challenge required finding and trying cryptic options discovered via documentation searches.

## My solve
**Flag:** `pwn.college{kRcv80oUKkP5jesYp4iUz3Br8ly.QX1EDO0wSO5kjNzEzW}`
I searched the manual of challenge using `/` to find the flag argument. Then the argument was invoked.
.
</br>
TERMINAL WORKING : 
```
hacker@man~searching-manuals:~$ man challenge
hacker@man~searching-manuals:~$ /challenge/challenge --axuovyn
Initializing...
Correct usage! Your flag: pwn.college{kRcv80oUKkP5jesYp4iUz3Br8ly.QX1EDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. To search within the manual '/' is used foloowed by the pattern we wnat to search.

## References 
pwn.college
<br/>

# Searching for manuals
The challenge required locating a small/helpful man page and following its instructions.
## My solve
**Flag:** `pwn.college{0nOS3kdrJisTclyRkmsqAmhqbWo.QX2EDO0wSO5kjNzEzW}`
I found the `-k` command which would lead another man page containing details to retrieve the file. I initially thought the command inferred would directly solve the question, but it was the other manual page. Then I entered that manual page and searched for the argument to retrieve the flag. After which I executed the /challenge/challenge using the argument.
</br>
TERMINAL WORKING : 
```
hacker@man~searching-for-manuals:~$ man man
hacker@man~searching-for-manuals:~$ man -k challenge
nkdrisclyk (1)       - print the flag!
hacker@man~searching-for-manuals:~$ /challenge/challenge "nkdris
clyk"
Incorrect usage! Please read the hidden challenge man page!
hacker@man~searching-for-manuals:~$ man nkdrisclyk
hacker@man~searching-for-manuals:~$ /challenge/challenge  --nkdris 032
Correct usage! Your flag: pwn.college{0nOS3kdrJisTclyRkmsqAmhqbWo.QX2EDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The man man command is a nested command that can be used to find other manual pages.

## References 
pwn.college
<br/>

# Helpful programs  
The challenge required using a program’s `--help` output to discover a helper option that reveals a secret value.

## My solve
**Flag:** `pwn.college{MTgu_SvSdyrqNdp84nSYlpYWWoK.QX3IDO0wSO5kjNzEzW}`
</br>
TERMINAL WORKING : 
</br>
```
hacker@man~helpful-programs:~$ /challenge/challenge --help
usage: a challenge to make you ask for help [-h] [--fortune]
                                            [-v]
                                            [-g GIVE_THE_FLAG]
                                            [-p]

optional arguments:
  -h, --help            show this help message and exit
  --fortune             read your fortune
  -v, --version         get the version number
  -g GIVE_THE_FLAG, --give-the-flag GIVE_THE_FLAG
                        get the flag, if given the correct
                        value
  -p, --print-value     print the value that will cause the -g
                        option to give you the flag
hacker@man~helpful-programs:~$ /challenge/challenge -g GIVE_THE_FLAG
usage: a challenge to make you ask for help [-h] [--fortune]
                                            [-v]
                                            [-g GIVE_THE_FLAG]
                                            [-p]
a challenge to make you ask for help: error: argument -g/--give-the-flag: invalid int value: 'GIVE_THE_FLAG'
hacker@man~helpful-programs:~$ /challenge/challenge -p
The secret value is: 843
hacker@man~helpful-programs:~$ /challenge/challenge -g 843
Correct usage! Your flag: pwn.college{MTgu_SvSdyrqNdp84nSYlpYWWoK.QX3IDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. --help can be used to navigate through commands.

## References 
pwn.college
<br/>

# Help for builtins
The challenge required using shell builtin help to discover a secret for a builtin command implementation.

## My solve
**Flag:** `pwn.college{IEfrLqTSt165s94JCGdcYPVyehN.QX0ETO0wSO5kjNzEzW}`
</br>
TERMINAL WORKING : 
```
hacker@man~help-for-builtins:~$ help challenge
challenge: challenge [--fortune] [--version] [--secret SECRET]
    This builtin command will read you the flag, given the right arguments!

    Options:
      --fortune         display a fortune
      --version         display the version
      --secret VALUE    prints the flag, if VALUE is correct

    You must be sure to provide the right value to --secret. That value
    is "IEfrLqTS".
hacker@man~help-for-builtins:~$ /challenge/challenge --secret "IEfrLqTS"
bash: /challenge/challenge: No such file or directory
hacker@man~help-for-builtins:~$ challenge --secret "IEfrLqTS"
Correct! Here is your flag!
pwn.college{IEfrLqTSt165s94JCGdcYPVyehN.QX0ETO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Shell builtins use help (not man) for documentation.


## References 
pwn.college
<br/>

