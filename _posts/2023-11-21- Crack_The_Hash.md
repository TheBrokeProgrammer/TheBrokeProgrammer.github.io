---
title: Crack The Hash
categories: [THM Writeups]
tags: [thm,pentest]
---

https://hashcat.net/wiki/doku.php?id=example_hashes
or use hashid to identify the right id to use in the hash.


1. 48bb6e862e54f2a795ffc4e541caed4d
```
hashcat -m 0 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/bZWDl8z.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This MD5 hash was successfully cracked using the RockYou wordlist, demonstrating the vulnerability of MD5 to common password lists.


2. CBFDAC6008F9CAB4083784CBD1874F76618D2A97
```
hashcat -m 100 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/pFSPEQi.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This SHA1 hash was successfully cracked using the RockYou wordlist, indicating the effectiveness of dictionary attacks against SHA1.

3. 1C8BFE8F801D79745C4631D09FFF36C82AA37FC4CCE4FC946683D7B336B63032
```
hashcat -m 1400 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/0uElyjB.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This SHA256 hash was cracked using the RockYou wordlist, showing that even stronger hashes can be cracked if weak passwords are used.

4. $2y$12$Dwt1BZj6pcyc3Dy1FWZ5ieeUznr71EeNkJkUlypTsgbX1H68wsRom
```
hashcat -m 1400 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
Its so long to crack i forgot to screenshot this one HAHAHAHAHAHAH, the answer for this one is "bleh"
**Outcome:** Successfully cracked. 
**Thoughts:** This bcrypt hash was cracked, though it took longer due to bcrypt's computational intensity, underscoring the importance of strong password algorithms.

5.  279412f945939ba78ce0758d3fd83daa
```
hashcat -m 900 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/dLttZCr.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This MD4 hash was cracked, indicating that while MD4 is weak, it can still be vulnerable to a good dictionary attack.

6. Hash: F09EDCB1FCEFC6DFB23DC3505A882655FF77375ED8AA2D1C13F640FCCC2D0C85
```
hashcat -m 1400 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/kbubX0D.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This SHA256 hash was cracked, indicating that even stronger hashes can be vulnerable to dictionary attacks if weak passwords are used.

7. Hash: 1DFECA0C002AE40B8619ECF94819CC1B
```
hashcat -m 1000 -a 0 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/KYz7MzN.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This NTLM hash was cracked using the RockYou wordlist, showing the vulnerability of NTLM hashes, especially with commonly used passwords.

8. Hash: $6$aReallyHardSalt$6WKUTqzq.UQQmrm0p/T7MPpMbGNnzXPMAXi4bJMl9be.cfi3/qxIf.hsGpS41BqMhSrHVXgMpdjS6xeKZAs02.

Salt: aReallyHardSalt
```
hashcat -m 1800 hash.txt /usr/local/bin/rockyou.txt
```
![img](https://i.imgur.com/KEQCL3H.png)
**Outcome:** Successfully cracked. 
**Thoughts:** This SHA512crypt hash was successfully cracked, showing that even with a strong algorithm, the use of a weak password makes it vulnerable.

9. Hash: e5d8870e5bdd26602cab8dbe07a942c8669e56d6

Salt: tryhackme
```
hashcat -m 150 e5d8870e5bdd26602cab8dbe07a942c8669e56d6:tryhackme"/usr/local/bin/rockyou.txt
```
Answer:  *481616481616*

**Outcome:** Successfully cracked. 
**Thoughts:** This HMAC-SHA1 hash with a known salt was cracked, demonstrating the importance of using both strong salts and strong passwords to enhance security.


