---
title: Pickle Rick
categories: [THM Writeups]
tags: [thm,pentest]
---
![Imgur](https://i.imgur.com/yw2LeM0.png)

This Rick and Morty-themed challenge requires you to exploit a web server and find three ingredients to help Rick make his potion and transform himself back into a human from a pickle.

Use Nmap to efficiently scan and assess these potential security risks.

![Imgur](https://i.imgur.com/OMRJETa.png)

Upon discovering that port 80 is open, Lets try to access the default webpage

![Imgur](https://i.imgur.com/FKW6X0I.png)

What we see here is rick became a pickle again and want a help from Morty. Imagine that we are Morty, we have to help rick to make himself back into a human again. 

I dont know what is BURPPPPPP means, hmm Burpsuite? lets see.

What we have to do now is to find credentials for us to logon into rick's computer

![Imgur](https://i.imgur.com/l0z7o2T.png)

I inspect the webpage and wee see here the note that the username is *R1ckRul3s* but theres no password here

Hmmmmm i always go to robots.txt directory wishing that there is some juicy stuff.

![Imgur](https://i.imgur.com/JW0Ufjm.png)

Ohshiiee maybe this is the password? lets find out

Lets dirb to see other directories

![Imgur](https://i.imgur.com/0mIwxSW.png)


There is a login page and lets try the credentials that we've saw earlier.

![Imgur](https://i.imgur.com/kaPL5Tk.png)

