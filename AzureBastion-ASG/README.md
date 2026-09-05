# Azure Bastion 

why it comes bastion , in any orgnization , we dont' assign public ip address on any server 
so how to connect the server so we need entry point like vpn, jump server or azure bastion

n a proper enterprise architecture, application servers such as EC2/VMs are normally placed in private subnets and are not assigned public IP addresses. So you need a controlled entry point to reach them for administration.

### Typical architecture
                    Internet
                       |
              +--------+--------+
              |                 |
             VPN          Bastion / Jump Server
              |                 |
              +--------+--------+
                       |
                Private Network
                       |
          +------------+------------+
          |                         |
     Private EC2/VM            Private EC2/VM
     10.0.2.10                  10.0.2.20

     There are several ways to provide that entry point:
     | Method                          | How it works                                                      | Common use                  |
| ------------------------------- | ----------------------------------------------------------------- | --------------------------- |
| **VPN**                         | Your laptop connects to the company's private network             | Enterprise environments     |
| **Bastion/Jump Server**         | Connect to one controlled server, then SSH/RDP to private servers | Traditional AWS/Azure setup |
| **AWS Systems Manager**         | Connect to EC2 without SSH/public IP                              | Modern AWS approach         |
| **Azure Bastion**               | Azure-managed service for RDP/SSH to VMs                          | Azure                       |
| **Direct Connect/ExpressRoute** | Private connectivity from corporate network to cloud              | Large enterprises           |

Azure bastion : PAAS service by ms --> Securely connect to servers via SSH and RDP Access from the browser 

Azure Bastion : Azure create the Seperate subnet for Azure Bastion and assign the public IP address for Bastion 
<img width="920" height="418" alt="image" src="https://github.com/user-attachments/assets/420c2913-d405-4d7c-93a7-48f8f19cbb2b" />

1 Bastion host --> 50 Connection Means 50 memebers would connect at the time 
Create a 2 Azure Bastion Host for redendancy purpose 


Steps : 
  - Create a Resource Group
  - Create a Virtual Network
<img width="1285" height="581" alt="image" src="https://github.com/user-attachments/assets/9ac7c934-4ee2-4434-a055-855c4ae04358" />
  -  Create the Review + Create
  -  Then Create the Bastions
<img width="775" height="646" alt="image" src="https://github.com/user-attachments/assets/a081d244-702a-4c64-aa59-11535a85c973" />

  - Advanced features of Azure Bastion
           - 1. Copy and paste : You can copy a command from your laptop and paste it into the VM.
           - Use case: Almost always useful for administrators.
                       Recommendation: ✅ Enable it unless your security policy prohibits clipboard transfer.
-   IP-based connection : Bastion then establishes the RDP/SSH connection to that IP.
-   Kerberos authentication
                  Kerberos is an authentication protocol commonly used with Microsoft Active Directory.
                  Instead of relying simply on a VM's local username/password, an organization can use domain credentials.
-  Native client support  : Normally, you connect through the Azure Portal browser session:
-  Shareable Link : It allows an administrator to create a temporary link that another person can use to connect to a VM through Bastion.
