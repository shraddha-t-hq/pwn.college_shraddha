# Aethercorb NetprobeX 
---
## Challenge summary
You enter a simulation of AetherCorp and its flagship networking tool, NetProbeX. 
The floor reconstructs the events that led to humanity’s downfall.
Engineers left faint traces in the system logs — small, odd markers where separators once sat. 
By reading those traces as if they divide commands you must reconstruct original command sequences, identify the backdoor flaw in NetProbeX, and 
recover the passcode required to advance to the next floor.
</br>
## Files provided
The link of a website was provided that worked as a terminal to conduct commands.
</br>
## How I solved it
I first ran ` ls ` to list the directory contents and confirmed the presence of four relevant log artifacts.
The ` cat ` command was **restricted** in the environment, so I used ` more ` (which was permitted) to page through and extract the contents of each file. 
Using more I copied out the log fragments.
</br>
Through online research I learned that I had to use odd markers that resembled IP-like tokens(for example 8.8.8.8%0a in URL-encoding or 0a as the ASCII hex for newline).
Treating those markers as separators allowed me to reconstruct the original command sequences and put in my commands into the dialogbox to execute.
Therefore, I performed the forensics (file discovery, resilient file-reading under restricted commands, marker decoding) and delivered file contents that enabled the next-stage exploit and retrieval of the citadel{...} passcode.
</br>
## What I learnt
**Interpreting the odd markers / “universal ip” tokens**
The IP addresses with appended markers are not literal network commands but obfuscated separators
— they indicate where separators (often newlines) had been replaced with encoded tokens.
Below are the variants you recorded and how to interpret them:
</br>
8.8.8.80a
</br>
8.8.8.8.0als
</br>
8.8.8.8.0amore
</br>
**Interpretation & explanation**
8.8.8.8 — looks like an ordinary IP address (Google DNS), commonly used in puzzles as a recognizable anchor.
</br>
0a — in hexadecimal notation, 0x0a is the ASCII code for newline (\n). In URL encoding a newline is commonly represented by %0a. When logs or URLs are mangled, that newline marker can show up as 0a or %0a appended to nearby tokens.
</br>
8.8.8.80a — likely represents 8.8.8.8 immediately followed by a 0a (newline), i.e., 8.8.8.8<newline>. Reading it this way lets you treat that marker as a command separator.
</br>
8.8.8.8.0als — meaning the original stream was 8.8.8.8\nls but the newline was encoded and merged into the token `ls`.
</br>
8.8.8.8.0amore — similarly decodes to 8.8.8.8<newline>more or 8.8.8.8\nmore, indicating that more was the command on the next line.
