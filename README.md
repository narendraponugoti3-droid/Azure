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

Step1 : Create RG and VN with one Subnet 
Step2 : Create VM with Zone1 and open the port 22 and 80 and enable public IP 
Step 3: Create Another VM with zone 2 and open the port 22 and 80  enable public IP 
Step 4: connect to VM ( ssh devopsuser@ipaddress )
                   Sudo su -
                   apt update 
                   apt install apache2 -y 
                   cd /var/www/html
                   vi index.html 
                   remove the content and copy the content here 
                   Then Save it 
                   http://publicipaddress 
Step 5 : Repeat step4 in Another VM also 

