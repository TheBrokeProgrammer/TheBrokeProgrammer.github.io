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


![Imgur](https://i.imgur.com/eE3T6so.png)

We made it to access the portal

But some pages is not allowed for us, only the commands pages only

![Imgur](https://i.imgur.com/TbM1kDC.png)

So lets utilize the command panel, use ls command to list the contents of a directory. 

![Imgur](https://i.imgur.com/av7rCBe.png)

The moment i try to open the Sup3rS3cretPickl3Ingred.txt with a cat command, there is a message 

![Imgur](https://i.imgur.com/lTEqiH1.png)

If the ls command is disabled or unavailable, you can use other commands like: less,more,tail,sed etc.

For me i used less and it gave me the result and the output of that file is the first ingredients.

We see that there is a clue.txt file and the output of that is: 

![Imgur](https://i.imgur.com/ylrpio8.png)

but anw i see the value of denied.php using "tac" command

![img](https://i.imgur.com/ZGQ4t8G.png)

Okay so lets traverse now 

![img](https://i.imgur.com/bhT5LNU.png)

Always go to the directory that you think is the juiciest part, which for me is the 'home' directory

![img](https://i.imgur.com/h6RwpYq.png)

Go to rick directory and we will see the second ingredients

so lets find out the last ingredients, go to root directory which is the common directory to see the final flag.

But when i try to use just the "ls" it does not show anything.

hmm? maybe because we have to use "sudo" ? to be able to access the root and we can see that the sudo command is not part of disabled command.

![img](https://i.imgur.com/skwVjQC.png)

YEHEYYYY THIS IS THE FINAL INGREDIENTS WE CAN HELP RICK NOW TO MAKE HIS POTION!!!