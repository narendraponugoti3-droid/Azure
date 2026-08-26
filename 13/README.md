# Azure

# Date 14/08/2026 
  Azure Hyd Region 
  Inside VN with One subnet 
  Subnet1-zone1: VM  2 cpu , 4gb ,64gb , INIC , ubuntu
  Subnet1-zone2: VM  2 cpu , 4gb ,64gb , INIC , ubuntu
  with Security group : ssh and http 
  First VM place in Zone 1 
  Second VM place in Zone 2 

<img width="1209" height="620" alt="image" src="https://github.com/user-attachments/assets/f12e6db9-040e-434f-adfa-6d0cde66e8e7" />

This is called zone redundancy

               -   Step1 : Create RG and VN with one Subnet 
               -   Step2 : Create VM with Zone1 and open the port 22 and 80 and enable public IP 
               -   Step 3: Create Another VM with zone 2 and open the port 22 and 80  enable public IP 
               -    Step 4: connect to VM ( ssh devopsuser@ipaddress )
                   Sudo su -
                   apt update 
                   apt install apache2 -y 
                   cd /var/www/html
                   vi index.html 
                   remove the content and copy the content here 
                   Then Save it 
                   http://publicipaddress 
              -  Step 5 : Repeat step4 in Another VM also 



Now Introducing the load balancer to connect both VM in different Zone with out public IP address 
<img width="1086" height="481" alt="image" src="https://github.com/user-attachments/assets/c4424031-a715-43be-9a20-cbc9030162d0" />


 - Step1 : Create the Backend Pool and add the VM
 - Step2 : Load balancer -Front end - Public IP
 - Step3 : Users connect the load balancer public IP and traffic to redirect to backend pool
 - Step4 : when request reach to load balancer , then redirect happen from LB to backend pool


# Configure the Load Balancer Manually in Azure 

Azure Console -- Search Load Balancer  - Create Load balancer with standard LB 

Subscribtion: 
    Resource Grooup: 
Name: MFLB 
REgion: Canada centrol 
SKU : 
Type: Public ( public/ internal )
Tier: Global (Global , region )

### Front end Configuration :
Public IP created and give it to front end 
<img width="1583" height="415" alt="image" src="https://github.com/user-attachments/assets/9f47e162-9268-46ef-9d1a-67189504fbf3" />

### Backend Pool 

Click Add the backend pool 
Name: 
Virtual Network: 
Backend Pool Configuration: NIC ( NIC, IP address) // if you select NIC , you change ip address , no issue 
<img width="1502" height="499" alt="image" src="https://github.com/user-attachments/assets/4308290e-9969-410b-bf1c-725c4bc63fa7" />

### Inbound rules 
 Click Load Balancing rule 
 <img width="1528" height="495" alt="image" src="https://github.com/user-attachments/assets/d40c93fc-2d15-41f5-9270-8ab6ecaf4e4b" />


Then Review and Create 

Then Go to MFLB -- Click Settings -- Frontend configuration -- take public IP address and search it in google chrome 

# Virtual machines Scale set 

we have existing VM with below configuration and but that VM is not sufficient so I need to upgrade this VM with more CPU and RAM 
<img width="586" height="374" alt="image" src="https://github.com/user-attachments/assets/c6eb5675-8d05-4310-a120-56a0e31f7138" />

This is called Vertical Scaling  , we are getting this type of requirments frequently 

   ### Horizontal Scaling 
   
we have existing LB with 2 VM but Particular time we are receiving more load so we need to increase the VM  Then We need to reduce the VM as well in this case , we need to use he Horizontal Scaling 
Based on the Load , VM is going to increase uo to 10 VM based on the Load like CPU utilization , Memory Utilization           Disk Utilization 

        
<img width="1135" height="227" alt="image" src="https://github.com/user-attachments/assets/0d578762-3aef-4570-88f0-c2ae8887206e" />


In this Horizontal Scaling , we need a base image with configuration of existing VM  we need to convert the image using already configured VM 

### Create an Image using existing VM 

Go to Public IP Address  ---> select IP Address --> Click Associate --> Resource Type :Network Interface 
Select the VM ( VM which is standalone VM) 

Connect to Existing VM and then this command to delete some of properties 
    waagent -dprovision+user
    
Then Stop the Existing VM  , Click the Capture  --> Select Image --> Then Fill all detials then create it 
    
