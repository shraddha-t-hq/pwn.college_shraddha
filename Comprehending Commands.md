# cat: not the pet, but the command! 
The challenge demanded to read the file named `flag` using the `cat` command.

## My solve
**Flag:** `pwn.college{0qFpKvnrkqWnsO7XEiMkIGUst0j.QX4cTO0wSO5kjNzEzW}`
After logging in, I used `cat flag` to display the file contents.
</br>
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

# catting absolute paths
The challenge demanded to read a flag file by giving its absolute path to `cat`.

## My solve
**Flag:** `pwn.college{g4Oco2wJyj_YCFfP4wPC7sYB-5G.QX5ETO0wSO5kjNzEzW}`
I provided the absolute path `/flag` to `cat` to read the file.  
</br>
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


## References 
The materials provided by my mentor.
<br/>

# More catting practise 
The challenge required retrieving a flag using an absolute path, without changing directories

## My solve
**Flag:** `pwn.college{M8M7w3ZG4GmKJttcY00keND8cU2.QXwITO0wSO5kjNzEzW}`
The flag was in `/opt/kropr/flag`, and I accessed it directly using `cat /opt/kropr/flag`.
</br>
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

# Grepping for a needle in a haystack
The challenge required finding a flag hidden within a large file using `grep` command.

## My solve
**Flag:** `pwn.college{M8M7w3ZG4GmKJttcY00keND8cU2.QXwITO0wSO5kjNzEzW}`
I used grep command with the arguments of the string to be found (pwn.college-as each flag starts with it) and the address provided to search the file for the pattern and extract the flag.
</br>
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
</br>
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
</br>
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
The challenge required creating specific files in `/tmp` to unlock the flag.

## My solve
**Flag:** `pwn.college{kx5_Njq7CcwMWo0VlWRF4qGEdPl.QXwMDO0wSO5kjNzEzW}`
I first created two files using `touch` command in the /tmp directory and then executed /challenge/run.
</br>
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
1. `touch` creates empty files if they don’t exist.

## References 
The materials provided by my mentor.
<br/>

# Removing files  //FLAG DINT GET COPIED REDO AND INSERT FLAG
The challenge tested file deletion with `rm`.

## My solve
**Flag:** `pwn.college{kx5_Njq7CcwMWo0VlWRF4qGEdPl.QXwMDO0wSO5kjNzEzW}`
I created a file called `delete_me` using the touch command and the removed it using `rm`.
</br>
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
</br>
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
1. `mv` moves files from one location to another.

## References 
The materials provided by my mentor.
<br/>
# Hidden files
The challenge tested identifying hidden files(which are files starting with `.`).

## My solve
**Flag:** `pwn.college{4hTvLxno-wWczb3g246tUTkrl3v.QXwUDO0wSO5kjNzEzW}`
I used ls -a to reveal hidden files in /. I found .flag-2367339979884.Initially I got confused on how to read it and tried the cd command, but then I realised that it was a file, which needed to be read with cat to extract the flag.
</br>
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

