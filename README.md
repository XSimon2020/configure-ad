# configure-ad

<p align="center">
<img width="559" alt="image" src="https://github.com/XSimon2020/azure-network-protocols/assets/111246513/52119721-42b1-4188-bfdc-9d4f2d7fe3a3">
</p>

<h1> Configuring Active Directory Within Azure Virtual Machines</h1>
This demonstration outlines a simulation for ticket lifecycles in osTicket.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure Virtual Machines

- Microsoft Remote Desktop

- Active Directory Domain Services

- Command Prompt

- PowerShell ISE

<h2>Operating Systems Used </h2>

- macOS

- Windows 10 Pro (21H2)

- Windows Server 2022 Datacenter: Azure Edition 

<h2>Steps</h2>

<p>
1) <b>Create the domain controller.</b><br/>
On portal.azure.com, search for virtual machines click to create a new one. When typing out the information for creating the vm, do it as it is shown in the screenshots besides the username and password that will be unique to you. Be sure to click the checkboxes for licensing. Click "Review + create" and then click "Create" after validation has passed.
<img width="888" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/06030cd4-289c-430e-8725-a7d57b9c208e">
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/587b1982-a5b2-4198-9d14-58e8a8ee990f">
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/9f787a73-a463-4d80-b560-ee9a1128479c">
<img width="887" alt="Screenshot 2024-04-09 at 12 11 59 PM" src="https://github.com/XSimon2020/configure-ad/assets/111246513/42b31dff-e9ce-437a-8306-4b26f612ccb0">
</p>
<br/>

<p>
2) <b>Create the client.</b><br/>
Once the previous vm, the domain controller, has been deployed, repeat the steps for creating the client with some slight differences as shown in the screenshots. Be sure the virtual network is the same as the domain controller for the client's virtual network in the "Networking' settings.  Click "Review + create" and then click "Create" after validation has passed as usual.
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/acc47d3b-72c9-4801-a85d-b2df758d6152">
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/56c8ab99-d8c5-4227-a985-05b1cc191634">
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/a9881f2b-5bd7-4435-8cba-3ce305fe92ed">
</p>
<br/>

<p>
3) <b>Log into the client.</b><br/>
Select for the client on the list of virtual machines then copy the public IP address the paste it onto Microsoft Remote Desktop. Double-click the added PC and type the username and password that was set up prior to deployment to log into the client.
<img width="885" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/a3514934-6864-4e06-8ebc-bc176052fe1a">
<img width="880" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/aa753c21-b04f-4489-b456-33904e5b3af8">
<img width="550" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/a21234ce-27f0-461e-a415-0ace45768ec7">
</p>
<br/>

<p>
4) <b>Configure a perpetual ping to the domain controller.</b><br/>
Within the client vm, type "cmd" on the search bar at the bottom left of the desktop to get to the command prompt. Open the command prompt and type "ping -t" with the private IP address of the domain controller. 
<img width="839" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/54d3b413-0f30-4c0a-b161-298ab7f621f7">
<img width="836" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/a76910da-d703-4baf-bdc3-633f13329d78">
</p>
<br/>

<p>
5) <b>Login into the domain controller.</b><br/>
Just like how you logged into the client, the same steps applies to log into the domain controller.
<img width="886" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/e9969a4d-19b8-4862-a1b7-690557cf4c53">
</p>
<br/>

<p>
6) <b>Allow ICMP traffic to get to the domain controller from the client.</b><br/>
Search for firewall on the search bar within the domain controller and click "Windows Defender Firewall with Advanced Security". Click "Inbound Rules" then click "Protocol" column repeatedly until you can see a row of ICMPv4 protocol settings. Click "Enable Rule" on the right side for two of the settings referring to echo requests. 
<img width="817" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/bac683e5-ce55-4301-88e6-0ffbcf395d39">
<img width="1781" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/6aef239c-17d0-40dc-923b-76d2e25aa13e">
</p>
<br/>

