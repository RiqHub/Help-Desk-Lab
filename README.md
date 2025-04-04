# <code style="color : red">!!!LAB STILL IN PROGRESS 01/25!!!</code>

![1test](https://github.com/user-attachments/assets/a828d4fd-8f7d-41ee-8b64-b5a21ea8d279)

<div style="text-align: center;">
  <h1>Help-Desk-Lab</h1>
</div>
I will be adding a ticketing system to troubleshoot the issues my "users" are having.  This lab will be used to simulate a Help desk environment. 


# The Set-up

![Rename Internet adapters ](https://github.com/user-attachments/assets/c658cf31-1434-4f68-866e-4b9dd00241a1)

<div align="center"><b>Once I got the Windows server set up in Oracle VB with 2 network adapters I renamed them to differentiate between my home internet and the internal internet that the Windows 10 machine would be pulling from.</b>
</div>

![Assigning IP for internat network ](https://github.com/user-attachments/assets/89fbd4dd-3460-4543-ae6d-13d606f9749d)

<div align="center"><b>Next, I assigned the internal adapter with a static address. I will use the server as a means to give internet access and IP address to the Windows 10 machine.</b>
</div>

![Installing Active directory ](https://github.com/user-attachments/assets/38a51063-cca7-4c4c-b60a-d356a4ebb420)
![dhcp scope](https://github.com/user-attachments/assets/ae1654c3-05f2-4c74-b50c-ca9b7e8a9a4f)
![Configuring NAT 2](https://github.com/user-attachments/assets/8ece7ecd-64ae-47af-8688-b523434e1342)


<div align="center"><b>After that, I equipped the server with the necessary services Active Directory, DHCP, and RAS/NAT</b>
</div>

# Ticket #1 (Password Lockout)
![closed ticket](https://github.com/user-attachments/assets/2fd81a55-0c5c-4335-bb25-ee9ab5017d90)

<div align="center"><b>Aacre has submitted a ticket stating that they have been locked out of their account due to too many wrong attempts. In the image you can see the priority has been set to high since the user is unable to access their computer. I have assigned myself the ticket and written comments to state what was done to fix the problem. Now we will walk through what was done. </b>
</div>

<br/>

<p align="center">
  <img src="https://github.com/user-attachments/assets/cef4ce63-4837-4963-879c-918ea23bf015" alt="Image 1" width="500">
  <img src="https://github.com/user-attachments/assets/4cdc4a78-eabe-4d79-ac8a-dbc06cac8197" alt="Image 2" width="500">
</p>

<div align="center"><b> It should be noted, these are the policies that I put in place for my network. For lab purposes I wont make them too complex but the most important policy right now is the lockout policy, with the max being 5 attempts. In the future we will tighten them up according to NIST SP 800-63B guidlines.</b>
</div>
<br/>

![new password](https://github.com/user-attachments/assets/b1618301-6545-413b-bccb-30ae83bf15af)
<div align="center"><b> Now, as a Help Desk associate we will go into Active Directory, find the user, right click their name, and reset password. This can also be done using the powershell command (Set-ADAccountPassword -Identity "username" -NewPassword (ConvertTo-SecureString "NewPassword123!" -AsPlainText -Force)). The users account is now unlocked and password is rest. I dont have the setting enabled but the next time they log in they should be prompted to create a new password. </b>
</div>
<br/>
<br/>

# Ticket #2 (Creating Oranizations,Network shares, and Permissions)
![Screenshot 2025-01-11 064405](https://github.com/user-attachments/assets/fe4057f4-cf5c-4a0e-b874-cdd05a6b442c)
<br/>
<div align="center"><b> For this ticket the CEO is asking for users to be separated in departments and for each department to have thier own folder that no other department can get into. This is how well do it.  </b>
<br/>


![Creating OUS](https://github.com/user-attachments/assets/e0dbd29e-eac9-48f1-8938-b26669f615e9)
<br/>
<div align="center"><b> First, I created 4 Organizational units (Sales, Finaince, HR, and IT). </b>
<br/>

![Security Groups](https://github.com/user-attachments/assets/b374377d-a6f2-48b5-8771-e156ac7416e1)
<br/>
<div align="center"><b>Then for each OU a security group is created </b>
<br/>

![Add users to sec groups](https://github.com/user-attachments/assets/e7cd9011-2259-4302-811d-7342e1fda1c2)
<br/>
<div align="center"><b>Once each group is created I selected users for each department.  </b>
<br/>

![Create share](https://github.com/user-attachments/assets/b2b37d8b-bbf2-47fb-ad93-e129a96655f1)
<br/>
<div align="center"><b>Next, I went into the server manager > Shared folders > Create new share for each department.  </b>
<br/>

![Set permissions](https://github.com/user-attachments/assets/b42bec9f-e29c-4d99-a8bf-71e64d51f90a)
<br/>
<div align="center"><b>As requested, only user from designated departments can access their respective folders.  </b>
<br/>

![access denied](https://github.com/user-attachments/assets/d75cb499-a6f1-43ce-8d08-28647620b7cf)
<br/>
<div align="center"><b>Finally, I went into aacre account to test these permissions and as you can see I am not able to get into the IT share since Aacre is a SALES associate.  </b>
<br/>






