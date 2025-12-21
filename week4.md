# Phase 4: Initial System Configuration & Security Implementation

## Objective:
This phase focuses on securing the server and ensuring all management operations are carried out via SSH from a trusted workstation.

---

## 1. Configure SSH with Key-Based Authentication
**Objective:** To eliminate password-based login and enhance security, key-based authentication is configured.

### Steps Taken:

1. **Generate SSH Key Pair on Workstation:**
   
    ssh-keygen -t rsa -b 4096 -C "roman email@example.com"
  

2. **Copy the Public Key to the Server:**
   
    ssh-copy-id username@server_ip
  

3. **Disable Password Authentication:**
    - Edit the SSH configuration file (`/etc/ssh/sshd_config`):
      
      sudo nano /etc/ssh/sshd_config
   
    - Set `PasswordAuthentication` to `no`:
      
      PasswordAuthentication no
    

4. **Restart SSH Service:**
    
    sudo systemctl restart ssh

   **Evidence**
   ![keygen](keygen.png)

   
    ![keygen](keygen2.png)

   

    ![restart](restart.png)
---

## 2. Configure a Firewall Permitting SSH from One Specific Workstation Only
**Objective:** Restrict SSH access to the server to a specific workstation (IP address).

### Steps Taken:

1. **Allow SSH from Trusted IP Only:**
    - Configure the firewall to only allow SSH connections from a specific IP:
   
      sudo ufw allow from [trusted_ip] to any port 22
    

2. **Deny Other SSH Connections:**
    
    sudo ufw deny 22
  

3. **Enable the Firewall:**
    
    sudo ufw enable
    

4. **Check Firewall Status:**
    
    sudo ufw status
   

**Outcome:** SSH access will be limited to the specified workstation IP address only, enhancing security.

 ![ufw](ufwserver5.png)


 
 ![ufw](ufwdesktop.png)

## 3. Manage Users and Implement Privilege Management
**Objective:** Create a non-root administrative user with limited privileges and ensure least privilege for user management.

### Steps Taken:

1. **Create a New User:**
    
    sudo adduser adminuser
  

2. **Add the User to Sudo Group:**
   
    sudo usermod -aG sudo adminuser

3. **Ensure Proper Permissions:**
    - Set file permissions for specific directories and files based on user roles.

4. **Verify User Privileges:**
      sudo -l -U adminuser
  

**Outcome:** The new user will have administrative privileges but will not have unrestricted access to the entire system.
 ![users](user1.png)


 
 ![users](user2.png)

## 4. SSH Access Evidence Showing Successful Connection
**Objective:** Capture evidence of a successful SSH connection to the server.

### Steps Taken:
- After SSH key-based authentication is set up, log into the server using the SSH key from the workstation:
  
    ssh roman12@192.168.56.106
   

- **Screenshot:**
   A screenshot showing the terminal window with a successful SSH connection. Ensure the prompt displays the user's session, confirming authentication was successful.
  
  ![keygen](keygen.png)

   ![keygen](keygen2.png) 


## 5. Configuration Files with Before and After Comparisons
**Objective:** Document configuration changes made to the system for security enhancement.

### Steps Taken:
- **Before:** The default SSH configuration allows password authentication.
  
    ![before](before1.png)
  
  
- **After:** SSH configuration file has `PasswordAuthentication no` set, and key-based authentication is enabled.
   ![after](after5.1.png)

   ![after](after5.2.png)

### Files to Include:
- `/etc/ssh/sshd_config` before and after changes.
- Firewall rules before and after implementing IP restrictions.
- User permissions configuration before and after adding `adminuser` to the sudo group.

---

## 6. Firewall Documentation Showing Complete Ruleset
**Objective:** Document all firewall rules applied to restrict access and enhance security.

### Steps Taken:
1. **Document Rules:**
 
    sudo ufw status verbose
   

** Outcome:** Clear documentation of firewall rules, ensuring only trusted sources can access SSH.

 ![firewall](6.png)

---

## 7. Remote Administration Evidence Demonstrating Commands Executed via SSH
**Objective:** Show evidence of remote server administration using SSH.

### Steps Taken:
1. **Execute Commands Remotely:**
    - commands executed via SSH:
     
      sudo apt update
      sudo apt upgrade
      sudo systemctl restart apache2
  

2. **Screenshot:**
   A screenshots showing the execution of these commands via SSH. Document each command's purpose (e.g., updating packages, restarting services).

    ![evidence](7.png)

    ![evidence](7.1.png)
---

## Conclusion
In this phase, the server was configured with SSH key-based authentication, ensuring enhanced security by eliminating password-based access. A firewall was implemented to restrict SSH access to a specific workstation, and a non-root user was created with administrative privileges. Additionally, evidence of successful SSH access and configuration changes has been documented to support security and administration best practices.

