# Listing Processes
The challenge required finding a hidden `/challenge/run` file by listing running processes.

## My solve
**Flag:** `pwn.college{oiUoM6HmfbfFb_2Hj-s4E1tv0N-.QX4MDO0wSO5kjNzEzW}`
<br/>
I used `ps -aux` to list all running processes and found the `/challenge/3839-run-14367` process.
</br>
TERMINAL WORKING : 
```
hacker@processes~listing-processes:~$ ps -aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  0.0   1056   640 ?        Ss   16:25   0:00 /sbin/docker-init -- /nix/var/nix/profiles/dojo-workspace/bin
root           7  0.0  0.0 231708  2560 ?        S    16:25   0:00 /run/dojo/bin/sleep 6h
root         132  0.0  0.0   4132  2560 ?        S    16:25   0:00 /challenge/3839-run-14367
root         135  0.0  0.0   2744  1600 ?        S    16:25   0:00 sleep 6h
hacker       137  0.0  0.0 231576  3520 pts/0    Ss   16:25   0:00 /nix/store/0nxvi9r5ymdlr2p24rjj9qzyms72zld1-bash-interactive-
hacker       143  0.0  0.0 231940  4160 pts/0    S    16:25   0:00 /run/dojo/bin/bash --login
hacker       153  0.0  0.0 233600  3840 pts/0    R+   16:25   0:00 ps -aux
hacker@processes~listing-processes:~$ /challenge/3839-run-14367
Yahaha, you found me! Here is your flag:
pwn.college{oiUoM6HmfbfFb_2Hj-s4E1tv0N-.QX4MDO0wSO5kjNzEzW}
Now I will sleep for a while (so that you could find me with 'ps').

```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `ps -aux` lists all processes, including those not associated with a terminal.
2. Process IDs (PID) help in identifying running programs when the file itself cannot be directly listed.

## References 
The materials provided by my mentor.
<br/>

