# Translating characters
The challenge demanded that I modify data using piping and the command ` tr `.

## My solve
**Flag:** `pwn.college{sIUYk7xVNzv5aEg7ntvhmUEc8Cu.01MxEzNxwSO5kjNzEzW}`
The given flag had to be toggled, so i wrote a string of uppercase, then lowercase letters to be replaced by the opposite string. This was done using the ` tr ` command.
<br/>
TERMINAL WORKING : 
```
hacker@data~translating-characters:~$ echo PWN.COLLEGE{SiuyK7XvnZV5AeG7NTVHMueC8cU.01mXeZnXWso5KJnZeZw} | tr ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ
pwn.college{sIUYk7xVNzv5aEg7ntvhmUEc8Cu.01MxEzNxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. ` tr ` is used to manipulate data and replace certain values from a string.
2. If multiple characters are to be replaced each character in the original string is replaced by the corresponding character in the replacement string. 

## References 
The materials provided by my mentor.
<br/>

# Deleting new lines 
The challenge demanded that I delete certain data from given data using the ` -d ` argument with ` tr `.

## My solve
**Flag:** `pwn.college{sL6pNteeO_fsslYsY2jz5x_UqV0.0VNxEzNxwSO5kjNzEzW}`
The flag was segmented into different lines. Just like characters, escape sequences can also be removed. Here I removed the newline escape sequence using the piping ` tr -d "\n" `. 
<br/>
TERMINAL WORKING : 
```
Deleting new lines 
hacker@data~deleting-newlines:~$ echo "pw
n
.c
olle
g
e
{s
L
6pNt
e
e
O
_f
s
slY
s
Y2
j
z
5
x_
Uq
V
0.0
VN
x
E
zN
xwS
O5k
j
N
zEz
W
}" | tr -d "\n"
pwn.college{sL6pNteeO_fsslYsY2jz5x_UqV0.0VNxEzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `-d` is used as an argument to `tr` to delete data.
2. Escape sequences can also be removed using `-d` which helps in compacting data spread over a large area (in this case, the flag).

## References 
The materials provided by my mentor.
<br/>

# Deleting characters 
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

# Extracting the first lines with head 
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

