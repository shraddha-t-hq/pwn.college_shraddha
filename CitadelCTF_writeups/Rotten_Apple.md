## Rotten Apple — Reversing Dual ROT Warps

---

## Challenge Summary  
The challenge description hinted at a distortion, comparing it to a *warped album*. 
The password to the next floor was said to have been warped first by a factor of **47**, and then by a factor of **13** — a clear reference to **ROT47** and **ROT13**,
two forms of simple substitution ciphers based on character rotation.
</br>
**Given Ciphertext:**  
4:R256=Y3oRRoP0#~%Ro?A

</br>

## How I Solved It 
The wording “warped by a factor of 47, then by a factor of 13” strongly suggested a combination of **ROT47** and **ROT13** — both are rotation ciphers commonly seen in CTF puzzles.
Since the password was *first* warped by ROT47 and *then* by ROT13, to reverse it, I needed to:
- Undo ROT13 first,  
- Then undo ROT47.
</br>
**Step 1 — Apply ROT13:**  
Input: 4:R256=Y3oRRoP0#~%Ro?A
Output: 4:E256=L3bEEbC0#~%Eb?N
</br>
**Step 2 — Apply ROT47:**  
Input: 4:E256=L3bEEbC0#~%Eb?N
Output: citadel{b3tt3r_ROTt3n}
</br>
The decoded flag was:
citadel{b3tt3r_ROTt3n}

## Output of the System  
citadel{b3tt3r_ROTt3n}
</br>

## What I Learned  
### 1. Understanding ROT13  
- **ROT13 (rotate by 13 places)** is a classical Caesar cipher variant that substitutes each letter with the one 13 positions after it in the alphabet.   
- It only affects **A–Z** and **a–z** characters.

### 2. Understanding ROT47  
- **ROT47** extends the same principle to the **ASCII printable range** (from `!` (33) to `~` (126)), rotating each character by 47 positions within that set.  
- This means ROT47 affects not just letters but also digits, punctuation, and special characters, making it more “visual” and suitable for deforming short strings that contain symbols.