# Killing Processes
The challenge required terminating a running process to allow `/challenge/run` to execute.
<br/>
## My solve
**Flag:** `pwn.college{AHfNzV5MXZqwulSz0Tl6zrXOmFx.QXyQDO0wSO5kjNzEzW}`
<br/>
I identified the `/challenge/dont_run` process using `ps -ef` to identify its PID and killed it with `kill 136`. Afterwards, I ran `/challenge/run` to retrieve the flag.
</br>
TERMINAL WORKING : 
```
hacker@processes~killing-processes:~$ ps -e | grep /challenge/dont_run
hacker@processes~killing-processes:~$ ps -e
    PID TTY          TIME CMD
      1 ?        00:00:00 docker-init
      7 ?        00:00:00 /run/dojo/bin/s
    135 ?        00:00:00 su
    136 ?        00:00:00 bash
    137 ?        00:00:00 sleep
    139 pts/0    00:00:00 ssh-entrypoint
    145 pts/0    00:00:00 bash
    170 pts/0    00:00:00 ps
hacker@processes~killing-processes:~$ ps -ef
UID          PID    PPID  C STIME TTY          TIME CMD
root           1       0  0 16:29 ?        00:00:00 /sbin/docker-init -- /n
root           7       1  0 16:29 ?        00:00:00 /run/dojo/bin/sleep 6h
root         135       1  0 16:29 ?        00:00:00 su -c /challenge/.launc
hacker       136     135  0 16:29 ?        00:00:00 /challenge/dont_run
hacker       137     136  0 16:29 ?        00:00:00 sleep 6h
hacker       139       0  0 16:30 pts/0    00:00:00 /nix/store/0nxvi9r5ymdl
hacker       145     139  0 16:30 pts/0    00:00:00 /run/dojo/bin/bash --lo
hacker       171     145  0 16:33 pts/0    00:00:00 ps -ef
hacker@processes~killing-processes:~$ kill 136
hacker@processes~killing-processes:~$ /challenge/run
Great job! Here is your payment:
pwn.college{AHfNzV5MXZqwulSz0Tl6zrXOmFx.QXyQDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `kill <PID>` terminates a process by sending a signal.

## References 
The materials provided by my mentor.
<br/>

# Interrupting Processes
The challenge required interrupting a process running in the terminal to access the flag.

## My solve
**Flag:** `pwn.college{g_ljc-NOQ34uYIMIf0MuneBZTP5.QXzQDO0wSO5kjNzEzW}`
<br/>
I ran `/challenge/run` and used `Ctrl-C` to interrupt the process. 
</br>
TERMINAL WORKING : 
```
hacker@processes~interrupting-processes:~$ /challenge/run
I could give you the flag... but I won't, until this process exits. Remember,
you can force me to exit with Ctrl-C. Try it now!
^C
Good job! You have used Ctrl-C to interrupt this process! Here is your flag:
pwn.college{g_ljc-NOQ34uYIMIf0MuneBZTP5.QXzQDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `Ctrl-C` sends an interrupt signal to the foreground process.

## References 
The materials provided by my mentor.
<br/>

# Killing Misbehaving Processes
The challenge required eliminating decoy processes to obtain the flag.

## My solve
**Flag:** `pwn.college{8Hv_LHEgb18vy8LvHi5VMBIpgHq.0FNzMDOxwSO5kjNzEzW}`
<br/>
I identified `/challenge/decoy` processes using `ps -ef | grep /challenge/decoy` and killed them. I then read the flag from `/tmp/flag_fifo`.
</br>
TERMINAL WORKING : 
```
hacker@processes~killing-misbehaving-processes:~$ ps -ef | grep /challenge/decoy | grep -v grep
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{0YvuExZgYPwS8IdYV87F0hPqyAQJIVrUiIg8qz1PbRA6dqt}
pwn.college{QrDEJ-6TZsyIQGotZ5nwynZN1HqqFwMHCL9kp3pVWDqe5te}
pwn.college{KvsFJtn-VD9sv4rUrYevkS1Q9xa-bjyV-wRv2e4pWpaVxlk}
pwn.college{qOFwcRbXxc-XzFLIiR7e2ulQax-9o5sZB6tQVuGWYwIhEvF}
pwn.college{HDd3EI-FotOBgR2tt05s7qdocVf2bRqdJ2OBFSlyCRK9ykA}
pwn.college{6.M7SEw3h3.mITcYiB6dJTf.hTxRYLYzeRDVLPsuPySoduV}
pwn.college{rB7SGs.ZhjMdP.gMB06oyV02jAqyNcS5N-QelpXCGEefbAX}
pwn.college{YpfZmnLukO..NR4mdZfytK.Xb2z3HferuUmpJ5oubY8vZkY}
pwn.college{ixn5irk0XzfDBVPSgYTYlfddHvyEHBERpYiLsWw6R6xUv77}
pwn.college{pisOZn9W6OjW7p5Ni8SHSm2-OjqPBU7cwI298ECd.z1aMSV}
pwn.college{Jhs8rD.M-nLyQAcC0Jeg5yRM8qwm7jth-i.hh5LM.3FpG9o}
pwn.college{9GU4HqbYWgs.Q3RwTxwyFoz.IWo-eseuUZcRsUE61jUVEt3}
pwn.college{pUc5Sh887cCq241aLnIKqEY-g78ePT86EaLqGeV-AHMaqoD}
pwn.college{zCP.MrnCEHZQlFHS2KsDR4kexwfifuBdTUQMcP3Sr-k0Qo6}
pwn.college{nfobY9rwKGqE6DKkTtR1xTgk909xvnNRueJWlzpKhZmUxuM}
pwn.college{HI55O.MiJW9patMbJubwC7wStpyzNZdys6tNp4Op1-iNobq}
pwn.college{xs7P6KbAHenkf5chMav-maCun7qBb0jdz7ID3sMRyByXN-n}
pwn.college{gWTECCzrUnlq4qry.u7H5asbYG1X0jt5exkQyC9tq7lq5rn}
pwn.college{FCxpYYuxtsDMKQrAEysv.nzYi.FHb3nJJamCl3Sxx8ZB75w}
pwn.college{3Gni01C5jbrf-crVTnOI-6Gtwgm9tb0.LDpU2tCBQOW9uNI}
pwn.college{ErYUbOtBkyry.QIpCBR4jAQVDACOfQOy3ayeCaE6t-OdEme}
pwn.college{Y7.ooEbGdD2dnnB-mVhajDDfJn.73d5Uae1P4COrB4mWFPS}
pwn.college{KguT6sEzGze96TgHdTGdMTPsBQlnXn9K8VkvTscMPynBIGc}
pwn.college{dLR5dthrikXbl4CC0I3LUrj4VDqkGfHOSQ8NjW.5ceaPlAi}
pwn.college{.7OxxwQcXXQwAGZgBXJQ3eToqmO7.yoHgoUy4ziLwnFPHoY}
pwn.college{HBH6woCkA3ttuf0mAhTKBNecTwF4.Tn-hC6joCRs6xkiZGV}
pwn.college{7ypQd6YQqYo4TatvxeP44sYTqRmMZDenfzo3F-IAkgBDGmh}
pwn.college{ymcOj1ixGLIjgJtpC0eoOS6gRdMxj4Exhv8CtE9HPEwr-a3}
pwn.college{IMGklmKppIsxyndB7aGCi0FFZg1iDm6ydQXWWf2sLH4UxJD}
pwn.college{46cJmVnYRsaYPU3OJeEEEHB4iYhFo7O6N4N7deHYFq3dOT8}
pwn.college{NR212pcjUUmTei3kzVw7lyzkiHnx5PR3mcIlaTQ7CQt3W9n}
pwn.college{NCH4..Q419HYx2.5L2TGYwBv9gJRGYn6gcFo8-ELP9-Lcb1}
pwn.college{TdWp55JM5yIjYucvuD9BFAP5fQ1soyN6PwlqQSdtoGzUGTO}
pwn.college{0iSbIQIPZ.uOLa2DHN51.POpN3AwOkLuF8RFM8H4d-1-.IK}
pwn.college{e8nlclCWUtBc9LUs9nzkuqtKaBj-oZexZ48vhfioHi...pP}
pwn.college{PxlC2pi4L.MzmLD77dyZCw4XarHeE2YYlEO2H-8nGr1vVF1}
pwn.college{Bv18pN21FEIvWiSmVcqp6UvNThBz9ogtJpZPudIftoOjs8b}
pwn.college{HuKmkyig3FORBqemx0NqWLaeCA7tF60B8w9EGXdGy0re0Bo}
pwn.college{emfg.lBWUGW3v-oQPFoGYPG82Hfwm--41bxeCAgIIaJuquW}
pwn.college{ygJG7qb7AesJEZSSVBBkq1dfNuIga0.qQZo8tyvyzyfaHfp}
pwn.college{LLpQYrcJQnii1cK5MToqhRPl67zk6AQWYjlVnqwA.atkMHC}
pwn.college{rFW1GgVaTvB-T3WatEQrBOEJbhbA8I-lKpowz-SCj8oRyJg}
pwn.college{RMBqXWhRyZC.hAoiGEhylrzr9wzqQSEXysEA2kjh8r.JT7p}
pwn.college{vN1fn1PS9wVcQuQO3lgNXN6gFksMYEPYreDJYTF6UCVRqm2}
pwn.college{Z3c86OCW1ZVS1.7wmqTdnWS1NO-oENnj8nbpoPLhLxEZAOi}
pwn.college{q11tL2JobJfQv4xlsEBYyjD2RxUkLlhnxliDJA4Th97I7C-}
pwn.college{.a2SKUpaNfiEYevWRKzWYsS4ihTl3QsC1TMrA5slk-2p26Z}
pwn.college{Ihs59.ntdwY1mkDK7-WfchGj5iGThfnOQ4BNrYl68XWZN5S}
pwn.college{RPPm.pm8o.Kezo.jPTLesPtbNTtrmCDRE6r3CqNDxSGr.4r}
pwn.college{EBaWAmhLYsCgjOm7Ue2lCgfJswYrqYY.auq76mDHtXA69MW}
pwn.college{42KKVFkrXZo8sLe0psRi1McaTvEDyLUootib4CwBx.hl.ms}
pwn.college{j35X.Lw4GR44xA6f10wqBLz33ln2Pf4DoQ-phPAJ6DgZ0wJ}
pwn.college{y44aKb1T35x8VLi2vw2Rsi4cZEk0zqkFAIoBBjfU-9IkXkk}
pwn.college{M.jru2aTLWcQYz3kDtHF37bez7wvzqAQBdKpw3zcokV8P3v}
pwn.college{TfGohMswNnpMb1pJCXvYD1HxKG-AWrkoD9ns2EB-Da5w3Qs}
pwn.college{Ga-ho98oobx-zNHsFf.MM8Scu1BST.G4i.-Kof75eoqCLvU}
pwn.college{VD--iJRiXqMz7behWKvdRGQUCTOPa6mdg4274LRR5QLR71.}
pwn.college{6S1bxx4I9.UOM0a2GII.l7hJoaY5jrZCKq5MZNOtXwJdugu}
pwn.college{VotgI9vFQU6sNGHxfQ79ofz.Ky.5VBtiQAMyWJCpbaczUnA}
pwn.college{Czcz3AEkygU2qC.TrelwS9qLAvBYSe5kr7ejIA5V4igLDVG}
pwn.college{aMGmg6wohTnJZWJeXnkAPJvI09R7Aza8yie.qHxsVTih3B6}
pwn.college{xZTGXx0i-SLEtGgYKT6g89qDYGB7zyV7m-wTMWHU0xjxAE3}
pwn.college{UuG4yxrNKuSMxwmdgu-7YR3n45iRca.pGkVSPGRHhPAGmEN}
pwn.college{RLv7S64AU1qQgRzXvl8SnmF0w46PZgS.tNjodWQclffEJ5Y}
pwn.college{WzZ5HABZbFCzkfkunvurlwZX5H3SI83118sf3rvbAAI5WE-}
pwn.college{0wI.z41pCpZ54PJk5YtjRhkeKP6spPmiifpFptnxGkbTHJq}
pwn.college{3pVUoWAxsoYEIcCiRuCJWj70.yGaKNpbKhaILEOeJmYDj4h}
pwn.college{Itx..fdpoNOxD1r9Sug4fyymQxDqbAcp.4RLMncyDNN7pwR}
pwn.college{h8raHlb0bWAJR6zxHoibZ5MhEr4ybcqU1bCqxdsEcuCk0WI}
pwn.college{du7M6BPFy7kfg0WENnJ-zdTX4NGBXlB-m5lnkYMlgCHevj6}
pwn.college{UPOcrOmeH1tXBYS2o.CPTTqJQfUJy2TjrYKCcBM4DL2YIHh}
pwn.college{cR-WqvO8z2pLD9dx9Ysk3.phP57QgNHGn3ngwQdFaZ2aXTO}
pwn.college{Ni.xE7jGDnaqSRQSgMAMZl6OIGZKWv6.wzFRMWuM7GLrYM-}
pwn.college{uJ1WUiMMQGuNiGAsHmz7frzVzLvfAnQzJPDF0r7wKHEW9-R}
pwn.college{gBGr.tYJ5w-vTi.9.eoijDPs4jrKGVLBAROY-7cPWwNrFKf}
pwn.college{Khf4ObI55L06bFbfqHWqYMQVHsvsMeVnOqxLbt-o4G4uFii}
pwn.college{3zzcee5JJPcshgxqJgh87Qrs3xD9x84bt3oO91gCx0KXhp6}
pwn.college{R.dj5mlqOm5zh4rqD1tNywu1IQgB9SNqckUQlLce8U2ns7u}
pwn.college{G9rVrCRUcYb8fojmYirGdEadzF0fj3xdKlUEhXYiIzloMr-}
pwn.college{M8vwALZuQa8qEnmOgO09JqAyiBC8TWJBc5OoOw9.j3UvLgy}
pwn.college{TBhYFeJRzR9caTu7ozPQ8AvOfgwXneA.CSnvdmo571Y1Seb}
pwn.college{O38LRRtXld8silxiU4m3MRIA-HNG8LzGVSHKtPWTr08a465}
pwn.college{QtC2rsXC65DYT4GjVsnYRUmWYJN.yXlnsPAUEtRMkqgKTMz}
pwn.college{zFRffh2s4dec9EMHQX8sCJo6z5f8JdASHi36A53ci3NnswJ}
pwn.college{2FPKWq.BLj3UBPoFH8FXgP6fiBXx5PWwJN72DpJAQw75i1w}
pwn.college{RDkwHcco8gzyQl7EQJC1nOAcAW45GiJUDnD8DY35uZ1wwEs}
pwn.college{067yJpYAPUsfEQqYZjlf4uLiIHpQZXwOR550PDxxtld15rw}
pwn.college{.SBW92LsIVkn6jb.oNFI8AC0AaRGtBl3pTgMP9vbAWr9-9S}
pwn.college{5muXFWkLBbvqf.xMoeFJbYfxgEkESgqWgPmDT5vVRKcgP8D}
pwn.college{qAfAPERaFEhoAQKZ9s7ETMBz8Lh1PuxJKf3-H9HbqcTudLQ}
pwn.college{OHuZFg2vbI3-NdMes..NsIW5kj0.BaWPc8aue0b7dKDZKu9}
pwn.college{UDmWYQSC.v0daMuNgrXHXckZPKW1jn6vSLrkcagGxyYljpE}
pwn.college{1OXuLv-d3dgDVKfDouXhL-LXMVCLjP6R20hMSO2IodHXhkA}
pwn.college{FWjSi3fhAeZM-fx.Xwua0A-m1t4t.PWJNW5zwxlzRLx63vB}
pwn.college{0qvKmdF7NFBME7BZzL4zVxDZmtQYbNGFFf628Kc2ZNmHwoc}
pwn.college{fW9jeKOMVCENVTIXA0-QmW6nJENj4Rdagk6COy2PzF5qcyU}
pwn.college{PJHDfMG.NToSFjY38wlA5ug5gsfFa11g7OPafhzHv9dI5cg}
pwn.college{Ap9vyUrmUa-hgpL7dgegKEUwzebw9mp5PZ5PfM7ll58LCaq}
pwn.college{FFBvKrTJiL6vc3a2dA6WvQVZifQ4K85JsDY-DMF8SeUQpc9}
pwn.college{TcMoLPfQXu9ZYmgymiZNH09EvdQlWU2ui43VEPNIReSyRB1}
pwn.college{872OywxN7T1CfepLhkAFk2ktnT6wKDFi.azLjT6B13m9OjL}
pwn.college{JTyqqwc2.d3HOCdO0ZHWrjjwm7ofThvjVSrburouh00Kf5h}
pwn.college{qBLALqVQlkYghPHWwJyDq6dXbN2WHbdN36HPx4Y1rZTYcKF}
pwn.college{531og4AvV0eC-FQJj5eg8LJ-G.FeVjZ7eOkdRQjy8GbWYYa}
pwn.college{MG950y3nMi21046iKApMBQx3k6p4oO9CaeTV-8PyOelCQ.8}
pwn.college{x6Rfe5voNm1WjSpdF9crPUL3iTNUGtvpYdYil8D6aN8fTMT}
pwn.college{Lb0FhWkivxOY.Z.G6-StXGp2Wb15eznzJy2zcTJlnxNmp1a}
pwn.college{rsVG0FWqrf6v5BIwUIyCCa1JWKGf9ivIdi29pNi1QNrvP45}
pwn.college{iH17rJiyw.Q9.Rr.r.mT7YOZ4Pom2uFhhfG4i87qlYiB17d}
pwn.college{t2Of3KABrPmaKPK6.aGheoyrMM449-28GSH4AWaUyGojlM4}
pwn.college{D78kreuUPmufFZkC0ff1h2yVJc8fvzNbghaAfruAEf2XAi4}
pwn.college{Yq32fQ6gV7rzrZVRcHr4SNXdbqlIfyy9QWnvbH9JdBVvJLJ}
pwn.college{KmtziAvaKJMLwPLf3Wv52Dpw5cJnqaBHNRDRiuGkXdjav8i}
pwn.college{uyJTscvgLpgPiUdYOF6pe0kJ2oFBjR0CCz-Y6ygWLStg5eX}
pwn.college{9-dKSrIu3nX5Qr.cIyPmWvJj6duEttrsCp.4ChsHxPFi3eM}
pwn.college{NEa24qgb4JZ4h.vamtyYzmRqf7fJWjXj.8msUCcJZDcce07}
pwn.college{sSpcZ7psJ57CVRtkwcBdk5fYYuoBlv7cu0Z-SXdV36lGdUI}
pwn.college{Qy3IkB-R2Q457srNs4TNQG5NPUnjDILaTvadU4ulKh59jvF}
pwn.college{8ZIefwpsZ6hL9kVDULbPejMrUtKPE6sNmU..lJJpp2zgTUx}
pwn.college{5bdRpWA.Mu2LEmGMg2kp2m6gSNCDWcW9MI2tz-sa8jJbcs8}
pwn.college{xS3PEwvPoTUrudMugNN6a06qIg.Yzn.J7h9MR2Ij7gZp6tO}
pwn.college{kVB5bLlgoUz8lmG9nd0VFMwMTORgRXOc5DNBEMBnINUvJRW}
pwn.college{iuUEJQ69bX-Q9p-ar4VTJYMVPVwvOS5vJGgM17vNjPU8NXj}
pwn.college{L1g4HDVvnmwwDGIyuPUfODpi79MotLGA4idpeYeYEcmhnaY}
pwn.college{kGKycuWkaYm5oqJfe1gsoqX8T9zR2kI-qvzbZy5HaGcAw8q}
pwn.college{44jvtJbJPYvJskl9xjJpo43aYpKW0Z6HA8xrfLKO6EBbi2g}
pwn.college{FF-xUOehdDpytaY.TOJdTcJAjGM0aclNNBbyVlbH6tdOJ1F}
pwn.college{Wgl-ZuRmK4Y3UJ3ZbF5H1C6MkK183PzR7x7vjw34eMJ.2D6}
pwn.college{TRebyU0EbNjBJWDv1jWyByJbs5gCmZgbj6Qp8FoT7mjK.46}
pwn.college{Why0s.HoZF1wURS221IG1hV8-40Xn.4LyWPVNkXFFMaRHjb}
pwn.college{fxHcjQoCSHz207YPv-jR9dpYitTREcTafj3fRrYHIgxrH5N}
pwn.college{Kr4UgMdtc7Cii.HzyEZp30t3kj7jJ.zaqZsVqXrKNvvAbip}
pwn.college{PAl13BZ4vOTD1WeOeYOZ5CWnwjCTr4a3HUuEt2qvzjNBYBF}
pwn.college{br0V9TmdgBrOUxQdIU773IoDCh.Y6AWHmNf3x5poIKp8HGd}
^C
hacker@processes~killing-misbehaving-processes:~$ /challenge/run
Sending the flag to /tmp/flag_fifo!
hacker@processes~killing-misbehaving-processes:~$ cat /tmp/flag_fifo
pwn.college{8Hv_LHEgb18vy8LvHi5VMBIpgHq.0FNzMDOxwSO5kjNzEzW}
```
This generated the flag and the challenge was completed!

## References 
The materials provided by my mentor.
<br/>

# Suspending Processes
The challenge required suspending a running process and then resuming it.

## My solve
**Flag:** `pwn.college{0Vk_bYNrjN3WcziPr0blEKwQQ0K.QX1QDO0wSO5kjNzEzW}`
<br/>
I ran `/challenge/run` and pressed `Ctrl-Z` to suspend the process. 
</br>
TERMINAL WORKING : 
```
hhacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         138     129  0 17:11 pts/0    00:00:00 bash /challe
root         140     138  0 17:11 pts/0    00:00:00 ps -f

I don't see a second me!

To pass this level, you need to suspend me and launch me again! You can
background me with Ctrl-Z or, if you're not ready to do that for whatever
reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~suspending-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running in
this terminal... Let's check!

UID          PID    PPID  C STIME TTY          TIME CMD
root         138     129  0 17:11 pts/0    00:00:00 bash /challe
root         145     129  0 17:12 pts/0    00:00:00 bash /challe
root         147     145  0 17:12 pts/0    00:00:00 ps -f

Yay, I found another version of me! Here is the flag:
pwn.college{0Vk_bYNrjN3WcziPr0blEKwQQ0K.QX1QDO0wSO5kjNzEzW}
```


## What I learned
I learned the following from this challenge : 
1. `Ctrl-Z` suspends a foreground process.

## References 
The materials provided by my mentor.
<br/>

# Resuming Processes
The challenge required suspending and then resuming a process using the `fg` command.

## My solve
**Flag:** `pwn.college{gE8l5fGaf05GBGCDqDkspVw11iA.QX2QDO0wSO5kjNzEzW}`
<br/>
I executed `/challenge/run`, suspended it using `Ctrl+Z`, and then resumed it in the foreground using `fg`.
</br>
TERMINAL WORKING : 
```
hacker@processes~resuming-processes:~$ /challenge/run
Let's practice resuming processes! Suspend me with Ctrl-Z, then resume me with
the 'fg' command! Or just press Enter to quit me!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~resuming-processes:~$ fg
/challenge/run
I'm back! Here's your flag:
pwn.college{gE8l5fGaf05GBGCDqDkspVw11iA.QX2QDO0wSO5kjNzEzW}
Don't forget to press Enter to quit me!

Goodbye!
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The `fg` command resumes a suspended process and brings it to the foreground.

## References 
The materials provided by my mentor.
<br/>

# Background Processes
The challenge required suspending a process, resuming it in the background, and then launching another instance of it.

## My solve
**Flag:** `pwn.college{Ul8Sg6GJowoba1NJ8HMfFylhF34.QX3QDO0wSO5kjNzEzW}`
<br/>
I ran `/challenge/run`, suspended it with `Ctrl+Z`, resumed it in the background using `bg`, and then launched another instance of `/challenge/run` while the first was active.
</br>
TERMINAL WORKING : 
```
hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         140 S+   bash /challenge/run
root         142 R+   ps -o user=UID,pid,stat,cmd

I don't see a second me!

To pass this level, you need to suspend me, resume the suspended process in the
background, and then launch a new version of me! You can background me with
Ctrl-Z (and resume me in the background with 'bg') or, if you're not ready to
do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~backgrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~backgrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out.

hacker@processes~backgrounding-processes:~$ /challenge/run
I'll only give you the flag if there's already another copy of me running *and
not suspended* in this terminal... Let's check!

UID          PID STAT CMD
root         140 S    bash /challenge/run
root         150 S    sleep 6h
root         151 S+   bash /challenge/run
root         153 R+   ps -o user=UID,pid,stat,cmd

Yay, I found another version of me running in the background! Here is the flag:
pwn.college{Ul8Sg6GJowoba1NJ8HMfFylhF34.QX3QDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `bg` resumes a suspended process in the background.
2. Multiple processes can run simultaneously using backgrounding.

## References 
The materials provided by my mentor.
<br/>

# Foregrounding Processes
The challenge required foregrounding a backgrounded process using the `fg` command.

## My solve
**Flag:** `pwn.college{QUKezSTN8noHuwjVIaz_V-nUzaO.QX4QDO0wSO5kjNzEzW}`
<br/>
I ran `/challenge/run`, suspended it using `Ctrl+Z`, resumed it in the background with `bg`, and finally brought it back to the foreground with `fg`.
</br>
TERMINAL WORKING : 
```
hacker@processes~foregrounding-processes:~$ /challenge/run
To pass this level, you need to suspend me, resume the suspended process in the
background, and *then* foreground it without re-suspending it! You can
background me with Ctrl-Z (and resume me in the background with 'bg') or, if
you're not ready to do that for whatever reason, just hit Enter and I'll exit!
^Z
[1]+  Stopped                 /challenge/run
hacker@processes~foregrounding-processes:~$ bg
[1]+ /challenge/run &
hacker@processes~foregrounding-processes:~$


Yay, I'm now running the background! Because of that, this text will probably
overlap weirdly with the shell prompt. Don't panic; just hit Enter a few times
to scroll this text out. After that, resume me into the foreground with 'fg';
I'll wait.

hacker@processes~foregrounding-processes:~$ fg
/challenge/run
YES! Great job! I'm now running in the foreground. Hit Enter for your flag!

pwn.college{QUKezSTN8noHuwjVIaz_V-nUzaO.QX4QDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. The `fg` command can bring a backgrounded process back to the foreground.

## References 
The materials provided by my mentor.
<br/>

# Starting Background Processes 
The challenge required foregrounding a backgrounded process using the `fg` command.

## My solve
**Flag:** `pwn.college{8KyVAgJ2f__5M4W4AuCLOd7-FEo.QX5QDO0wSO5kjNzEzW}`
<br/>
I ran  `/challenge/run &` to launch the process directly in the background.
</br>
TERMINAL WORKING : 
```
hacker@processes~starting-backgrounded-processes:~$ /challenge/run &
[1] 156
hacker@processes~starting-backgrounded-processes:~$


Yay, you started me in the background! Because of that, this text will probably
overlap weirdly with the shell prompt, but you're used to that by now...

Anyways! Here is your flag!
pwn.college{8KyVAgJ2f__5M4W4AuCLOd7-FEo.QX5QDO0wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!

## What I learned
I learned the following from this challenge : 
1. Appending `&` to a command runs it directly in the background.
## References 
The materials provided by my mentor.
<br/>

# Processing Exit Codes
The challenge required retrieving the exit code of one program and using it as input to another.

## My solve
**Flag:** `pwn.college{U_nW-14Y6hMMgSAxGo2t8CfHlRj.QX5YDO1wSO5kjNzEzW}`
<br/>
I ran `/challenge/get-code` to obtain an exit code, checked it using `echo $?`, and passed the retrieved value to `/challenge/submit-code`.
</br>
TERMINAL WORKING : 
```
hacker@processes~process-exit-codes:~$ /challenge/get-code
Exiting with an error code!
hacker@processes~process-exit-codes:~$ echo $?
209
hacker@processes~process-exit-codes:~$ /challenge/submit-code 209
CORRECT! Here is your flag:
pwn.college{U_nW-14Y6hMMgSAxGo2t8CfHlRj.QX5YDO1wSO5kjNzEzW}
```
This generated the flag and the challenge was completed!


## What I learned
I learned the following from this challenge : 
1. `$?` stores the exit code of the last executed command.
2. Exit code 0 usually means success, while non-zero values indicate different failure states.

## References 
The materials provided by my mentor.
<br/>
