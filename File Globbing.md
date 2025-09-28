# Mathching with *
The challenge required changing directory to `/challenge` using a globbed path no longer than four characters.

## My solve
**Flag:** `pwn.college{oC6AAYZgX06mfyUkJ02ycmUuDjj.QXxIDO0wSO5kjNzEzW}`
I used globbing with `*` to shorten `/challenge` into just `/ch*`, keeping it within 4 characters, and then ran `/challenge/run`.
</br>
TERMINAL WORKING : 
```
hacker@globbing~matching-with-:~$ cd /cha*
You specified the path to 'cd' to in more than 4 characters. Disallowed!
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /ch*
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{oC6AAYZgX06mfyUkJ02ycmUuDjj.QXxIDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `*` expands to match any sequence of characters in filenames or paths.
2. It can shorten commands by substituting long paths with fewer characters.

## References 
pwn.college
<br/>


# Mathching with ?
The challenge required changing directory to `/challenge` while replacing the letters `c` and `l` with single-character wildcards.

## My solve
**Flag:** `pwn.college{UJak5xFZ1t1bT2jx2Spo7hLOJur.QXyIDO0wSO5kjNzEzW}`
I replaced the `c` and `l` in `/challenge` with `?`, typing `/ ?ha??enge``, which resolved to /challenge.
</br>
TERMINAL WORKING : 
```
This challenge resets your working directory to /home/hacker unless you change
directory properly...
This challenge resets your working directory to /home/hacker unless you change
directory properly...
hacker@globbing~matching-with-:~$ cd /?ha??enge
hacker@globbing~matching-with-:/challenge$ /challenge/run
You ran me with the working directory of /challenge! Here is your flag:
pwn.college{UJak5xFZ1t1bT2jx2Spo7hLOJur.QXyIDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `?` matches exactly one character, unlike `*` which matches many.
2. Combining multiple `?` makes it possible to replace multiple letters.
## References 
pwn.college
<br/>

# Mathching with []
The challenge required running `/challenge/run` with a single argument that bracket-globs into `file_b, file_a, file_s, and file_h`.

## My solve
**Flag:** `pwn.college{sZGeeuRlPZqxRhTsClFObZeVXeH.QXzIDO0wSO5kjNzEzW}`
I used file_[bash] to match the specified files inside /challenge/files.
</br>
TERMINAL WORKING : 
```
hacker@globbing~matching-with-:~$ cd /challenge/files
hacker@globbing~matching-with-:/challenge/files$ /challenge/run file_[bash]
You got it! Here is your flag!
pwn.college{sZGeeuRlPZqxRhTsClFObZeVXeH.QXzIDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `[]` matches one character from the listed set, letting you target specific names.
  

## References 
pwn.college
<br/>

# Mathching path with []
The challenge required passing absolute paths (from /) that bracket-glob into `file_b, file_a, file_s, and file_h`.

## My solve
**Flag:** `pwn.college{goS2kJg1S-kmqVMX5yNgP8Rn-0E.QX0IDO0wSO5kjNzEzW}`
I ran /challenge/run /challenge/files/file_[bash] just like it is done to find files, to expand the absolute path.
</br>
TERMINAL WORKING : 
```
hacker@globbing~matching-paths-with-:~$ /challenge/run /challenge/files/file_[bash]
You got it! Here is your flag!
pwn.college{goS2kJg1S-kmqVMX5yNgP8Rn-0E.QX0IDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Globbing works on full paths as well as filenames.
  

## References 
pwn.college
<br/>

# Multiple globs
The challenge required running `/challenge/run` with a single short (≤3 chars) globbed word containing two `*` globs that matches every filename containing the letter p.

## My solve
**Flag:** `pwn.college{ILBoZTxbne5WmKeyWzCHB7iNl_Y.0lM3kjNxwSO5kjNzEzW}`
The challenge required running /challenge/run with a single short (≤3 chars) globbed word containing two * globs that matches every filename containing the letter p.
</br>
TERMINAL WORKING : 
```
hacker@globbing~multiple-globs:~$ cd /challenge/files
hacker@globbing~multiple-globs:/challenge/files$ /challenge/run /*p*
Error: your argument is too long! It must be 3 characters or less.
hacker@globbing~multiple-globs:/challenge/files$  /challenge/run *p*
You got it! Here is your flag!
pwn.college{ILBoZTxbne5WmKeyWzCHB7iNl_Y.0lM3kjNxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Multiple `*` can be used inside a single word to match patterns before and after a substring.
  

## References 
pwn.college
<br/>

# Mixing globs
The challenge required a single short (≤6 chars) glob that matches the files `challenging`, `educational`, and `pwning`.

## My solve
**Flag:** `pwn.college{0d4jq3tx0rNcZfk1oqUXG3WQlig.QX1IDO0wSO5kjNzEzW}`
Initially, I struggled to find a common unique way of globbing all the mentioned files without covering others, then i realised, they all started with unique letters, so i kept the substring at the start like so, `[cep]*`.
</br>
TERMINAL WORKING : 
```
hacker@globbing~mixing-globs:~$ cd /challenge/files
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *[eaw]*
Error: your argument is too long! It must be 6 characters or less.
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *[aw]*
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
amazing beautiful challenging educational fantastic great happy jovial laughing magical pwning radiant wonderful xenial
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *[cw]*
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
challenging educational fantastic incredible magical nice optimistic pwning victorious wonderful
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run *[hw]*
Your expansion did not expand to the requested files (challenging, educational,
pwning). Instead, it expanded to:
challenging delightful happy laughing pwning thrilling wonderful youthful
hacker@globbing~mixing-globs:/challenge/files$ /challenge/run [cep]*
You got it! Here is your flag!
pwn.college{0d4jq3tx0rNcZfk1oqUXG3WQlig.QX1IDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Bracket expressions can select starting letters to target multiple specific filenames.
  

## References 
pwn.college
<br/>

# Exclusionary globbing 
The challenge required a glob that matches all files that do not start with `p`, `w`, or `n` using `!`.

## My solve
**Flag:** `pwn.college{cHEXUk3JsYcq9L6QUUXjNWKJ6Vt.QX2IDO0wSO5kjNzEzW}`
I used [!pwn]* to exclude filenames beginning with p, w, or n.
</br>
TERMINAL WORKING : 
```
hacker@globbing~exclusionary-globbing:~$ cd /challenge/files
hacker@globbing~exclusionary-globbing:/challenge/files$ /challenge/run [!pwn]*
You got it! Here is your flag!
pwn.college{cHEXUk3JsYcq9L6QUUXjNWKJ6Vt.QX2IDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Starting `[]` with `!` inverts the character set to exclude matches.
  

## References 
pwn.college
<br/>

# Tab completion 
The challenge required revealing a specially crafted filename inside `/challenge` that can only be read by using tab completion to expand its tricky name.

## My solve
**Flag:** `pwn.college{gZIsb8ExhO8SYghdxXRvTXsMw_O.0FN0EzNxwSO5kjNzEzW}`
I used tab completion on /challenge/pwn<TAB> to expand the filename, then cat.
</br>
TERMINAL WORKING : 
```
hacker@globbing~tab-completion:~$ cat /challenge/pwncollege​
pwn.college{gZIsb8ExhO8SYghdxXRvTXsMw_O.0FN0EzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Tab completion expands otherwise hard-to-type filenames.
2. It’s a safer alternative to wildcards when an exact filename is needed.
  

## References 
pwn.college
<br/>

# Tab completion on command
The challenge required using tab completion to auto-complete and execute a hidden command that begins with pwncollege.

## My solve
**Flag:** `pwn.college{gZIsb8ExhO8SYghdxXRvTXsMw_O.0FN0EzNxwSO5kjNzEzW}`
I typed the command prefix pwncollege and used tab completion to expand and execute the hidden command.
</br>
TERMINAL WORKING : 
```
//insert
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Tab completion works for commands as well as filenames
  

## References 
pwn.college
<br/>

# Auto completing tabs 
The challenge required using tab completion to expand and execute a hidden command beginning with pwncollege.

## My solve
**Flag:** `pwn.college{Aapg-8PC1e1RHrlt1oj4kQWQmn2.0VN0EzNxwSO5kjNzEzW}`
I typed pwncollege and pressed TAB to auto-complete the hidden command (pwncollege-5155). Running it returned the flag.
</br>
TERMINAL WORKING : 
```
hacker@globbing~tab-completion-on-commands:~$ pwncollege-5155
Correct! Here is your flag:
pwn.college{Aapg-8PC1e1RHrlt1oj4kQWQmn2.0VN0EzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Tab completion helps discover hidden or unusual commands quickly.
  

## References 
pwn.college
<br/>
