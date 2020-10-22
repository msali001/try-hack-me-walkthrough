# Lazy Admin

export IP=10.10.140.218

nmap -sC -sV -oN nmap/initial 10.10.140.218

```
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.8 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 49:7c:f7:41:10:43:73:da:2c:e6:38:95:86:f8:e0:f0 (RSA)
|   256 2f:d7:c4:4c:e8:1b:5a:90:44:df:c0:63:8c:72:ae:55 (ECDSA)
|_  256 61:84:62:27:c6:c3:29:17:dd:27:45:9e:29:cb:90:5e (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-server-header: Apache/2.4.18 (Ubuntu)
|_http-title: Apache2 Ubuntu Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

```

gobuster located

```
/content

```
searchsploit returned

```
 Exploit Title                                                                                                 |  Path
--------------------------------------------------------------------------------------------------------------- -----------------------
SweetRice 0.5.3 - Remote File Inclusion                                                                        | php/webapps/10246.txt
SweetRice 0.6.7 - Multiple Vulnerabilities                                                                     | php/webapps/15413.txt
SweetRice 1.5.1 - Arbitrary File Download                                                                      | php/webapps/40698.py
SweetRice 1.5.1 - Arbitrary File Upload                                                                        | php/webapps/40716.py
SweetRice 1.5.1 - Backup Disclosure                                                                            | php/webapps/40718.txt
SweetRice 1.5.1 - Cross-Site Request Forgery                                                                   | php/webapps/40692.html
SweetRice 1.5.1 - Cross-Site Request Forgery / PHP Code Execution                                              | php/webapps/40700.html
SweetRice < 0.6.4 - 'FCKeditor' Arbitrary File Upload                                                          | php/webapps/14184.txt
--------------------------------------------------------------------------------------------------------------- -----------------------

```

SweetRice 1.5.1 - Backup Disclosure  ----- Worked
```
Username and password ---- manager - Password123

```
SweetRice 1.5.1 - Cross-Site Request Forgery / PHP Code Execution  ---- Worked


Reverse Shell obtained

Flag found in home
sudo -l
```
Matching Defaults entries for www-data on THM-Chal:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on THM-Chal:
    (ALL) NOPASSWD: /usr/bin/perl /home/itguy/backup.pl
```
ls -l /etc/copy.sh ------- is writable!
```
-rw-r--rwx 1 root root 5 oct 19 19:24 /etc/copy.sh

```
/etc/copy.sh  ---- modified to run bash
Privilage escalated to root
Flag found root's home


#1 What is the user flag?

```
THM{63e5bce9271952aad1113b6f1ac28a07}
```

#2 What is the root flag?

```
THM{6637f41d0177b6f37cb20d775124699f}
```




