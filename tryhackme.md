
CC: Pen Testing WriteUp – TryHackMe


In this article, I tried to prepare a write-up for the “CC: Pen Testing” room on tryhackme.

[Task 1] Introduction
The idea behind this room is to provide an introduction to various tools and concepts commonly encountered in penetration testing.

#1 Read the above.
ANSWER: No answer needed

[Task 2] [Section 1 – Network Utilities] – nmap
nmap is one of the most important tools for pentesting.

#1 What does nmap stand for?
ANSWER: Network Mapper

#2 How do you specify which port(s) to scan?
ANSWER: -p

#3 How do you do a “ping scan”(just tests if the host(s) is up)?
ANSWER: -sn

#4 What is the flag for a UDP scan? 
ANSWER: -sU

#5 How do you run default scripts?
ANSWER: -sC

#6 How do you enable “aggressive mode”?
ANSWER: -A

#7 What flag enables OS detection
ANSWER: -O

#8 How do you get the versions of services running on the target machine
ANSWER: -sV

#9 Deploy the machine
After deploy the machine, you can run this nmap command:

1
nmap -A -sC -sV -O <IP Address>
You can see my nmap result. All answer can be seen.


ANSWER: No answer needed

#10 How many ports are open on the machine? 
ANSWER: 1

#11 What service is running on the machine?  
ANSWER: Apache

#12 What is the version of the service?
ANSWER: 2.4.18

#13 What is the output of the http-title script(included in default scripts)
ANSWER: Apache2 Ubuntu Default Page: It Works

[Task 3] [Section 1 – Network Utilities] – Netcat
You can see netcat help page:


#1 How do you listen for connections?
ANSWER: -l

#2 How do you enable verbose mode(allows you to see who connected to you)?
ANSWER: -v

#3 How do you specify a port to listen on
ANSWER: -p

#4 How do you specify which program to execute after you connect to a host(One of the most infamous)?
ANSWER: -e

#5 How do you connect to udp ports
ANSWER: -u

[Task 4] [Section 2 – Web Enumeration] – gobuster
You can see gobuster help page:


#1 How do you specify directory/file brute forcing mode?
ANSWER: dir

#2 How do you specify dns bruteforcing mode? 
ANSWER: dns

#3 What flag sets extensions to be used?
ANSWER: -x

#4 What flag sets a wordlist to be used?
ANSWER: -w

#5 How do you set the Username for basic authentication?
ANSWER: -U

#6 How do you set the password for basic authentication?
ANSWER: -P

#7 How do you set which status codes gobuster will interpret as valid?
ANSWER: -s

#8 How do you skip ssl certificate verification?
ANSWER: -k

#9 How do you specify a User-Agent?
ANSWER: -a

#10 How do you specify a HTTP header?
ANSWER: -H

#11 What flag sets the URL to bruteforce?
ANSWER: -u

#12 Deploy the machine
After deploy the machine, you can run this command:

1
gobuster dir -u http://<Machine IP> -w /usr/share/wordlists/dirb/common.txt -t 64

#13 What is the name of the hidden directory
You can see the answer above picture.

ANSWER: secret

#14 What is the name of the hidden file with the extension xxa
You can see my answer:


ANSWER: password

[Task 5] [Section 2 – Web Enumeration] – nikto
You can use nikto help page:


#1 How do you specify which host to use? 
ANSWER: -h

#2 What flag disables ssl?
ANSWER: -nossl

#3 How do you force ssl?
ANSWER: -ssl

#4 How do you specify authentication(username + pass)?
ANSWER: -id

#5 How do you select which plugin to use?
ANSWER: -plugins

#6 Which plugin checks if you can enumerate apache users? 
You have to run this command:

1
nikto --list-plugins
Then you can show the answer:


ANSWER: apacheusers

#7 How do you update the plugin list ?
ANSWER: -update

#8 How do you list all possible plugins to use?
ANSWER: –list-plugins

[Task 6] [Section 3 – Metasploit]: Intro
#1
ANSWER: No answer needed

[Task 7] [Section 3 Metasploit]: Setting Up
#1 What command allows you to search modules?
ANSWER: search

#2 How do you select a module? 
ANSWER: use

#3 How do you display information about a specific module?
ANSWER: info

#4 How do you list options that you can set?
ANSWER: options

#5 What command lets you view advanced options for a specific module?
ANSWER: advanced

#6 How do you show options in a specific category
ANSWER: show

