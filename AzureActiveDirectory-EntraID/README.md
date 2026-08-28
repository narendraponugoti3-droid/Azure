# Azure --> IAM /Entra 
Management Group : it is the place where you configure polices and rules , rules and polices we write in Management Group

Subscriptions1 are nothing but billing boundaries  
Resource Group is nothing but logical container of your resources 
<img width="1330" height="706" alt="image" src="https://github.com/user-attachments/assets/e07edd53-7e2d-42d6-ae4b-66f94e11148d" />

Service Principlas 
<img width="1445" height="541" alt="image" src="https://github.com/user-attachments/assets/3b92f6dc-d8af-4501-8327-c03cbd6d6d14" />


In azure , we are giving the 2 permisions fregently ( Owner , contributor )
Owner : we can perform any activity on that resource and she can also give permissions to other users 
Contributor : we can perform any activity on that resource  , she/he cannot give the permissions to other users 

go to Azure EntraID --> Create a USER 
Then Take Userid and then log in to azure portal 
we cannot perform any action because you dont have any permissions 
Now we will give the permission 
 go to the main Azure Account  --> Create RG then --> CLick IAM on RG --> Click ADD --> Click Assign Role 

 This is not best practice
 Then go to Create a GROUP and attach the user to GRUOP 
 


