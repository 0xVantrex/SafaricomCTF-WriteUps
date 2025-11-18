# Beauty Trap — writeup

**Category:** Cryptography / Steganography  
**Difficulty:** Easy (56 solves)  
**Tooling used:** `file`, `xxd`/`strings`, `base64`, `steghide`, `exiftool` (optional)  
**Final flag (accepted):**  
`safctf{edae3ec1-701f-452f-9ead-d90fbbe2e5dc}`

---

## Summary

The challenge provided a single image `beauty.jpg`. The trick: metadata (JPEG comment) contained a Base64 string which decoded to a password for a hidden payload embedded with `steghide`. Extracting with that password produced an ASCII file containing what looked like a flag — the CTF checker required the flag prefix in lowercase, so submitting `safctf{...}` (all lower) was accepted.

---

## Step-by-step

1. **Initial reconnaissance**
    
    `file ~/Downloads/beauty.jpg`
    
    Output included a JPEG comment: `MWE6QTQuMXwtYlgzW2lJYg==`
    
2. **Decode the comment (Base64)**
    
    `echo 'MWE6QTQuMXwtYlgzW2lJYg==' | base64 -d`
    
    Result: `1a:A4.1|-bX3[iIb` — this looks like a password.
    
3. **Use `steghide` to extract embedded data**
    
    `steghide extract -sf ~/Downloads/beauty.jpg -p '1a:A4.1|-bX3[iIb'`
    
    Output: `wrote extracted data to "secret"`
    
4. **Inspect the extracted file**
    
    `file secret cat secret`
    
    Contents: `safCTF{edae3ec1-701f-452f-9ead-d90fbbe2e5dc}`
    
5. **Submission nuance**  
    The challenge expected the prefix in lowercase. Submitting the extracted string **as-is** failed; submitting the lowercased prefix succeeded:
    
    `safctf{edae3ec1-701f-452f-9ead-d90fbbe2e5dc}`
    

---

## Notes, tips & alternative checks

- Always run `file`, `strings`, and `exiftool` on images in crypto/stego challenges. Metadata and embedded comments are commonly used.
    
    `strings beauty.jpg | egrep -i 'CTF|flag|comment' exiftool beauty.jpg`
    
- If `steghide` prompts for a passphrase, try obvious words from metadata, challenge text, or decode Base64 comments like we did.
    
- If nothing shows up, use `binwalk -Me` to look for appended archives or hidden files.
    
- Watch for trivial submission issues: extra newlines, case-sensitivity, or surrounding whitespace. Use `tr -d '\r\n' < secret` before copying.