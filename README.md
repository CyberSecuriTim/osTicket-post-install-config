<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>

This tutorial outlines the post-installation configuration of the open-source help desk ticketing system osTicket.<br />

<p>
 
  - NOTE: As the name suggests, this project requires a successful installation of osTicket to have already been completed.
    - For a step-by-step procedure detailing how to install this software (and all its dependencies) feel free to take a look at my other github repository [here](https://github.com/Cybersecuritim/osticket-installation).
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Post-Install Configuration Objectives</h2>

- Configure "Roles"
- Configure "Departments"
- Configure "Teams"
- Enable anyone to create tickets 
- Configure "Agents" (i.e. help desk employees)
- Configure "Users" (i.e. customers)
- Configure "SLA" (service level agreements)
- Configure "Help Topics" 

<h2>Configuration Steps</h2>

<h2> 
 STEP 1: Access your created Windows 10 virtual machine (which has osTicket currently installed on it) hosted in Azure by establishing a remote desktop connection via its public IP address using your preferred Remote Desktop client.
</h2>

<p>
  
 - I used the Windows Remote Desktop Connection app during this lab.
 
 ![image](https://github.com/user-attachments/assets/717a484f-161d-4a11-8c7f-fd1752d2b202)
</p>

<h2>
 STEP 2: Access the help desk login page using this link within the Virtual Machine (http://localhost/osTicket/scp/login.php).
</h2>

- Be sure to login using the administrator credentials that were assigned during the osTicket basic installation process towards the end of the previous lab.

![image](https://github.com/user-attachments/assets/4be6480e-345e-4bd0-aa4e-602f708f2595)

![image](https://github.com/user-attachments/assets/23bdc905-2b23-4da0-a7bf-2df6cc415261)

- NOTE: Upon login, if you are not automatically brought to the admin panel (and instead in the agent panel), simply click "Admin Panel" link in the top right corner to be redirected to the admin panel in order to complete the outlined configuration objectives. 

![image](https://github.com/user-attachments/assets/67d2c382-fed3-415e-bd1b-3a97d2f9b241)

<h2>
STEP 3: It seems your help desk agents are hungry. Time to configure some roles for them.🍞
</h2>

 <p>

  - (From the admin panel) Select the "Agents" tab then select the "Roles" Tab.
  - Select "Add New Role"
    - Name this new role whatever would like (I chose Supreme Admin 👑)

![image](https://github.com/user-attachments/assets/c04a37ce-5027-4a99-aaa8-1e9f3c4e1943)

- Navigate to the "Permissions" tab and as the name suggests, assign all permissions to this new role.
![image](https://github.com/user-attachments/assets/a4964fff-6538-4670-9d45-20935ed80c75)
![image](https://github.com/user-attachments/assets/05fb9944-84ce-41ed-a38a-4dfc24f4e22a)
![image](https://github.com/user-attachments/assets/92791b8e-ed65-469a-bc13-6d89dd908688)







    
 </p>
