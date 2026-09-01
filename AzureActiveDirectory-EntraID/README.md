# Azure --> IAM /Entra 
Management Group : it is the place where you configure polices and rules , rules and polices we write in Management Group

Subscriptions1 are nothing but billing boundaries  
Resource Group is nothing but logical container of your resources 
<img width="1330" height="706" alt="image" src="https://github.com/user-attachments/assets/e07edd53-7e2d-42d6-ae4b-66f94e11148d" />

Service Principlas 
<img width="1445" height="541" alt="image" src="https://github.com/user-attachments/assets/3b92f6dc-d8af-4501-8327-c03cbd6d6d14" />
| Level                | Purpose                                            |
| -------------------- | -------------------------------------------------- |
| **Management Group** | Organize/manage **subscriptions**                  |
| **Subscription**     | Billing and security boundary containing resources |
| **Resource Group**   | Organize **Azure resources**                       |
| **Resource**         | VM, Storage Account, SQL DB, VNet, etc.            |

Azure --> EntraId 
Primary Domain : azure provide default domain name with no charges 
If you want to provide custom domain , you need to buy entra id licenses 
<img width="1663" height="278" alt="image" src="https://github.com/user-attachments/assets/abc32337-e7f2-426b-9209-2d2e573bdbe9" />


In azure , we are giving the 2 permisions fregently ( Owner , contributor )
Owner : we can perform any activity on that resource and she can also give permissions to other users 
Contributor : we can perform any activity on that resource  , she/he cannot give the permissions to other users 

<img width="879" height="267" alt="image" src="https://github.com/user-attachments/assets/7d5612a7-e86d-414b-a66f-3832394d1f63" />


go to Azure EntraID --> Create a USER 
Then Take Userid and then log in to azure portal 
we cannot perform any action because you dont have any permissions 
Now we will give the permission 
 go to the main Azure Account  --> Create RG then --> CLick IAM on RG --> Click ADD --> Click Assign Role 

 This is not best practice
 Then go to Create a GROUP and attach the user to GRUOP 
 

### Give permission b/w Resources 
1. I created the VM and enable the identity under Security 
<img width="1353" height="541" alt="image" src="https://github.com/user-attachments/assets/3860f607-2124-42d8-9d11-79e1a44d794e" />

2. I created the Storage Account --> Then CLick IAM --> ADD --> Add Role Assignment
   Add Storage blob reader
   <img width="1887" height="374" alt="image" src="https://github.com/user-attachments/assets/4ee4273d-6a0a-4d10-bb6a-e6cef6c4b7c3" />


Azure VM has identity and VM need to connect the Azure then get the identity , we need to connect the Azure from Inside VM 

run this command in VM  , If you want ONLY the access token
access_token=$(curl -s \
"http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/" \
-H "Metadata: true" | jq -r '.access_token')

OR   

access_token =$(curl 'http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https%3A%2F%2Fstorage.azure.com%2F' \
-H 'Metadata:true' | jq -r '.access_token')


Then Verify the token is here or not 

Echo $access_token 

Then run this command 

curl "https://storageiamnavishna.blob.core.windows.net/narendra?restype=container&comp=list" -H "x-ms-version: 2023-11-03" -H "Authorization: Bearer $access_token"


curl "https://storageiamnavishna.blob.core.windows.net/narendra/Hello.txt" -H "x-ms-version: 2023-11-03" -H "Authorization: Bearer $access_token"