<p>
7) <b>Validate ICMP traffic is flowing from the client.</b><br/>
Back within the client vm, validate ICMP traffic is being sent to the domain controller then press "command+C" to stop the perpetual ping from occurring.
<img width="838" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/8eb75c78-5186-48f6-8d38-d2684fe127a4">
</p>
<br/>

<p>
8) <b>Validate ICMP traffic is flowing from the client.</b><br/>
Back within the client vm, validate ICMP traffic is being sent to the domain controller then press "command+C" to stop the perpetual ping from occurring.
<img width="838" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/8eb75c78-5186-48f6-8d38-d2684fe127a4">
</p>
<br/>

<p>
9) <b>Activate Active Directory Domain Services from the domain controller.</b><br/>
For future reference, it is good practice to avoid confusion and to ensure that you are in the correct vm you intend to be in by going to the command prompt and typing "whoami". Now on the server manager dashboard from within the domain controller vm, click "Add roles and features then go through each settings without tampering with the preconfigured settings. Click "Active Directory Domain Services" then click "Add Features" once you get to the necessary section. Keep going through the remaining sections while leaving each preconfiguration untouched then click "Install" once you get to it. Click "Close" once the installation is fully loaded. 
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/7d378af0-375c-41f3-ae9d-e430447b9ec5">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/a1ad6306-de08-455f-adf6-06d4ec567211">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/e96b7f24-0928-4ce0-9c37-1cd723a56ce4">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/8249686b-ac2d-4138-b499-1c16c16ac801">
</p>
<br/>

<p>
10) <b>Activate Active Directory Domain Services from the domain controller. (cont.)</b><br/>
Click the flag with the yellow triangular hazard symbol then click "Promote this server to a domain controller". On the "Deployment Configuration" section, configure the settings as it is show in the screenshot then click "Next >". Uncheck the box for creating DNS delegation in the "DNS Options" section. Wait for the NetBIOS domain name to load then click "Next >". Plow through the rest of the sections then wait for the prerequisites to be succesful in the "Prerequisite Check" section then click "Install". Once the install is complete, you will automatically get signed out of the domain controller.
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/501b0013-4f74-4ce3-97a2-eb58fbdec84b">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/b4187f4e-e227-4393-b8b2-cc59766a8c96">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/2c0abd77-719a-47d3-8dc2-d31cb0168321"> 
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/5e39e5c8-7980-420e-b164-c8933300f752">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/abc3f78f-9c40-4bf2-998c-4ade70c65d02">
<img width="818" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/4f520530-b3c8-47ff-b38a-f504d4266f8e">
</p>
<br/>

<p>
11) <b>Sign back into the domain controller with the new credentials.</b><br/>
Sign back into the domain controller on Microsoft Remote Desktop with the prefix as it is in the screenshot with your credentials
<img width="598" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/c152d3be-a723-4912-94d4-506bbf97df53">
</p>
<br/>

<p>
12) <b>Add organizational units.</b><br/>
Within the domain controller,go to "Active Directory Users and Computers" as shown in the screenshot. Two-finger click "mydomain.com" then click "Ogranizational Unit" to add a new organizational unit. You should have two of them with the names as shown in the screenshots.
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/d1116b76-9eb9-4bdf-bebe-9dd86d71e67a">
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/b3a40bb8-d5eb-433b-a0ce-c4fcfa20f5e3">
</p>
<br/>

<p>
13) <b>Create an admin account.</b><br/>
Two-finger click "mydomain.com again and click "User" to start creating an admin account. The information for the account should be filled in just how it is in the screenshots then click "Next >". Uncheck the checkbox for changing the password after each new login attempt and create a password for the admin account. Click "Next >" then "Finish" to finalize the acount set-up. Drag the admin account to the "_ADMINS" folder.
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/c27860f3-7c20-4c26-aa12-66b6337bdd31">
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/f7fae36c-ed71-4844-a7f8-28931e40b1cc">
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/b526c62c-2afa-40fd-b6d0-b73934d59e7a">
</p>
<br/>

