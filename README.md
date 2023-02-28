<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>


<h1>Active Directory Configuration</h1>
In this tutorial, we are configuring and playing around with Active Directory. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022

<!-- 
<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4
This is a comment -->
<h2>Actions and Observations</h2>


<p>
Log in into DC-1 and go to server manager, Click on “Add roles and features”, click next until server roles, in there, select “Active Directory Domain Services”; finish the installation clicking next and finally install. 
Click on the flag with the yellow sign at the top right (see picture below), then click “Promote this server to a domain controller”. For Root domain name you can use “mydomain.com” or whatever you want. Then, set a password, and keep clicking next and install. After installation you should be kicked out of the session, re-login but this time for the username use: “mydomain.com\XXX” where XXX is the username given for DC-1 when created. 
</p>
<p>
<img src="https://i.imgur.com/p2v1HDM.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Create an Admin and Normal User Account in AD
Inside DC-1, in server manager go to Tools > Active Directory Users and Computers. Right click in mydomain.com > New > Organizational Unit, let’s create one call _EMPLOYEES, and another one call _ADMINS.  
Right click _ADMINS > New > User, create a user name (jane doe in this example) as seen below. Set the password and uncheck change password next log in (normally we wouldn’t do this but this is just practice). Click on the new user (jane doe in this case) > Properties > Member Of > Add.. enter domain admin then click check name and OK. To test this worked, let’s log in as the new user jane doe, using “mydomain.com\jane_admin” as the username to check if it works. 
</p>
<p>
<img src="https://i.imgur.com/4bqlqeI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Now we are setting the DNS of Client-1 to point to DC-1 so it works as an DNS server. First of all, inside Azure, go to VM Client-1, select networking, then click on “Network interface” > DSN server. Click on Custom, then enter the IP that you gave DC-1 in the preview steps. Finally go back to Client-1 VM and restart it. 
Now log in into Client-1, then right click window’s logo and select Systems > Rename This PC (Advance) > Change… > Domain, then type domain.com ; when asked for username and password use: “mydomain.com\jane_admin” and its password. 
</p>
<p>
<img src="https://i.imgur.com/byrbWhZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />


<p>
Log into Client-1 using mydomain.com\jane_admin and its password. Once inside, go to system > Remote desktop > “Select users that can remotely access this PC” > Add.. 
Then type “domain users”, click on Check Names and OK twice. 
</p>
<p>
<img src="https://i.imgur.com/vHbIYcN.jpg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
Crate user and log in with that user 

Login to DC-1 as jane_admin, then go to active directory users and computers, go to users, right click then go to New > User, Create user with new Name, Last Name, Login Name, and Password. If something need to be change with that user, right click on its name and select properties. Now that you created a new user, try to log in with that new user name and its password (remember to use as name: mydomain.com\NewUser)
<p>

</p>
<br />

