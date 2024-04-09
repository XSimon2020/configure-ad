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
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/9f787a73-a463-4d80-b560-ee9a1128479c
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
Within the client vm, type "cmd" on the search bar at the bottom left of the desktop to get to the command prompt.
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/acc47d3b-72c9-4801-a85d-b2df758d6152">
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/56c8ab99-d8c5-4227-a985-05b1cc191634">
<img width="887" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/a9881f2b-5bd7-4435-8cba-3ce305fe92ed">
<img width="839" alt="image" src="https://github.com/XSimon2020/configure-ad/assets/111246513/54d3b413-0f30-4c0a-b161-298ab7f621f7">

</p>
<br/>




