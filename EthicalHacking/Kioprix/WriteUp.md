# Kioptrix (192.168.64.3) CTF Write-Up

**Author:** Alan Garcia  
**Date:** 8/31/23

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
CTF prepared by TCM https://academy.tcm-sec.com/

## Challenge Overview
This CTF had a difficulty of easy

## Initial Reconnaissance
Detail the information-gathering phase:
- IP : (192.168.64.3)
- NMAP revealed the following ports opened:

nmap -A -p- -T4 192.168.64.3  
Starting Nmap 7.93 ( https://nmap.org ) at 2023-08-24 01:16 MST
Nmap scan report for 192.168.64.3
Host is up (0.00087s latency).
Not shown: 65529 closed tcp ports (conn-refused)
PORT      STATE SERVICE     VERSION
22/tcp    open  ssh         OpenSSH 2.9p2 (protocol 1.99)
|_sshv1: Server supports SSHv1
| ssh-hostkey: 
|   1024 b8746cdbfd8be666e92a2bdf5e6f6486 (RSA1)
|   1024 8f8e5b81ed21abc180e157a33c85c471 (DSA)
|_  1024 ed4ea94a0614ff1514ceda3a80dbe281 (RSA)
80/tcp    open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_http-title: Test Page for the Apache Web Server on Red Hat Linux
| http-methods: 
|_  Potentially risky methods: TRACE
111/tcp   open  rpcbind     2 (RPC #100000)
| rpcinfo: 
|   program version    port/proto  service
|   100000  2            111/tcp   rpcbind
|   100000  2            111/udp   rpcbind
|   100024  1          32768/tcp   status
|_  100024  1          32768/udp   status
139/tcp   open  netbios-ssn Samba smbd (workgroup: MYGROUP)
443/tcp   open  ssl/https   Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
| ssl-cert: Subject: commonName=localhost.localdomain/organizationName=SomeOrganization/stateOrProvinceName=SomeState/countryName=--
| Not valid before: 2009-09-26T09:32:06
|_Not valid after:  2010-09-26T09:32:06
|_http-server-header: Apache/1.3.20 (Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b
|_ssl-date: 2023-08-24T12:16:24+00:00; +3h59m59s from scanner time.
| sslv2: 
|   SSLv2 supported
|   ciphers: 
|     SSL2_DES_64_CBC_WITH_MD5
|     SSL2_DES_192_EDE3_CBC_WITH_MD5
|     SSL2_RC4_128_EXPORT40_WITH_MD5
|     SSL2_RC4_64_WITH_MD5
|     SSL2_RC2_128_CBC_WITH_MD5
|     SSL2_RC2_128_CBC_EXPORT40_WITH_MD5
|_    SSL2_RC4_128_WITH_MD5
|_http-title: 400 Bad Request
32768/tcp open  status      1 (RPC #100024)

Host script results:
|_clock-skew: 3h59m58s
|_smb2-time: Protocol negotiation failed (SMB2)
|_nbstat: NetBIOS name: KIOPTRIX, NetBIOS user: <unknown>, NetBIOS MAC: 000000000000 (Xerox)

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 23.32 seconds

-139
  Interesting Items:
  SMB
  Unix (Samba 2.2.1a)
  
  Could anonymously connect to IPC with smbclient, but not Admin
  139- Potentially Vulnerable to:
  https://www.rapid7.com/db/modules/exploit/linux/samba/trans2open/
  https://www.exploit-db.com/exploits/10
  https://www.exploit-db.com/exploits/7

-80/443
  Interesting items:
  80/tcp    open  http        Apache httpd 1.3.20 ((Unix)  (Red-Hat/Linux) mod_ssl/2.8.4 OpenSSL/0.9.6b)

  Potentially Vulnerable to:
  mod_ssl/2.8.4 - mod_ssl 2.8.7 and lower are vulnerable to a remote buffer overflow which may allow a remote shell. 
  http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2002-0082, OSVDB-756.
  https://github.com/heltonWernik/OpenLuck
-22
  SSH
   OpenSSH 2.9p2 (protocol 1.99)
   
   22- Possible Vulnerabilities
   https://www.exploit-db.com/exploits/21402
 
- Service enumeration (nmap, netcat, etc.)
- Analysis of open ports and running services
- Any initial clues or data found during this phase

## Exploitation

-The SMB (Samba) exploit:

I quickly found that the service running under port 139 (samba) was seriously vulnerable and decided to attack that. (Note: Samba is very similar to FTP / NFS, it’s basically a file-sharing system between Linux and Windows).

Searched for Samba 2.2.1a exploit on metasploit:

Explain how you approached exploiting the challenge:
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
