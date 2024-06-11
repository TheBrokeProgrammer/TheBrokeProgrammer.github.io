---
title: Simple CTF
categories: [THM Writeups]
tags: [thm,pentest]
---


I performed an Nmap scan to thoroughly assess the network's security posture and identify any open port

![img](https://i.imgur.com/GqAQFMV.png)

 Utilized ffuf to conduct a directory search for dirbusting, enabling the identification of hidden or unlisted directories within the target system.

![img](https://i.imgur.com/SOLrefE.png)


FFUF was able to find there is a webpage at “/simple”. Let’s try browsing to it now and see what we find.

![img](https://i.imgur.com/KKdMVOj.png)

Now that we know this is a CMS, we recognize that CMS platforms are often vulnerable to various types of attacks.

![img](https://i.imgur.com/Ry9P8vm.png)

Let's search if we can see some exploits with this CMS version


![img](https://i.imgur.com/cq13OAj.png[/img])

In our findings, we identified a page on Exploit-DB that corresponds with our search criteria. It details a SQL injection vulnerability, specifically exploiting CVE-2019-9053.

![img](https://i.imgur.com/VABXJsz.png)

Copy this file or download it and run this with the parameter needed.

Use this command to run it

```
python exploit.py -u http://[target-ip]/simple --crack -w /usr/share/wordlists/rockyou.txt
```

(Note: Initially, the script failed to execute because the "termcolor" module was not installed on my machine. To resolve this issue, I installed the module using the command: `pip install termcolor`.)

![img](https://i.imgur.com/3Rb0Knk.png)

Yehey we have a credential now. 

Recall that we observed a port running SSH. Perhaps we can utilize these credentials to establish an SSH connection.

![img](https://i.imgur.com/MrkPmz8.png)

We have successfully established a connection using the "mitch" credentials. At this stage, we are able to access the "user.txt" file, which contains a flag.


We see another user in the /home directory which is "sunbath"


## PrivEsc

sudo -l command is used to list the permissions that a user has via sudo, which is a program that allows users to execute commands with the security privileges of another user, typically the superuser (root).

![img](https://i.imgur.com/q829qwP.png)


After seeing that i searched immediately in https://gtfobins.github.io/ to find a way to bypass this and be a root and i see this one: 

![img](https://i.imgur.com/5oMeii7.png)


![img](https://i.imgur.com/IrMZ4hH.png)

Yehey!! We are root now and you can find the root flag here.