# An Epic File System quest
The challenge required to follow a chain of filesystem “breadcrumbs” (using `ls`, `cd`, `cat`, etc.) — obey the special hints (delayed / trapped / hidden) to reach the final file that contains the flag.
## My solve
**Flag:** `pwn.college{oaXROjW_S9XEwCmZAUI-eQqlYSo.QX5IDO0wSO5kjNzEzW}`
The challenge required me to use several commands and keen observations to find the flag.
</br>
TERMINAL WORKING : 
```
hacker@commands~an-epic-filesystem-quest:~$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls
CUE  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin  challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$ cat CUE
Yahaha, you found me!
The next clue is in: /usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__$ ls -a
.  ..  BRIEF  __init__.cpython-38.pyc  interfaces.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__$ cat BRIEF
Lucky listing!
The next clue is in: /usr/share/perl/5.30.0/JSON/PP

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__$ CD /usr/share/perl/5.30.0/JSON/PP
bash: CD: command not found
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__$ cd /usr/share/perl/5.30.0/JSON/PP
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/JSON/PP$ ls
ALERT  Boolean.pm
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/JSON/PP$ cat ALERT
Congratulations, you found the clue!
The next clue is in: /opt/busybox/busybox-1.33.2/util-linux/volume_id

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/perl/5.30.0/JSON/PP$ cd /
hacker@commands~an-epic-filesystem-quest:/$ ls /opt/busybox/busybox-1.33.2/util-linux/volume_id
Config.in       cramfs.c  fat.c          lfs.c         minix.o     romfs.o             unused_hpfs.c          unused_via_raid.c
Config.src      cramfs.o  fat.o          lfs.o         nilfs.c     squashfs.c          unused_isw_raid.c      util.c
Kbuild          erofs.c   get_devname.c  lib.a         nilfs.o     squashfs.o          unused_lsi_raid.c      util.o
Kbuild.src      erofs.o   get_devname.o  linux_raid.c  ntfs.c      sysv.c              unused_lvm.c           volume_id.c
NUGGET-TRAPPED  exfat.c   hfs.c          linux_raid.o  ntfs.o      sysv.o              unused_mac.c           volume_id.o
bcache.c        exfat.o   hfs.o          linux_swap.c  ocfs2.c     ubifs.c             unused_msdos.c         volume_id_internal.h
bcache.o        ext.c     iso9660.c      linux_swap.o  ocfs2.o     ubifs.o             unused_nvidia_raid.c   xfs.c
btrfs.c         ext.o     iso9660.o      luks.c        reiserfs.c  udf.c               unused_promise_raid.c  xfs.o
btrfs.o         f2fs.c    jfs.c          luks.o        reiserfs.o  udf.o               unused_silicon_raid.c
built-in.o      f2fs.o    jfs.o          minix.c       romfs.c     unused_highpoint.c  unused_ufs.c
hacker@commands~an-epic-filesystem-quest:/$ /opt/busybox/busybox-1.33.2/util-linux/volume_id cat NUGGET-TRAPPED
bash: /opt/busybox/busybox-1.33.2/util-linux/volume_id: Is a directory
hacker@commands~an-epic-filesystem-quest:/$ ls
CUE  boot       dev  flag  lib    lib64   media  nix  proc  run   srv  tmp  var
bin  challenge  etc  home  lib32  libx32  mnt    opt  root  sbin  sys  usr
hacker@commands~an-epic-filesystem-quest:/$
hacker@commands~an-epic-filesystem-quest:/$ mv /opt/busybox/busybox-1.33.2/util-linux/volume_id /
mv: cannot move '/opt/busybox/busybox-1.33.2/util-linux/volume_id' to '/volume_id': Permission denied
hacker@commands~an-epic-filesystem-quest:/$ mv NUGGET-TRAPPED CUE
mv: cannot stat 'NUGGET-TRAPPED': No such file or directory
hacker@commands~an-epic-filesystem-quest:/$ mv /opt/busybox/busybox-1.33.2/util-linux/volume_id/NUGGET-TRAPPED /CUE
mv: replace '/CUE', overriding mode 0644 (rw-r--r--)?
hacker@commands~an-epic-filesystem-quest:/$ cat CUE
Yahaha, you found me!
The next clue is in: /usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ diff mv /opt/busybox/busybox-1.33.2/util-linux/volume_id/NUGGET-TRAPPED /CUE
diff: extra operand '/CUE'
diff: Try 'diff --help' for more information.
hacker@commands~an-epic-filesystem-quest:/$ diff /opt/busybox/busybox-1.33.2/util-linux/volume_id/NUGGET-TRAPPED /CUE
2c2,4
< The next clue is in: /usr/share/racket/pkgs/frtime/opt/compiled
---
> The next clue is in: /usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__
>
> The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /usr/share/racket/pkgs/frtime/opt/compiled
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/frtime/opt/compiled$ ls
TIP                      frtime-opt-lang_rkt.zo  frtime-opt_rkt.zo       lowered-equivs_rkt.zo
frtime-opt-lang_rkt.dep  frtime-opt_rkt.dep      lowered-equivs_rkt.dep
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/frtime/opt/compiled$ cat TIP
Congratulations, you found the clue!
The next clue is in: /usr/lib/x86_64-linux-gnu/gedit/plugins/externaltools

Watch out! The next clue is **trapped**. You'll need to read it out without 'cd'ing into the directory; otherwise, the clue will self destruct!
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/frtime/opt/compiled$ ls /usr/lib/x86_64-linux-gnu/gedit/plugins/externaltools
LEAD-TRAPPED  __pycache__        capture.py     functions.py  linkparsing.py  outputpanel.py
__init__.py   appactivatable.py  filelookup.py  library.py    manager.py      windowactivatable.py
hacker@commands~an-epic-filesystem-quest:/usr/share/racket/pkgs/frtime/opt/compiled$ cd /
hacker@commands~an-epic-filesystem-quest:/$ diff /usr/lib/x86_64-linux-gnu/gedit/plugins/externaltools/LEAD-TRAPPED /CUE
1,2c1,4
< Congratulations, you found the clue!
< The next clue is in: /opt/linux/linux-5.4/arch/openrisc/kernel
---
> Yahaha, you found me!
> The next clue is in: /usr/lib/python3/dist-packages/cryptography/hazmat/backends/__pycache__
>
> The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/$ cd /opt/linux/linux-5.4/arch/openrisc/kernel
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/openrisc/kernel$ ls
CLUE           dma.c    irq.c         process.c  setup.c   stacktrace.c      time.c      vmlinux.h
Makefile       entry.S  module.c      prom.c     signal.c  sync-timer.c      traps.c     vmlinux.lds.S
asm-offsets.c  head.S   or32_ksyms.c  ptrace.c   smp.c     sys_call_table.c  unwinder.c
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/openrisc/kernel$ cat CLUE
Congratulations, you found the clue!
The next clue is in: /usr/local/lib/python3.8/dist-packages/plumbum/cli/i18n/fr

The next clue is **hidden** --- its filename starts with a '.' character. You'll need to look for it using special options to 'ls'.
hacker@commands~an-epic-filesystem-quest:/opt/linux/linux-5.4/arch/openrisc/kernel$ cd /usr/local/lib/python3.8/dist-packages/plumbum
/cli/i18n/fr
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/plumbum/cli/i18n/fr$ ls -a
.  ..  .TRACE  LC_MESSAGES
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/plumbum/cli/i18n/fr$ cat .TRACE
Congratulations, you found the clue!
The next clue is in: /usr/lib/python3/dist-packages/sage/schemes/plane_conics/__pycache__

The next clue is **delayed** --- it will not become readable until you enter the directory with 'cd'.
hacker@commands~an-epic-filesystem-quest:/usr/local/lib/python3.8/dist-packages/plumbum/cli/i18n/fr$ cd /usr/lib/python3/dist-packages/sage/schemes/plane_conics/__pycache__
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/schemes/plane_conics/__pycache__$ la
bash: la: command not found
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/schemes/plane_conics/__pycache__$ ls
REVELATION               con_field.cpython-38.pyc         con_prime_finite_field.cpython-38.pyc       constructor.cpython-38.pyc
__init__.cpython-38.pyc  con_finite_field.cpython-38.pyc  con_rational_field.cpython-38.pyc
all.cpython-38.pyc       con_number_field.cpython-38.pyc  con_rational_function_field.cpython-38.pyc
hacker@commands~an-epic-filesystem-quest:/usr/lib/python3/dist-packages/sage/schemes/plane_conics/__pycache__$ cat REVELATION
CONGRATULATIONS! Your perserverence has paid off, and you have found the flag!
It is: pwn.college{oaXROjW_S9XEwCmZAUI-eQqlYSo.QX5IDO0wSO5kjNzEzW}


```
This generated the flag and the challenge was completed!

