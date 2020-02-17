---
title: "week 4"
date: 2020-02-17T00:31:23+11:00
showDate: false
---

### *this was probably my worst week since beginning this studio.*

there were many obstacles this week where i became stuck for a lot longer than i had hoped, pulling me behind from getting my sprint and deliverable completed within a reasonable time.

### monday
it didn't take me long to realise that running 2 virtual machines on a laptop with 4GB of ram was not feasible. despite being introduced to vulnerable boxes like 'basic pentesting' and 'wakanda', all i could do was watch the demos and try to follow what was happening. but, with my lack of experience in hacking i was lost very quickly. i left class early so i can work on this on a more reliable PC, but i ended up spending the rest of the day installing vmware and setting up kali.

### wednesday
my plan for today was to complete *basic pentesting 1* and *vulnversity* so that i got an idea of how to solve these boxes before i approach my deliverable. however after coming into class i ran into issues with connecting to the vpn and maintaining a stable connection to the server. working in the shell was *extremely* slow making it difficult. i spent around 6 hours in class, however about 5 of those hours were spent waiting for scans and connections. i think if i had given up and done the rest of the work elsewhere, i would have had a much more productive day. 

![sloooooooooooow](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/SmartSelect_20200217-003706_Gallery.gif?raw=true)

### thursday
 after consulting the tutors i learned the slow connectivity was caused by a firewall issue with UTS. i tried connecting through my mobile hotspot instead, but this was still not much better. i tried to complete *basic pentesting 1* today because it did not require openVPN, however i still struggled with slow connection speeds. being in class was quite stress-inducing this week because i seemed to have issues while my classmates paced ahead of me. but, this did give me a good opportunity to consult my tutors who were really happy to help. in the end, i accepted that i would need to do the majority of my work at home and studied theory during classtime by looking at tutorials on pentesting. 
 
 ### attempt at *basic pentesting 1*
 
 first i was able to find the ip address simply by checking the network connection settings in the login menu on the virtual machine.
 
 ![network connections](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/connection%20settings.PNG?raw=true)
 
 so, i used this ip address to run an nmap scan to find any open ports.
 
 ![nmap scan](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/nmap%20scan.PNG?raw=true)
 
 we now know that the web service is running on port 80, and we can use dirbuster to check for potential hidden directories.
 
 ![dirbuster](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/dirbuster%20scan.PNG?raw=true)
 
 /secret/ appeared as a result, which led us to an interesting page...
 
 ![secret page](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/secret%20blog.PNG?raw=true)
 
i was able to log into the admin account on wordpress using very simple brute force. this was not too hard to guess because wordpress confirms that the username specifically is correct. the password "admin" was my first guess, since that is what is often used with default network logins.

![wordpress login](https://github.com/yukariinc/yukariinc.github.io/blob/master/images/wordpress%20login.png?raw=true)

i googled for a malicious wordpress plugin and found one fron pwnedsauce, which i uploaded onto the server. this was as far as i got before i gave up due to connection issues.

### the deliverable.

because of how behind i was already, my plan of completing *basic pentesting 1* and *vulnversity* before i do my deliverable did not succeed. instead, i tried to apply as much of my limited knowledge as i could to complete kioptrix, and rely on google to aid with some tools i haven't used yet like metasploit and nbtscan. although this was extremely challenging, it has definitely forced me to learn a lot about pentesting and it was honestly a fun experience. if i had more time, i would like to go back and experiment more different ways to root the machine and continue with the kioptrix series.

### SLO progression.
1. i consulted the tutors a lot for advice on how i should approach this week's deliverable, and was glad that i did. i think i was recommended a decent machine that was just at my skill level, that was simple enough for me to solve but challenging enough for me to learn from.
2. i had to put my theoretical knowledge into practice while using my creativity to approach the various boxes. each box had different solutions which made me learn more creative ways to hack.
3. i only came up with one solution for the deliverable and did not finish the other boxes. i hope to come up with more solutions for these in the next week.
4. this week i relied heavily on my tutors for assistance with issues i couldn't wrap my head around. although i try to be as helpful as i can to my other classmates, i think this week i was a lot more dependent others than i was being dependable. i hope to catch up by week 5 so that i can be a better team-mate in my class.
5. although i am happy with the solution i got for my deliverable, i know that i should have out more time into solving it rather than dealing with technical issues. with some more time, i can finish *basic pentesting 1* and *vulnversity*, as well as think of more ways to hack kioptrix.

### reflection.

this week was extremely difficult, not because of the work we had to do, but because of the issues i faced with networks. i wish i was able to approach these faster by doing more work at home rather than at uni. i felt quite discouraged and unmotivated due to the issues, but thanks to the tutors i was able to pick myself up and tackle the deliverable within time. next week, i aim to catch up and produce higher quality work than i have previously.