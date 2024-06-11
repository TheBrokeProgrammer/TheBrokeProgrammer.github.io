---
title: LazyAdmin
categories: [THM Writeups]
tags: [thm,pentest]
---

I performed an Nmap scan to thoroughly assess the network's security posture and identify any open ports. This detailed analysis helps in understanding potential vulnerabilities and securing the network effectively.

![img](https://i.imgur.com/bReNuXL.png)


I utilized ffuf to conduct a directory search for dirbusting, enabling the identification of hidden or unlisted directories within the target system.

```
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt:FUZZ -u http://{TARGET-IP}/FUZZ
```

![img](https://i.imgur.com/bD4FIlF.png)

Upon discovering the /content directory, I accessed it and found a hint indicating that it is powered by the CMS SweetRice.

![img](https://i.imgur.com/LRou7df.png)

I conducted an additional ffuf scan targeting the `/content` directory to uncover any further hidden or unlisted subdirectories and files.

![img](https://i.imgur.com/fst4XDh.png)

The most significant discovery from the additional ffuf scan was the /inc directory, which contained potentially valuable information.

![img](https://i.imgur.com/ZJSrSFL.png[/img)

There were numerous PHP files, which immediately made me think we might be able to upload a reverse shell. However, we cannot view the contents of these files.

But we see also that there is a mysql_backup directory and when i try to open that we will see a sql.



![img](https://i.imgur.com/wHyOsIE.png)



Aside from /inc directory there is also a /as directory which is a login page for SweetRice CMS

![img](https://i.imgur.com/buzGDUA.png)

Default credentials are not an option for this case, but we noticed that the database file is exposed, which might contain the credentials we need to gain access.

```
grep "passw" mysql_bakup_20191129023059-1.5.1.sql
```

![img](https://i.imgur.com/vkNsyfW.png)

You will find the credentials here, but the password is in hash form. We need to decrypt this hash using CrackStation.


![img](https://i.imgur.com/27dF6lw.png)


I used the credentials that we saw and yea we successfully login as manager.

![img](https://i.imgur.com/OedmQeQ.png)

The first thing that comes to mind in this situation is figuring out how we can upload our `revshell.php` file.

I discovered that the Ads feature allows file uploads, which provides an opportunity to upload our `revshell.php` file.

![img](https://i.imgur.com/ekGuk3j.png)

Let's set up our listener before navigating to the directory containing our `revshell.php` file.

![img](https://i.imgur.com/0CczBd6.png)

Load the revshell file and wait until we access to the shell.

![img](https://i.imgur.com/WLghU0t.png)

```
python3 -c 'import pty; pty.spawn("/bin/bash")'
```
Use this script to have a live shell

![img](https://i.imgur.com/eiOhobK.png)

We can see here the 1st flag for this challenge.