[Task 8] [Section 3 – Metasploit]: – Selecting a module
This task will take you through selecting and setting options for one of the most popular metasploit modules “eternalblue“. All basic commands that could be run before selecting a module can also be done while a module is selected.

#1 How do you select the eternalblue module?

ANSWER: use exploit/windows/smb/ms17_010_eternalblue

#2 What option allows you to select the target host(s)?

ANSWER: RHOSTS

#3 How do you set the target port?
ANSWER: RPORT

#4 What command allows you to set options?
ANSWER: set

#5 How would you set SMBPass to “username”?
ANSWER: set SMBPass username

#6 How would you set the SMBUser to “password”?
ANSWER: set SMBUser password

#7 What option sets the architecture to be exploited?
ANSWER: arch

#8 What option sets the payload to be sent to the target machine?
ANSWER: payload

#9 Once you’ve finished setting all the required options, how do you run the exploit?
ANSWER: exploit

#10 What flag do you set if you want the exploit to run in the background?
ANSWER: -j

#11 How do you list all current sessions?
ANSWER: sessions

#12 What flag allows you to go into interactive mode with a session?
ANSWER: -i

[Task 9] [Section 3 – Metasploit]: meterpreter
#1 What command allows you to download files from the machine?
ANSWER: download

#2 What command allows you to upload files to the machine?
ANSWER: upload

#3 How do you list all running processes?
ANSWER: ps

#4 How do you change processes on the victim host?
ANSWER: migrate

#5 What command lists files in the current directory on the remote machine?
ANSWER: ls

#6 How do you execute a command on the remote host?
ANSWER: execute

#7 What command starts an interactive shell on the remote host?
ANSWER: shell

#8 How do you find files on the target host?
ANSWER: search

#9 How do you get the output of a file on the remote host?
ANSWER: cat

#10 How do you put a meterpreter shell into “background mode”
ANSWER: background

[Task 10] [Section 3 – Metasploit]: Final Walkthrough
Let’s select the “exploit/multi/http/nostromo_code_exec” module and list the options:


#1 Select the module that needs to be exploited
ANSWER: use exploit/multi/http/nostromo_code_exec

#2 What variable do you need to set, to select the remote host
ANSWER: rhosts

#3 How do you set the port to 80
ANSWER: set rport 80

#4 How do you set listening address(Your machine)
ANSWER: lhost

#5 Exploit the machine!
Let’s set the parameters then exploit this machine 🙂


#6 What is the name of the secret directory in the /var/nostromo/htdocs directory?
You can do like me:


ANSWER: s3cretd1r

#7 What are the contents of the file inside of the directory?

ANSWER: Woohoo!

[Task 11] [Section 4 – Hash Cracking]: Intro
#1
ANSWER: No answer needed

[Task 12] [Section 4 – Hash Cracking]: Salting and Formatting
#1
ANSWER: No answer needed

[Task 13] [Section 4 – Hash Cracking]: hashcat

#1 What flag sets the mode.
ANSWER: -m

#2 What flag sets the “attack mode”
ANSWER: -a

#3 What is the attack mode number for Brute-force

ANSWER: 3

#4 What is the mode number for SHA3-512  

ANSWER: 17600

#5 Crack This Hash:56ab24c15b72a457069c5ea42fcfc640
You can use this web site.


ANSWER: happy

#6 Crack this hash: 4bc9ae2b9236c2ad02d81491dcb51d5f
You can use this web site.


ANSWER: nootnoot

[Task 14] [Section 4 – Hash Cracking]: John The Ripper
#1 What flag let’s you specify which wordlist to use?
ANSWER: –wordlist

#2 What flag lets you specify which hash format(Ex: MD5,SHA1 etc.) to use?  
ANSWER: –format

#3 How do you specify which rule to use?
ANSWER: –rules

#4 Crack this hash: 5d41402abc4b2a76b9719d911017c592
You can use this command in “/root/Desktop” directory.


ANSWER: hello

#5 Crack this hash: 5baa61e4c9b93f3f0682250b6cf8331b7ee68fd8
You can use this command in “/root/Desktop” directory.


ANSWER: password

[Task 15] [Section 5 – SQL Injection]: Intro
#1
ANSWER: No answer needed

[Task 16] [Section 5 – SQL Injection]: sqlmap
Sqlmap is arguably the most popular automated SQL injection tool out there.

You can see the sqlmap help menü:


