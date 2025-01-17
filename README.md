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
    - You can name this new role whatever would like (I chose Supreme Admin 👑)

![image](https://github.com/user-attachments/assets/c04a37ce-5027-4a99-aaa8-1e9f3c4e1943)

- Navigate to the "Permissions" tab and as the name suggests, assign all permissions to this new role.
![image](https://github.com/user-attachments/assets/a4964fff-6538-4670-9d45-20935ed80c75)
![image](https://github.com/user-attachments/assets/05fb9944-84ce-41ed-a38a-4dfc24f4e22a)
![image](https://github.com/user-attachments/assets/92791b8e-ed65-469a-bc13-6d89dd908688)

- Finally, click "Add role".
  - Feel free to continue adding roles if you so desire.

<h2>
STEP 4: Now configure some Departments that your agents will be placed into. 
</h2>

<p>

 - (From the admin panel) Select the "Agents" tab, then the "Departments" tab.
 - Select "Add New Department"
 - Name this new Department "System Administrators"
   - Select "Create Dept"  

![image](https://github.com/user-attachments/assets/651aa352-4f5a-4232-96a4-e252d61ac148)

</p>

<h2>
 STEP 5: Why should you be restricted to the strict confines of departments? Now configure "Teams" that allow you to group your help desk agents regardless of their departments...Avengers Assemble!⚡
</h2>

<p>

 - (From the admin panel) Select the "Agents" tab, then the "Teams" tab.
 - Select "Add New Team"
   - Name this new team "Level II Support"
 - Select "Create Team" 

![image](https://github.com/user-attachments/assets/a61f0d45-5c80-4373-9904-5856aa213e10)

</p>

<h2>

 STEP 6: Allow anyone to create tickets as an end user of the ticketing system.
</h2>

<p>

 - (From the admin panel) Go to the "Settings" tab, then select the "Users" tab
 - Ensure the "Registration Required: Require registration and login to create tickets" field (under Authentication Settings) is unchecked.

![image](https://github.com/user-attachments/assets/e92ed9ad-a614-4298-94c0-6a4a5fbb5a38)

- Save the changes.
</p>

<h2>

 STEP 7: Your Help Desk is currently a Ghost Town. It is time to finally configure some Help Desk Agents to work these tickets!
</h2>

<p>

 - (From the admin panel) Select the "Agents" tab, then select the "Agents" tab below it.
 - Select "Add New Agent"
 - Within the "Account" tab
   - You can name your agent whatever you like
   - Assign an email address of your choosing
     - NOTE: the email username may be whatever you like but the email's domain must be a recognized email domain (eg. gmail.com or outlook.com) 
   - Assign a usernamer of your choosing
   - Check the "Administrator" field underneath "Status and Settings" as well
     - This will give this agent access to the Admin panel.  
   - Set the password for this agent by selecting the "Set Password" button beside the username.


![image](https://github.com/user-attachments/assets/a01d610f-d8f2-472d-ab44-cfeaa78b6d6f)


 - Uncheck "Send the agent a password reset email"
   - Now manually assign the agent a password
   - Uncheck "Require password change at next login"
   - Click "Set"

![image](https://github.com/user-attachments/assets/3819b416-27b4-4568-83ad-c0e1038380f6)

  - Now navigate to the "Access" tab
  - Assign this agent to the "System Administrators" department as its primary department.
    - And simultaneously assign the "Supreme Admin" (or whatever you named it) role to this agent.
    - Check the "Fall back to primary role on assignments" field for this agent.
      - This will enable the agent to assume their "Supreme Admin" role even if assigned a ticket or task that is outside their primary department or
         extended access department, instead of being granted "read only" access. 

   - Optionally, you may also grant this agent "Extended Access" and place them in a secondary department (I chose Support) and grant them the Expanded 
     Access role for tickets assigned to that department. 

   ![image](https://github.com/user-attachments/assets/8c0d5d20-f404-4dbb-b2e7-f9edda5eb51b)

   - The default permissions assigned to this agent (can be viewed in the "Permissions tab") will suffice for the purposes of this lab.
   - Lastly, you can also add this agent to a specific team if you so desire via the "Teams" tab.
     - I chose to add this agent to the "Level I Support" team
    
 ![image](https://github.com/user-attachments/assets/339aa9e7-1bdc-4195-b1cd-248a3dccaf1a)

   - Now finally, click "Create" and you will have successfully provisioned your first help desk agent.
</p>
<b>
 
</b>

<p>

 - We will create another help desk agent and to verify that the first agent was provisioned accurately, let us kill two birds with one stone...figuratively of course. 🐦
   - Log out of your current admin agent's account and login as the new administrator agent that you just created.

![image](https://github.com/user-attachments/assets/8c8115bf-0064-4459-929f-a3d32e6d84a7)

   
</p>