<p>
14) <b>Add admin account to the necessary security group..</b><br/>
Two-finger click the admin account within the folder and click "Properties". Add the admin account to the "Domain Admins" securtiy group as shown in the screenshot. Click "Apply" then "OK".
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/5f1d00c6-2f33-42f7-9638-23125d025422">
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/551a641e-0f7f-44f1-9257-caacded2d846">
</p>
<br/>

<p>
15) <b>Log out of the domain controller and log back in with the admin account.</b><br/>
You can log out of the domain controller in the command prompt as shown in the screenshot. Log back into the domain controller with the admin account as shown in the screenshot.
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/707d1ba2-68c1-4837-97e4-8e37d1fe0ea7">
<img width="441" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/62eb9892-4c61-4588-ae81-93989fd998a8">
</p>
<br/>

<p>
16) <b>Change the dns server of the client as the domain controller.</b><br/>
Within Azure, change the client's dns server to be the domain controller by using its private IP address and then save it as shown in the screenshot. Be sure to restart the client.
<img width="881" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/3e0d145b-7e86-4165-a254-4d1fbf9f5393">
</p>
<br/>

<p>
17) <b>Log out of the domain controller and log back in with the admin account.</b><br/>
You can log out of the domain controller in the command prompt as shown in the screenshot. Log back into the domain controller with the admin account as shown in the screenshot.
<img width="874" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/707d1ba2-68c1-4837-97e4-8e37d1fe0ea7">
<img width="441" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/62eb9892-4c61-4588-ae81-93989fd998a8">
</p>
<br/>

<p>
18) <b>Join client to the domain.</b><br/>
Go back to the client still with the original account and go to the system settings as shown in the screenshot and click "Rename this PC (advanced)". Type out the domain name as shown in the screenshot then click "OK". On the pop type out the credentials of the admin account and validate that the client is now joined in the domain as shown.
<img width="916" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/e6529282-7b92-4cba-84d8-815eacff2f1d">
<img width="916" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/79449d5d-6c0e-48b8-9140-c0ae120127a0">
<img width="916" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/bd0eafff-9c39-4235-8dd3-76555a879b20">
<img width="916" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/437a36f6-fbda-41e4-a007-4ea236718f56">
</p>
<br/>

<p>
19) <b>Set up remote desktop for non-administrative users on the client.</b><br/>
Restart the client as required and log back in with the admin account. Allow domain users to access remote desktop within the necessary settings as shown in the screenshot.
<img width="916" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/e9d12b65-dcaf-464a-bb05-9cf62ba9f819">
</p>
<br/>

<p>
19) <b>Generate random user accounts.</b><br/>
Go back to the domain controller and open "Windows PowerShell ISE" while making sure you run it as an admin. Go to the link url: [Script](https://docs.google.com/document/d/1MTwfILCUvTNCdNnfktYKkEbJJwYm_TNVfGj-6oR0LYA/edit?usp=sharing) to copy the script and paste it onto Windows Powershell ISE as shown. Click the green play button to run the script and observe the thousands of random useer accounts being generated.
<img width="865" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/f176729c-13d8-44ab-b6f9-5d0aab49763d">
<img width="865" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/d4d028d6-d675-4009-a4bc-3b8dc75edae4">
<img width="865" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/66380f3d-da7a-4070-b1c8-5d0fe73ff5f3">
</p>
<br/>

<p>
20) <b>Log into the client with a random user account.</b><br/>
Still within the domain controller, go to the "_EMPLOYEES" folder "Active Directory Users and Computers" to see the list of user accounts already saved. Select one of the user accounts to use and log into the client with it. Be sure to log in properly with the correct password as shown in the screenshot. Notice when examining the script used to generate the accounts, they all use the same password. You should now be able to log into any random user account besides the user account used as an example as shown.
<img width="865" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/35fc2622-0758-4190-8d9f-8b6df4ec57af">
<img width="599" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/7a25f2b8-2bfc-4025-b110-b780e591b463">
<img width="1794" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/576ecae8-56d6-4af4-89e4-01d65e5ffd0f">
</p>
<br/>

<b>This marks the end of the demonstration.<b>























