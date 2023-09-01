# Academy (192.168.64.4) CTF Write-Up

**Author:** Alan Garcia  
**Date:** 9/1/2023

## Table of Contents
- [Introduction](#introduction)
- [Challenge Overview](#challenge-overview)
- [Initial Reconnaissance](#initial-reconnaissance)
- [Exploitation](#exploitation)
- [Privilege Escalation](#privilege-escalation)
- [Flag Retrieval](#flag-retrieval)
- [Conclusion](#conclusion)
- [Resources](#resources)

---

## Introduction
Academy was developed by TCM Academy

## Challenge Overview
This challenge has the easy dificulty

## Initial Reconnaissance
Detail the information-gathering phase:
- IP address: 192.168.64.4
- NMAP:
  - 21/tcp open  ftp     vsftpd 3.0.3
  | ftp-anon: Anonymous FTP login allowed (FTP code 230)
  |_-rw-r--r--    1 1000     1000          776 May 30  2021 note.txt

  - 22/tcp open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
  - 80/tcp open  http    Apache httpd 2.4.38 ((Debian))
- Service enumeration:
  - gobuster dir -u http://192.168.64.4 -w /usr/share/wordlists/rockyou.txt -t 40
  - Results:
    - /academy              (Status: 301) [Size: 314] [--> http://192.168.64.4/academy/]
   
  - Findings:
    - note.txt
    - └─$ cat note.txt
        Hello Heath !
        Grimmie has setup the test website for the new academy.
        I told him not to use the same password everywhere, he will change it ASAP.
        
        
        I couldn't create a user via the admin panel, so instead I inserted directly into the database with the following command:
        
        INSERT INTO `students` (`StudentRegno`, `studentPhoto`, `password`, `studentName`, `pincode`, `session`, `department`, `semester`, `cgpa`, `creationdate`, `updationDate`) VALUES
        ('10201321', '', 'cd73502828457d15655bbd7a63fb0bc8', 'Rum Ham', '777777', '', '', '', '7.60', '2021-05-29 14:36:56', '');
        
        The StudentRegno number is what you use for login.
        
        
        Le me know what you think of this open-source project, it's from 2020 so it should be secure... right ?
        We can always adapt it to our needs.
        
        -jdelta
Interesting Findings:
-10201321
-cd73502828457d15655bbd7a63fb0bc8

At this point, I saved the hash to hashes.txt and ran hash-cat on it:
-└─$ hashcat -m 0 hashes.txt /usr/share/wordlists/rockyou.txt      
-cd73502828457d15655bbd7a63fb0bc8:student
student is the password for the /academy page


## Exploitation
Explain how you approached exploiting the challenge:

-using the web browser, i accessed /academy and logged in using the login info



- Vulnerabilities or weaknesses identified
- Tools used (exploit frameworks, custom scripts, etc.)
- Step-by-step breakdown of the exploitation process
- Screenshots, code snippets, or command outputs to illustrate each step

## Privilege Escalation
If applicable, describe how you escalated privileges:
- Any misconfigurations or vulnerabilities identified
- Exploits or techniques used for privilege escalation
- Detailed explanation of how you gained higher-level access

## Flag Retrieval
Detail how you located and captured the flag(s):
- Method used to identify the flag location
- Exact flag(s) content and format
- Proof of flag retrieval (screenshot or flag content)

## Conclusion
Summarize your experience and takeaways from the challenge:
- Lessons learned during the CTF
- New skills or knowledge gained
- Challenges faced and how you overcame them
- Shoutouts or acknowledgments to teammates or resources

## Resources
List any external sources, tools, or references you used:
- Official documentation
- Write-ups from other participants (if referred)
- Tools or frameworks used

