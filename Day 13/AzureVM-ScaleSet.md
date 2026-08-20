Azure VM should be high available and Zone redundant 

Setup this Diagram today in Azure 
<img width="1092" height="530" alt="image" src="https://github.com/user-attachments/assets/3194f5b1-417b-4d26-9c18-078221490bb3" />

Step1 : Create a Resource Group 
Step2 : Create a VN(Virtual  Network ) with One Subnet 
Step3 : Create VM with Zone 1 and Create another VM with different  Zone 2 and enable public IP and security group :SSH and http 

Step4 : Connect to VM --> ssh devopsuser@ipaddress  --> install apache2 --> cd /var/www/html --> vi index.html-->replace content and save it 
Step5 : repeat Step4 on 2nd VM 
Step6 :