#1 How do you specify which url to check?
You can see the answer above the picture.

ANSWER: -u

#2 What about which google dork to use?
You can see the answer above the picture

ANSWER: -g

#3 How do you select(lol) which parameter to use?

ANSWER: -p

#4 What flag sets which database is in the target host’s backend?
You can see the answer previous picture 🙂

ANSWER: –dbms

#5 How do you select the level of depth sqlmap should use
ANSWER: –level

#6 How do you dump the table entries of the database?

ANSWER: –dump

#7 Which flag sets which db to enumerate?
You can see the answer previous picture 🙂

ANSWER: -D

#8 Which flag sets which table to enumerate?
You can see the answer previous picture 🙂

ANSWER: -T

#9 Which flag sets which column to enumerate?
You can see the answer previous picture 🙂

ANSWER: -C

#10 How do you ask sqlmap to try to get an interactive os-shell?

ANSWER: –os-shell

#11 What flag dumps all data from every table
ANSWER: –dump-all

[Task 17] [Section 5 – SQL Injection]: A Note on Manual SQL Injection
#1
ANSWER: No answer needed

[Task 18] [Section 5 – SQL Injection]: Vulnerable Web Application
To demonstrate how to use sqlmap to check for vulnerabilities and dump table data, I will be walking you through an example web app. Deploy the machine and let’s get started!

#1 Set the url to the machine ip, and run the command
ANSWER: No answer needed

#2 How many types of sqli is the site vulnerable too?
ANSWER: 3

#3 Dump the database.
You can use this command: You should answer all question with “Y”.


ANSWER: No answer needed

#4 What is the name of the database? 

ANSWER: tests

#5 How many tables are in the database?

Their names are “msg” and “flag”.

ANSWER: 2

#6 What is the value of the flag?

ANSWER: found_me

[Task 19] [Section 6 – Samba]: Intro
#1
ANSWER: No answer needed

[Task 20] [Section 6 – Samba]: smbmap
You can use the help menu.


#1 How do you set the username to authenticate with?
ANSWER: -u

#2 What about the password?    
ANSWER: -p

#3 How do you set the host?
ANSWER: -H

#4 What flag runs a command on the server?
ANSWER: -x

#5 How do you specify the share to enumerate?
ANSWER: -s

#6 How do you set which domain to enumerate?
ANSWER: -d

#7 What flag downloads a file?
ANSWER: –download

#8 What about uploading one?
ANSWER: –upload

#9 Given the username “admin”, the password “password”, and the ip “10.10.10.10”, how would you run ipconfig on that machine
ANSWER: smbmap -u “admin” -p “password” -H 10.10.10.10 -x “ipconfig”

[Task 21] [Section 6 – Samba]: smbclient
You can use the help menu.


#1 How do you specify which domain(workgroup) to use when connecting to the host?
ANSWER: -w

#2 How do you specify the ip address of the host?
ANSWER: -I

#3 How do you run the command “ipconfig” on the target machine?
ANSWER: -c “ipconfig”

#4 How do you specify the username to authenticate with?
ANSWER: -U

#5 How do you specify the password to authenticate with?
ANSWER: -P

#6 What flag is set to tell smbclient to not use a password?
ANSWER: -N

#7 While in the interactive prompt, how would you download the file test, assuming it was in the current directory?
ANSWER: get test

#8 In the interactive prompt, how would you upload your /etc/hosts file
ANSWER: put /etc/hosts

[Task 22] [Section 6 – Samba]: A note about impacket
#1
ANSWER: No answer needed

[Task 23] [Miscellaneous]: A note on privilege escalation
#1
ANSWER: No answer needed

Task 24 [Section 7 – Final Exam]: Good Luck 😀
First, you have to use search the directory with “gobuster”. I used the “directory-list-2.3-medium.txt” wordlist.


I found the “/secret” directory. Then again I searched the this directory with “.txt, .php, .html” extensions.


I found the “secret.txt” directory.


I got some information. I tried to crack the hash value.


Then I connected with ssh.

User name: nyan

Password: nyan


#1 What is the user.txt
ANSWER: supernootnoot

#2 What is the root.txt

ANSWER: congratulations!!!!

So far, I have tried to explain the solutions of the questions as detailed as I can. I hope it helped you. See you in my next write-up.


tryhackme

CC:PenTesting, hash, John, NMAP, smbclient, smbmap, sqlmap, tryhackme, writeup
