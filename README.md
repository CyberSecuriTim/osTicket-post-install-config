<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Post-Install Configuration</h1>

This tutorial outlines the post-installation configuration of the open-source help desk ticketing system osTicket.<br />

<p>
 
  - NOTE: As the name suggests, this project requires a successful installation of osTicket to have already been completed.
    - For a step-by-step procedure detailing how to install this software (and all its dependencies) feel free to take a look at my other GitHub repository [here](https://github.com/Cybersecuritim/osticket-installation).
</p>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10 (22H2)

<h2>Post-Install Configuration Objectives</h2>

- Configure "Roles"
- Configure "Departments"
- Configure "Teams"
- Enable anyone to create tickets 
- Configure "Agents" (i.e. help desk employees)
- Configure "Users" (i.e. customers)
- Configure "Help Topics"
- Configure "SLA" (service level agreements)

<h2>Configuration Steps</h2>

<h2> 
 STEP 1: Access your created Windows 10 virtual machine (which has osTicket currently installed on it) hosted in Azure by establishing a remote desktop connection via its public IP address using your preferred Remote Desktop client.
 
</h2>

<p>

  - Ensure to start/turn on your VM if it was turned off after the previous lab.
 
 ![image](https://github.com/user-attachments/assets/717a484f-161d-4a11-8c7f-fd1752d2b202)
</p>

<h2>
 STEP 2: Access the help desk login page using this link within the Virtual Machine (http://localhost/osTicket/scp/login.php).
</h2>

- Be sure to log in using the administrator credentials that were assigned during the osTicket basic installation process towards the end of the previous lab.

![image](https://github.com/user-attachments/assets/4be6480e-345e-4bd0-aa4e-602f708f2595)

![image](https://github.com/user-attachments/assets/23bdc905-2b23-4da0-a7bf-2df6cc415261)

- NOTE: Upon login, if you are not automatically directed to the admin panel (and instead to the agent panel), simply click the "Admin Panel" link in the top right corner to be redirected to the admin panel in order to complete the outlined configuration objectives. 

![image](https://github.com/user-attachments/assets/67d2c382-fed3-415e-bd1b-3a97d2f9b241)

<h2>
STEP 3: It seems your help desk agents are hungry. Time to configure some roles for them.🍞
</h2>

 <p>

  - (From the admin panel) Select the "Agents" tab then select the "Roles" Tab.
  - Select "Add New Role"
    - You can name this new role whatever you would like (I chose Supreme Admin 👑)

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
   - Name this new team "Online Banking"
   - Add the admin agent that you are currently using to this team.
     - You are free to add more agents to this team after we create them later in the lab.  
 - Select "Create Team" 

![image](https://github.com/user-attachments/assets/e4be4415-0b74-4f82-ae07-66fc9532c9c6)

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

 STEP 7: Your Help Desk is currently a Ghost Town. It is time to finally provision some Help Desk Agents to work these tickets!
</h2>

<p>

 - (From the admin panel) Select the "Agents" tab, then select the "Agents" tab below it.
 - Select "Add New Agent"
 - Within the "Account" tab
   - You can name your agent whatever you like
   - Assign an email address of your choosing
     - NOTE: the email username may be whatever you like but the email's domain must be a recognized email domain (eg. gmail.com 
       or outlook.com) 
   - Assign a username of your choosing
   - Check the "Administrator" field underneath "Status and Settings" as well
     - This grants the agent access to the Admin panel.  
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
      - This will enable the agent to assume their "Supreme Admin" role even if assigned a ticket or task that is outside their primary 
        department or extended access department, instead of being granted "read-only" access. 

   - Optionally, you may also grant this agent "Extended Access" and place them in a secondary department (I chose Support) and grant them the Expanded 
     Access role for tickets assigned to that department. 

   ![image](https://github.com/user-attachments/assets/8c0d5d20-f404-4dbb-b2e7-f9edda5eb51b)

   - The default permissions assigned to this agent (which can be viewed in the "Permissions tab") will suffice for the purposes of this lab.
   - Lastly, you can also add this agent to a specific team if you so desire via the "Teams" tab.
     - I chose to add this agent to the "Level I Support" team
    
 ![image](https://github.com/user-attachments/assets/339aa9e7-1bdc-4195-b1cd-248a3dccaf1a)

   - Now finally, click "Create" and you will have successfully provisioned your first help desk agent.
</p>
<b>
 
</b>

<p>

 - We will create another help desk agent and also verify that the first agent was provisioned accurately, so let us kill two birds with one stone...figuratively of course. 🐦
   - Log out of your current admin agent's account and login as the new administrator agent that you just created.

![image](https://github.com/user-attachments/assets/8c8115bf-0064-4459-929f-a3d32e6d84a7)

   - Now navigate to the admin panel to begin creating a new help desk agent.
     - Repeat the steps outlined above to create a new Agent.
     - "Agents" tab ---> "Agents" tab ---> "Add New Agent" 
     - Name your new agent whatever you would like
     - Assign an email address with a recognized domain name
     - Assign a username and manually set a password.
     - NOTE: Leave the "Administrator" field unchecked this time
       - We do not want to get too trigger-happy with provisioning Admin permissions...the principle of least privilege is a cornerstone of 
          cybersecurity best practices for good reason.
      
![image](https://github.com/user-attachments/assets/fd81ec14-6f26-4237-b1d1-bc2fff9fa936)

   - Under the "Access" tab, assign this agent's primary department to be "Support" and grant them the "Expanded Access" role.
   - Uncheck "Fall back to primary role on assignments"
     - This will ensure that this agent is granted read only privileges on any tickets or tasks that are not assigned to his/her primary or extended accesss department(s).
       - Do not add this agent to any extended access departments.
   - Leave the default permissions assigned to this agent as is.
   - Assign this agent to the "Level II Support" team. 

![image](https://github.com/user-attachments/assets/0f309702-8ddc-406a-ac4e-8492c0e02ccb)

  - Finally, click "Create" to successfully create another help desk agent using your created help desk agent...I call that agentception 😏
</p>

<h2>

 STEP 8: What good is a ticketing system if we have no users to well, use it? It is time to configure some users so we can get to resetting those passwords 💻
</h2>

<p>

 <p> 

  - Navigate to the Agent Panel.
  - (From the Agent Panel), select the "Users" tab
    - Under "User Directory" select "Add User"
    - Assign an email address and name to the user (be as imaginative as you would like to)

![image](https://github.com/user-attachments/assets/7dce28ba-cf4c-466f-866a-3fbf641a347d)

   - Click "Add User"
   - Repeat these steps to create as many end users as you would like for your ticketing system (I will create one more).

![image](https://github.com/user-attachments/assets/d966aeb6-c077-46c4-b660-d117b4ea51e4)


 </p>
</p>

<h2> 
 STEP 9: Time to configure a few SLAs (Service Level Agreements) to give our Help Desk Agents some objective metrics to guide their response efforts. 📝
</h2>

<p>

 - Navigate to the Admin panel.
 - (From the admin panel), Select the "Manage" tab then select "SLA"
 - "Add New SLA Plan"
   - Name this SLA "Sev-A" (just to indicate the highest severity)
   - Set the Status as "Active"
   - Assign a grace period of 1 hour
   - Configure the SLA's schedule to be 24/7
   - "Add Plan"

  ![image](https://github.com/user-attachments/assets/52e140ce-657e-44cf-89d9-7830cb00fe3f)

  - Repeat these steps two more times.
    - Create an SLA named "Sev-B" with a 4-hour grace period and on a 24/7 schedule.

![image](https://github.com/user-attachments/assets/7d45ec5f-d53d-4057-ac1e-4de6b0394a6d)

    
   - Create another SLA named "Sev-C" with an 8 hour grace period and a grace period of Monday - Friday, 8am - 5pm while also abiding by U.S. Holidays.


  ![image](https://github.com/user-attachments/assets/b4fbe357-61bd-4de6-84c4-69852c047642)


</p>
<h2>
STEP 10: Now that we have our Users and some SLAs to provide the expected service levels for these users, the last thing we need to configure are some "Help Topics" so that they can communicate what it is that they need help with from our Help Desk Agents.
</h2>

<p>

 - Navigate to the admin panel.
 - (From the Admin Panel), Select the "Manage" tab, then select "Help Topics"
 - Click the "Add New Help Topic" button.
   - Under the "Help Topic Information" tab:
     - Topic: Business Critical Outage
     - Status: Active
     - Type: Public
     - Parent Topic: Top-Level Topic

  ![image](https://github.com/user-attachments/assets/7cb72aca-39cc-4ea0-a238-88d4c938bf04)


   - Under the "New ticket options" tab:
     - Department: System Administrators
     - Ticket Number format: System Default
     - Status: System Default
     - Priority: Emergency
     - SLA Plan: Sev-A
    
   
   ![image](https://github.com/user-attachments/assets/5026c5be-e50f-422a-a249-e83119e55bf7)

   - Under the "Forms tab:
     - Do not change the default configurations.

   ![image](https://github.com/user-attachments/assets/825e5276-64c2-4d9e-bdaa-bc033f580ec4)

   - Click "Add Topic" 

   - Repeat these steps to create as many help topics as you would like to. I will create three more namely:
     - Personal Computer Issues
       - Parent Topic: "Report a Problem"
       - Department: "Support"
       - Priority: "Normal"
       - SLA Plan: Sev-B
     ![image](https://github.com/user-attachments/assets/6fb35c32-f11f-40c8-afc6-622bee468069)

      
     - Equipment Request 
         - Parent Topic: "General Inquiry"
         - Department: "Maintenance"
         - Priority: "Low"
         - SLA Plan: Sev-C
       ![image](https://github.com/user-attachments/assets/83c00ddf-3abb-4a67-9c80-1147561a0628)


     - Password Reset...How could I ever forget this one? 
       - Parent Topic: "Top-Level Topic"
       - Department: "Support"
       - Priority: "Normal"
       - SLA Plan: Sev-B
       ![image](https://github.com/user-attachments/assets/6552617e-feea-4d72-95f4-15fce07700dc)
   

</p>

<h2> 

Congratulations! You have successfully completed the post-installation configuration of osTicket. Feel free to navigate throughout the portal and make additional config changes to your heart's content. If you would like a brief simulated exercise in creating and triaging tickets, as well as the overall ticket lifecycle in osTicket, please check out my other GitHub repository linked
[here](https://github.com/Cybersecuritim/osticket-ticket-lifecycle).
</h2>

  <h3>

  - PS: If you ever wanted to take a temporary break and reduce the costs of having your computing resources hosted in Azure you can 
    stop/deallocate your VM within the Azure portal.
     - From the [Azure portal](https://portal.azure.com) home page select or search for "Virtual Machines"
     - Then select the VM that you created for the osTicket lab and select "Stop" then confirm your selection.
    
   ![image](https://github.com/user-attachments/assets/f69f2e4f-4954-4976-a285-71bef8b78b86)
  </h3>