## What I learned
I learned the following from this challenge : 
1. Carefully following paths is verg important.
2. shell commands are case-sensitive — cd ≠ CD.
3. Attempting to `cat` a directory gives “Is a directory”.It is best to always ensure the target is a file. `ls` will clarify this.
4. `diff` is a very useful tool.

## References 
pwn.college
<br/>

# Making directories 
The challenge tested identifying hidden files(which are files starting with .).

## My solve
**Flag:** `pwn.college{cOahzAa4Kbc0j218Fv3eWhAMhIK.QXxMDO0wSO5kjNzEzW}`
I first entered into the /tmp directory, where i created another directory called `pwn` USING THE `mkdir` command.
</br>
TERMINAL WORKING : 
```
hacker@commands~making-directories:~$ cd /tmp
hacker@commands~making-directories:/tmp$ mkdir pwn
hacker@commands~making-directories:/tmp$ ls
bin  hsperfdata_root  pwn  tmp.TpSOPGOVKK
hacker@commands~making-directories:/tmp$ cd pwn
hacker@commands~making-directories:/tmp/pwn$ touch college
hacker@commands~making-directories:/tmp/pwn$ /challenge/run
Success! Here is your flag:
pwn.college{cOahzAa4Kbc0j218Fv3eWhAMhIK.QXxMDO0wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. mkdir <dir> creates a new directory.


## References 
pwn.college


# Linking files
The challenge demanded fooling a program that reads `/home/hacker/not-the-flag` into returning the real `/flag` contents by creating a symbolic link so the program opens the real flag instead of the decoy.

## My solve
**Flag:** `pwn.college{kpKkl0ez4eka52a0FT_IZGgCQzV.QX5ETN1wSO5kjNzEzW}`
I created a symbolic link named `/home/hacker/not-the-flag` that points to `/flag` using `ln -s <target> <link>`. This causes any process that opens `/home/hacker/not-the-flag` to actually read `/flag`.
</br>
TERMINAL WORKING : 
```
hacker@commands~linking-files:~$ ln -s /flag /home/hacker/not-the-flag
hacker@commands~linking-files:~$ /challenge/catflag
About to read out the /home/hacker/not-the-flag file!
pwn.college{kpKkl0ez4eka52a0FT_IZGgCQzV.QX5ETN1wSO5kjNzEzW}

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `ln -s <target> <linkname>` creates a symbolic link at `<linkname>` that refers to `<target>`, causing accesses to the link to resolve to the target file.


## References 
pwn.college
