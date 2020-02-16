---
title: "w4 deliverable"
date: 2020-02-17T01:09:51+11:00
showDate: false
---
# boot2root writeup

__vulnerable machine__: [kioptrix Level 1](https://www.vulnhub.com/entry/kioptrix-level-1-1,22/)

author: [kioptrix](https://www.vulnhub.com/author/kioptrix,8/)

**objective**: acquire root access

**tools**:
- kali linux
- netdiscover
- nmap
- gobuster
- metasploit
- nbtscan
- nikto
- tcp shell bind
- trans2open

## reconnaissance.

i first used netdiscover to scan for the possible ip address of kioptrix. 

![netdiscover](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/1.PNG?raw=true)

from the look of the list of addresses, 192.168.48.131 didn't seem to belong, so i scanned that with nmap. 

![nmap](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/2.PNG?raw=true)

this lead me to a web server running on redhat linux (as described in kioptrix), so it was safe to assume this was the address i was looking for. 

port 139 is used by the netbios-ssn service on samba, so i ran an nbtscan to find out more...
![nbtscan](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/5.PNG?raw=true)
this confirms we are scanning the right ip address.

## locating directories.

i used gobuster to use brute force to gather common directory names i could try to intercept. the results were quite promising.

![gobuster](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/3.PNG?raw=true)

however, i was still blocked from accessing these pages...

![/manual](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/4.PNG?raw=true)

## finding exploits.

i used nikto to search for possible ways to exploit the system. from here we can see a few ways how this system is vulnerable...

![nikto](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/6.PNG?raw=true)

i then used metasploit to search for ways to compromise samba. 

![metasploit](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/7.PNG?raw=true)

after playing around with a few of the options i decided to stick with trans2open as it was simple enough for me to use. 

![exploit search](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/8.PNG?raw=true)

here, all i need to do is set the remote host and port, and trans2open will initiate a bruteforce attack.

![trans2open](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/8.PNG?raw=true)

![rhost set](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/9.PNG?raw=true)

## privilege escalation.

i ran a search for a payload compatible with trans2open through metasploit again. because i am trying to gain root access, i'd want to use the shell bind tcp. 

![show payloads](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/10.PNG?raw=true)

![set payload](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/11.PNG?raw=true)

now, all i need to hit __exploit__ with metasploit, and voila!
![exploit](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/12.PNG?raw=true)

we have successfully used brute force to gain shell access. now we just need to bash into the shell and we have achieved privilege escalation.

## root access.

looking through the directories we can find some interesting files that mark the completion of this challenge. 

![ls](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/13.PNG?raw=true)

![completion](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/kioptrix/14.PNG?raw=true)