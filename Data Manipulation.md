# Translating characters
The challenge demanded that I modify data using piping and the command ` tr `.

## My solve
**Flag:** `pwn.college{sIUYk7xVNzv5aEg7ntvhmUEc8Cu.01MxEzNxwSO5kjNzEzW}`
<br/>
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
<br/>
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

# Extracting the first lines with head 
The challenge demanded that I grab only the first seven lines of a program’s output and pipe those lines into another program (/challenge/college) so it prints the flag. 
## My solve
**Flag:** `pwn.college{I8PMEEzY9jj7867pQjoJjuRREV1.0lNxEzNxwSO5kjNzEzW}`
<br/>
I ran `/challenge/pwn`, limited its output to the first 7 lines using `head -n 7`, and piped that into `/challenge/college`. 
<br/>
TERMINAL WORKING : 
```
Extracting the first line with head
hacker@data~extracting-the-first-lines-with-head:~$ /challenge/pwn | head -n 7 | /challenge/college
Congratulations, you piped the right codes!
pwn.college{I8PMEEzY9jj7867pQjoJjuRREV1.0lNxEzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `head -n <number>` extracts the first n lines of input — useful to reduce program output to only what you need.

## References 
The materials provided by my mentor.
<br/>

# Extracting specific sections of text
The challenge demanded that I extract the second column (single characters) from many lines of numeric and character pairs produced by `/challenge/run`, then join those characters into a single continuous flag string. 
## My solve
**Flag:** `pwn.college{QfQ1A0Xv2jiB6-ebsrEcI4vYNND.01NxEzNxwSO5kjNzEzW}`
<br/>
I ran `/challenge/run`, used cut `-d " " -f 2` to extract the second column, and piped the result to `tr -d "\n"` to join them together into one line.
<br/>
TERMINAL WORKING : 
```
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run
626 p
10860 w
15468 n
23521 .
9923 c
972 o
22124 l
780 l
18086 e
20883 g
7341 e
11554 {
12948 Q
20078 f
22039 Q
178 1
24807 A
32706 0
18268 X
28961 v
18783 2
13952 j
11847 i
23502 B
28770 6
18647 -
8361 e
26640 b
10999 s
18674 r
2433 E
8827 c
14860 I
7722 4
32121 v
15574 Y
18211 N
25428 N
24829 D
4387 .
20496 0
30767 1
24511 N
13782 x
10343 E
11062 z
8383 N
5809 x
25589 w
9108 S
32713 O
30686 5
4588 k
12145 j
16135 N
26915 z
12298 E
31707 z
9856 W
11951 }
hacker@data~extracting-specific-sections-of-text:~$ /challenge/run | cut -d " " -f 2 | tr -d "\n"
pwn.college{QfQ1A0Xv2jiB6-ebsrEcI4vYNND.01NxEzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `cut -d " " -f n` is perfect to extract the nth space-separated column from each line. where `-f n` is the column to be deleted and `" "` is the column delimeter.

## References 
The materials provided by my mentor.
<br/>

# Sorting data
The challenge demanded that I sort a file of many fake flags so the real flag appears where we designed it to be when ordered alphabetically.
## My solve
**Flag:** `pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5kjNzEzW}`
<br/>
The flags were kept in such a way that alphabetically, the real flag would come last, so I ran `sort -r /challenge/flags.txt` to reverse-sort all candidate flags. 
Therefore, the first line of the reversed sorted output was the real flag.
<br/>
TERMINAL WORKING : 
```
hacker@data~sorting-data:~$ sort -r /challenge/flags.txt
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5kjNzEzW}
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5kjNyEzW}
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5jjNzEzW}
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5jjNzDzW}
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSN5kjNzEzW}
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtE.0FM0MDNxvSO5kjMzEzW}
pwn.college{UmuMBOkkyJ3TQnCvUtZ1aMdShtD.0EM0MDOxwSO5kiNzEzW}
pwn.college{UmuMBOkkyJ3SQnCuUtZ0aMdShtD.0EM0MDNxwSO5kjNzEzW}
pwn.college{UmuMBOkkyJ2TQnCvTtZ1aMdSgtE.0EM0MDOxwSO4kjNzEzV}
pwn.college{UmuMBOkkyJ2TQnCuUtZ0aMdShtE.0FM0MDOxwSO5kjNzEzW}
pwn.college{UmuMBOkkyJ2TQnBvUtZ1aMdShtD.0FM0MCOxwSO5kiNzEzW}
pwn.college{UmuMBOkkxI3TQnCvUtZ1aLdShtE.0FM0MDOxvSO5kjNzEzW}
pwn.college{UmuMBOkjyJ3TQmCvUtZ1aMdShsE.0FM0LDOxvSO5kjNzDzW}
pwn.college{UmuMBOjkyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5kjNzEzW}
pwn.college{UmuMBNkkyJ2TQnCvUtZ1aMdShtE.0FM0MDOxwRO4jjNzEzW}
pwn.college{UmuMBNkkyI3SQnCvUtZ1aLdShtE.0FM0MDOxwSO4kjNyEzW}
pwn.college{UmuLBOkjyJ3TQnCvUtZ1aMdShtE.0FM0MDOxwSO5kjNzEzW}
pwn.college{UmtMBOjkyJ3TQnCvUtZ1aLcRhtE.0FL0LDOxwSO5kiNzEzW}
pwn.college{UluMBOkkyJ3TQnCvUtZ0aMdShtE.0FM0MDOxvSO5kjNzEzW}
pwn.college{TltMAOjjxI2TPnCuUtZ1aMdShtE.0FL0LDNwvSN5jiNzEzW}
pwn.collegd{TmuLBOkkyJ3TPmCvTsZ1aMdShsE.0FM0MDOxwSO5kjNyEyV}
pwn.collefe{UmuMBOkjyJ2TQnCvUtZ1aMdShtE.0FM0MDOxwSO5kjNzEzW}
pwn.collefe{UluMBNjkyJ3TQnCvTsZ1aLdShtE.0FM0MDOxwSO5kjNzEzW}
pwn.colldge{UmuMBOkkyI3SPnCvUtZ1aMdShtE.0FL0MDOxwSO5kjNzDzW}
pwn.colldge{UmtLBOkkyI3SPnBuUtZ1aMdSgtD.0EM0LDOwwRO4kjNzEzW}
pwn.colldfe{UmuLBOjkxI2TQmBvTsY0aLdShtD.0FM0MDOwvSN5kjNyDyW}
pwn.colkefe{UmuMBOkkyJ3TPmCvUtZ1aLdSgtE.0FM0MDOxwSO5kjNzEzW}
pwn.colkdge{UmuLBOjjxI3SQmCvUtZ1aMcRhsD.0FM0MDOxwSO5kjMzEzV}
pwn.colkdge{UluLBOjkyJ3TQnCvUtZ0aMdSgtD.0FL0MDNwwSO5kiNzEzW}
pwn.coklege{UmuMBOkkyI3TQnBvUtZ1aLdSgsE.0EL0MDOwwSN5kjNzEzV}
pwn.cokkefe{UmuMBOkkyJ2TQmBvUsZ0aLdShtE.0FL0MDOxwRO5kiMzEyW}
pwn.cokkefe{UmtMBOjjyJ2TQnCvUtY1aLdSgtE.0EM0MDOxwSN4kiNyEzW}
pwn.cnlldge{UluLANkkxJ3SQnCuTsZ1aLcShsE.0FM0MDNxwSO4jjNyDzW}
pwn.cnlldge{TmtMBOjkyJ2TQmCvUtZ1aLdShtE.0FM0MDOxwRO5kjNzEzW}
pwn.bollege{UmtMBNjkyJ3TPmBvUsY0aMcRhtD.0EM0MDOwwRO5kjNzDyW}
pwn.bollege{UluMBOkkxI3TQnCvUtZ1aMdShsE.0FM0MDOxwRO5kjMzEzW}
pwn.bollege{TmuMBOkkyJ3TQmCvUsZ1aMcSgsD.0FM0LDOxwRO5kjNzEyW}
pwn.bollegd{UltLBNkkxJ3TQmBvUtZ1aMdShtD.0FM0MDOxwRO5kjNzEzW}
pwn.boklegd{UluMBOjkyJ3SQmCvUtZ1aMdShsE.0FM0MCOxwSO5jiNzEzV}
pwn.bnllege{UmuMBOkkxJ3TQnCvTsY1aMcShtE.0FM0MDOxwSN5jjMzEzV}
pwn.bnllege{UluMBNjjyJ3TPnBvTtZ1aMdRgtD.0FM0MDOxvRO5jiNyEyV}
pwn.bnllegd{UmuLBOjkxI2TQmCvTtY1aMdRhsE.0EL0MDOxwRO5kiMyEzV}
pwn.bnklege{UluLBOjkyJ2SQnCvUsZ1aMcSgsD.0FM0LDOwwRO5kiNzEzW}
pwm.college{UmuMBOjkyJ3TPnCuUsZ0aMdRgsE.0FM0MDOxvSO5kjNzEzW}
pwm.college{UmuMBOjjyJ3TQnCvTtZ1aMcSgsE.0FM0MDOxwRO4kjNzDzV}
pwm.college{UmtLANjkyJ3TQnCuUtZ0aMdSgtE.0FL0MCOxvSO5kiNzEzV}
pwm.college{UluLBNkjyJ3SQmCuUtZ1aLdRhtD.0EM0MCOxwSN4jiNyEzV}
pwm.colkefd{UluLBOkkyJ3TPnCuTtZ1aMdShtE.0FM0LDOxvRN5kjNzEzV}
pwm.coklege{UmtMBOkkyJ3TPnBvUtZ1aLcShsE.0FM0MDNxwRO5kiNyEzW}
pwm.cokldge{TmtMBOkkyI3SQmCvUtY1aMdRhtE.0FM0MDOxwRO4kjNzEyW}
pwm.cokldfd{UmtMBNkkyJ3TPnBvTsY1aLcSgtE.0FM0MDNwwRO5kjNzEyW}
pwm.cnllege{UmuMBOjkyJ3TPnCuTtZ1aLdShtD.0EM0MCOwwSN5kjNzEyW}
pwm.cnllege{UmuMBNjjyJ3TQnCuUsZ0aMdShtE.0FM0MCOxvSO5jiNzEzW}
pwm.cnllege{UltMANkkyJ3TPnCvUtZ1aMcShtE.0FM0MDOxwSO5kjNzEyW}
pwm.cnllege{TmuMBNkkxJ2SQmCvTtZ0aMdShtD.0EM0MDOxwRN5kiNyEzV}
pwm.cnllegd{TmuLBNkjxJ2SQnBuUtY0aMcShtE.0FM0MDNxwSO5kjNyDzW}
pwm.cnllefe{UmuMAOjjyI3TQmBuUtZ1aMdRhtE.0FL0MDNxwSN4kjMyEzV}
pwm.cnlldfd{UmuMANkkyI3TQmCvUsZ1aLdShsD.0FL0MDOwvSO4kiNzEyW}
pwm.cnklege{TmuMAOjkyJ3TQnCuUtZ0aMdRhsD.0FL0MDNxvSO4kjNzDyW}
pwm.cnkldfe{UmuMBOkjxJ3SQmBvUsZ1aMcSgtE.0FL0MDOxvRN4kjNzEyW}
pwm.bollege{UmuMBOkkyI3TQnCvTtZ1aLdShtE.0FL0MDOxwSO5jjNzEzW}
pwm.bollegd{TluMBOkkyJ3TQnBvUsZ0aLdRgtE.0FM0MCOxvSO5kjMzDyW}
pwm.bolkege{TmtMBNkkxJ3TPnCvUtY1aMdShtE.0EM0LDNxvSO4jjNyEzW}
pwm.bokkegd{UmtMBOkjyI3SPnBuUtY1aLdShsD.0FM0MDNxwSN5jiNzEzV}
pwm.bnlkegd{UmtMBOkkxJ3TQnCvUsZ1aLdShtE.0FM0LCNwwRO5jjMzDzW}
pwm.bnlkdfe{TluMBNkkyI2SQnCvUtZ1aMdShtE.0EM0MDOwwSO5kjMzDyV}
pvn.collegd{UmtMAOkkxI3TPnCuUtZ1aMdShsE.0EM0MDOxvRO5kjMyDyV}
pvn.collefe{TmuLAOkjyI2TQmCvTtZ0aLdSgtD.0EM0LCOxwSN5jiNzEyV}
pvn.colldge{UmtMANjjxJ3TPnCvUsY1aMcRgtE.0FM0LDOwwRO5kjNzDzW}
pvn.colkege{UmtLBOkjyJ2TQnBvTtZ0aMcRhtE.0FM0MDOxvSO4jiNzEyW}
pvn.colkegd{TmuLBOkkyI3SQnCvUtY1aMdSgtE.0EL0MCOxvSN4kjMzEzW}
pvn.colkdge{UmtMBOkjyJ3TQmCvUtY1aMdRgtE.0FM0MDNxwRO5jjNzDyW}
pvn.cokkegd{TltMBOkjyJ2SQnBvUsZ0aMdShsE.0EL0LCOxwSO5kiMyDzW}
pvn.cnlkefe{UltMBOjkyJ3SQmCvUtY1aLdRhtE.0FM0LDNxwSO4jiNzDyW}
pvn.cnklege{UmuMBOjjxI2TPnCvUsZ0aMdSgtD.0FM0MCNxwSN4jjMzEyW}
pvn.bolkdge{UmtMBNkkxI3TPnCvUsY1aLcRhsD.0FL0LDOxwSN5kiNyEzW}
pvn.boklefe{UluMAOkkyI3TPmBuUtZ0aMcSgsD.0FM0MDNxwSO5jjNzEyV}
pvn.bokldfe{TluMANkkyI3SQnCvUtZ0aMdShtE.0EL0LDNwwRN5kiMzEyW}
pvm.college{UmtMBOjkyJ2TPnCvUtZ1aMcRhtE.0FL0MDNwvRO4kjNyEyW}
pvm.colldgd{TmuMBOjjyJ2SQnBvTtZ1aMdSgtE.0FM0LDNwwSO5kjMzEzW}
pvm.cnkkegd{UmtLAOkkyJ3TQmCvTtZ0aMcRhtE.0EM0MCOxwSO5kiNzDzW}
pvm.bolldgd{TmtLBOjkxJ2SPmCuUtZ1aMcShtE.0EM0LDOxvSO4jjMzEzW}
own.colkegd{UmuMBOkjyJ2TQmCvUtZ0aMdShsD.0EM0MDOxwSO5kjMzEzW}
own.cnllege{UmtMBOkkyJ3TQnBvUtZ1aMdRhtE.0FM0LDOxwSO5kiMzEzV}
own.cnllefe{TluLBOkkyJ2TQnCvUtZ1aMdShtE.0FL0MCNwwSO5kiMzEzW}
own.cnklege{UmuMBOkkyJ3TQmCuUsZ0aMdShtE.0FM0MDOxvRO4kjNyEyV}
own.bolldgd{TmuMBOjkyJ2SQnCvTtZ0aLcShtE.0FM0MDOwwSN5jiMzDyW}
own.bolkege{TluMBOkkyI2TQmCvTsY0aLdSgtE.0EM0MCOxwRN4kjNzDzV}
own.bokldge{TluMBNkkxI3SPmCuUtZ1aMcRgtE.0FL0MDNxvSO5jjNzDzW}
owm.collegd{TmtMBOjkyJ3TQnBvUtY1aMcSgtD.0EM0LDOxwSO5kiNzDyV}
owm.coklegd{UmtMBNkkyI3SQnCvTtZ0aLdShtD.0EM0LDOwwSN5kiMzDzW}
owm.bolkege{UluMBOkjyJ3SPnCvTtZ1aMdRhtE.0EL0LDNxwRO5jjNzEzW}
ovn.collefe{UmuMAOkkxI3TQnBvUtZ0aMdRgsE.0FL0MDNxvSN4kiNyEyW}
ovn.coklege{UmuMAOjjxI3TQmBvUsY0aMdRhtE.0EL0LDOxvSN5kjMyEzW}
ovn.coklegd{UmtLAOkkyJ3TQnBvUsZ1aMdShtE.0FM0MCOxvSO5kiNzDzW}
ovm.college{UmuMBOkkyI3TQnBvUtZ1aMdShsE.0FM0MCNwvRO4kjNzEzV}
ovm.college{UmuMBOkkxJ3TQmCvUtZ1aMdShtE.0FM0MDOxvSO5kjNzEzW}
ovm.college{UmtLBOkjyI2TQnBuTtZ1aMcShsE.0FL0LDOxwSO4kjMzEyV}
ovm.coklefe{UmuMAOkjyI3TQnCvUsY1aLcShsD.0FM0LDOxwSO5kjMzEzW}
ovm.cokkdge{UmuMANkkyJ3TQmCuTsZ0aMcRhtE.0FM0LCNxvSN5jjNzEzV}
ovm.cnllegd{UmtMBNjjxI2SQmCvUsZ1aLdRhsE.0FM0LDOxvSO5kjNzEzW}

```

## What I learned
I learned the following from this challenge : 
1. `sort` orders lines alphabetically by default.
2. `-r` as an argument to `sort` reverses that order.

## References 
The materials provided by my mentor.
<br/>
