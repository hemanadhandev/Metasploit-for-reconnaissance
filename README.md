# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands
## EXECUTION STEPS AND ITS OUTPUT
Find out the ip address of the attackers system
### OUTPUT:
![WhatsApp Image 2024-04-16 at 11 01 32 AM](https://github.com/Vinothini1711/Echoserver/assets/144300204/ebeb5637-deff-4b72-8bf0-3bfe471258cd)

Invoke msfconsole:
![Screenshot 2024-04-16 110721](https://github.com/Vinothini1711/Echoserver/assets/144300204/a0875db3-fd18-4690-ad66-be9498a4abc4)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![Screenshot 2024-04-16 132316](https://github.com/Vinothini1711/Echoserver/assets/144300204/21c94bf6-d7f3-4a94-823e-f39fffd7e7de)

#### Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000
### OUTPUT:
![Screenshot 2024-04-16 135424](https://github.com/Vinothini1711/Echoserver/assets/144300204/ffaf2ae4-1cfe-4bc2-acac-0c6b0655f004)
step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.
scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
### OUTPUT:
![Screenshot 2024-04-16 131743](https://github.com/Vinothini1711/Echoserver/assets/144300204/c269f35c-9557-4414-a327-5bd814cc66d4)
Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
### OUTPUT:
![Screenshot 2024-04-16 133518](https://github.com/Vinothini1711/Echoserver/assets/144300204/21d4867d-a7b7-4347-8ddd-cf7d3349566b)

Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
![Screenshot 2024-04-16 134336](https://github.com/Vinothini1711/Echoserver/assets/144300204/75464033-d029-41e1-b72d-82cf071276c0)
The info command provides information regarding a module or platform,
### OUTPUT
![Screenshot 2024-04-16 134439](https://github.com/Vinothini1711/Echoserver/assets/144300204/0250ac1c-41ae-4777-b1d4-c7c2a56188f3)
Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
#### MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
![Screenshot 2024-04-16 134632](https://github.com/Vinothini1711/Echoserver/assets/144300204/754bb0f4-3689-4c4c-b443-e08795d9067f)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
![Screenshot 2024-04-16 135941](https://github.com/Vinothini1711/Echoserver/assets/144300204/812fa80b-937d-4031-aac2-6c541e11a33c)
use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11 Or: use auxiliary/scanner/mysql/mysql_version
![Screenshot 2024-04-16 140022](https://github.com/Vinothini1711/Echoserver/assets/144300204/7137d483-7b44-450f-ac82-ad2dbe539e76)
Use the set rhosts command to set the parameter and run the module, as follows:
![Screenshot 2024-04-16 140055](https://github.com/Vinothini1711/Echoserver/assets/144300204/24c4647e-9715-4418-b50a-a8a8330adeb3)
After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
![Screenshot 2024-04-16 140131](https://github.com/Vinothini1711/Echoserver/assets/144300204/3bb3d9cc-b688-4c59-a9a8-63327ba4f2f5)
set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
![msf6](https://github.com/Vinothini1711/Echoserver/assets/144300204/518c2b02-ba4e-4f9f-8c4a-cc0971468a8d)
## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
