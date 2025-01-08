
![1test](https://github.com/user-attachments/assets/a828d4fd-8f7d-41ee-8b64-b5a21ea8d279)

<div style="text-align: center;">
  <h1>Help-Desk-Lab</h1>
</div>
Credit to Josh Madakor for helping with the set up of this lab. However I will be taking it a step further by adding a ticketing system to troubleshoot the issues my "users" are having.  This lab will be used to simulate a Help desk environment. 


# The Set-up

![Rename Internet adapters ](https://github.com/user-attachments/assets/c658cf31-1434-4f68-866e-4b9dd00241a1)

<div align="center"><b>Once I got the Windows server set up in Orical VB with 2 network adapters I renamed them to differentiate between my home internet and the internal internet that the Windows 10 machine would be pulling from.</b>
</div>

![Assigning IP for internat network ](https://github.com/user-attachments/assets/89fbd4dd-3460-4543-ae6d-13d606f9749d)

<div align="center"><b>Next, I assigned the internal adapter with a static address. I will use the server as a means to give internet access and IP address to the Windows 10 machine.</b>
</div>

![Installing Active directory ](https://github.com/user-attachments/assets/38a51063-cca7-4c4c-b60a-d356a4ebb420)
![dhcp scope](https://github.com/user-attachments/assets/ae1654c3-05f2-4c74-b50c-ca9b7e8a9a4f)
![Configuring NAT 2](https://github.com/user-attachments/assets/8ece7ecd-64ae-47af-8688-b523434e1342)


<div align="center"><b>After that, I equipped the server with the necessary features Active Directory, DHCP, and a NAT</b>
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

