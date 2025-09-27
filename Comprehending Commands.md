# Cat not the pet but the command 
The challenge demanded to read the file named `flag` using the `cat` command.

## My solve
**Flag:** `pwn.college{0qFpKvnrkqWnsO7XEiMkIGUst0j.QX4cTO0wSO5kjNzEzW}`
After logging in, I used `cat flag` to display the file contents.
TERMINAL WORKING : 
```
hacker@commands~cat-not-the-pet-but-the-command:~$ cat flag
pwn.college{0T3mKpmd6T2EEh-wKsle-wxsYkw.QXxcTN0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `cat` prints file contents to the terminal. 
2. You can concatenate multiple files by passing several filenames to `cat`.

## References 
The materials provided by my mentor.
<br/>

# Catting absolute paths
The challenge demanded to read a flag file by giving its absolute path to `cat`.

## My solve
**Flag:** `pwn.college{g4Oco2wJyj_YCFfP4wPC7sYB-5G.QX5ETO0wSO5kjNzEzW}`
I provided the absolute path `/flag` to `cat` to read the file.  
TERMINAL WORKING : 
```
hacker@commands~catting-absolute-paths:~$ cat /flag
pwn.college{g4Oco2wJyj_YCFfP4wPC7sYB-5G.QX5ETO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Absolute paths (starting with `/`) point to exact locations in the filesystem.
2. `cat /path/to/file` works regardless of the current directory.
3. 

## References 
The materials provided by my mentor.
<br/>

# More catting practise 
The challenge required retrieving a flag using an absolute path, without changing directories

## My solve
**Flag:** `pwn.college{M8M7w3ZG4GmKJttcY00keND8cU2.QXwITO0wSO5kjNzEzW}`
The flag was in /opt/kropr/flag, and I accessed it directly using `cat /opt/kropr/flag`.
TERMINAL WORKING : 
```
You cannot use the 'cd' command in this level, and must retrieve the flag by
absolute path. Plus, I hid the flag in a different directory! You can find it
in the file /opt/kropr/flag. Go cat it out **without** cding into that
directory!
hacker@commands~more-catting-practice:~$ cat /opt/kropr/flag
pwn.college{M8M7w3ZG4GmKJttcY00keND8cU2.QXwITO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. How to locate files in unusual directories.
2. That cd is not always allowed, so direct absolute paths are key.

## References 
The materials provided by my mentor.
<br/>

# Grepping for a needle in a haysack
The challenge required finding a flag hidden within a large file using `grep` command.

## My solve
**Flag:** `pwn.college{M8M7w3ZG4GmKJttcY00keND8cU2.QXwITO0wSO5kjNzEzW}`
I used grep command with the arguments of the string to be found (pwn.college-as each flag starts with it) and the address provided to search the file for the pattern and extract the flag.
TERMINAL WORKING : 
```
hacker@commands~grepping-for-a-needle-in-a-haystack:~$ grep pwn.college /challenge/data.txt
pwn.college{sq0YsTFhUsFN6iillw7a0Wo-5AC.QX3EDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. grep is used for searching patterns(key strings) inside files.
2. Providing a keyword like pwn.college quickly filters the relevant line.
3. grep is extremely useful in large files where manually searching is impractical.

## References 
The materials provided by my mentor.
<br/>

# Comparing files
The challenge required identifying differences between two files to find the real flag.

## My solve
**Flag:** `pwn.college{A88PZDE20mHMcp4o3Q-QE3nhNHS.01MwMDOxwSO5kjNzEzW}`
I used `diff` command to compare files that were provided. The line unique to the first file revealed the flag.
TERMINAL WORKING : 
```
hacker@commands~comparing-files:~$ diff /challenge/decoys_and_real.txt /challenge/decoys_only.txt40d39
< pwn.college{A88PZDE20mHMcp4o3Q-QE3nhNHS.01MwMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. diff highlights the differences between two files.
2. It is a fast way to check for hidden or unique lines.
3. File comparison can uncover hidden content in CTF challenges.

## References 
The materials provided by my mentor.
<br/>
# Listing files 
The challenge tested listing directory contents to discover a renamed executable containing the flag.

## My solve
**Flag:** `{EYyAioENiW_U_nFbhIlxlTG7dwh.QX4IDO0wSO5kjNzEzW}`
I used `ls` first to list all the files in /challenge directory, then identified a renamed executable and then ran it.
TERMINAL WORKING : 
```
hacker@commands~listing-files:~$ ls /challenge
9025-renamed-run-1448  DESCRIPTION.md
hacker@commands~listing-files:~$ /challenge/9025-renamed-run-1448
Yahaha, you found me! Here is your flag:
pwn.college{EYyAioENiW_U_nFbhIlxlTG7dwh.QX4IDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. ls lists files and directories.
2. Sometimes the flag is hidden inside executables instead of text files.

## References 
The materials provided by my mentor.
<br/>

# Touching files
The challenge required creating specific files in /tmp to unlock the flag.

## My solve
**Flag:** `pwn.college{kx5_Njq7CcwMWo0VlWRF4qGEdPl.QXwMDO0wSO5kjNzEzW}`
I first created two files using `touch` command in the /tmp directory and then executed /challenge/run.
TERMINAL WORKING : 
```
hacker@commands~touching-files:~$ touch /tmp/pwn /tmp/college
hacker@commands~touching-files:~$ /challenge/run
Success! Here is your flag:
pwn.college{kx5_Njq7CcwMWo0VlWRF4qGEdPl.QXwMDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. touch creates empty files if they don’t exist.

## References 
The materials provided by my mentor.
<br/>

# Removing files  //FLAG DINT GET COPIED REDO AND INSERT FLAG
The challenge tested file deletion with `rm`.

## My solve
**Flag:** `pwn.college{kx5_Njq7CcwMWo0VlWRF4qGEdPl.QXwMDO0wSO5kjNzEzW}`
I created a file called `delete_me` using the touch command and the removed it using `rm`.
TERMINAL WORKING : 
```
Removing files 
hacker@commands~removing-files:~$ touch delete_me
hacker@commands~removing-files:~$ rm delete_me
hacker@commands~removing-files:~$ /challenge/check
Excellent removal. Here is your reward:

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1.rm permanently deletes files (no trash bin).

## References 
The materials provided by my mentor.
<br/>

# Moving files  
The challenge required moving a file to a specific location.

## My solve
**Flag:** `pwn.college{8GQ05C4xsxWaOX50a3J_01fb5FZ.0VOxEzNxwSO5kjNzEzW}`
I moved the flag using `mv` command to the directory given. Then ran `/challenge/run` to verify
TERMINAL WORKING : 
```
hacker@commands~moving-files:~$ mv /flag /tmp/hack-the-planet
Correct! Performing 'mv /flag /tmp/hack-the-planet'.
hacker@commands~moving-files:~$ /challenge/check
Congrats! You successfully moved the flag to /tmp/hack-the-planet! Here it is:
pwn.college{8GQ05C4xsxWaOX50a3J_01fb5FZ.0VOxEzNxwSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1.mv moves files from one location to another.

## References 
The materials provided by my mentor.
<br/>
# Hidden files
The challenge tested identifying hidden files(which are files starting with .).

## My solve
**Flag:** `pwn.college{4hTvLxno-wWczb3g246tUTkrl3v.QXwUDO0wSO5kjNzEzW}`
I used ls -a to reveal hidden files in /. I found .flag-2367339979884.Initially i got confused on how to read it and tried the cd command, but then I realised that it was a file, which needed to be read with cat to extract the flag.
TERMINAL WORKING : 
```
hacker@commands~hidden-files:~$ cd /
hacker@commands~hidden-files:/$ ls -a
.                    challenge  lib64   proc  tmp
..                   dev        libx32  root  usr
.dockerenv           etc        media   run   var
.flag-2367339979884  home       mnt     sbin
bin                  lib        nix     srv
boot                 lib32      opt     sys
hacker@commands~hidden-files:/$ cd .flag-2367339979884
bash: cd: .flag-2367339979884: Not a directory
hacker@commands~hidden-files:/$ cat .flag-2367339979884
pwn.college{4hTvLxno-wWczb3g246tUTkrl3v.QXwUDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. Files starting with . are hidden by default.
2. The `-a` argument in `ls` shows hidden files.


## References 
The materials provided by my mentor.
<br/>
#An epic file system quest 
#making directories 
