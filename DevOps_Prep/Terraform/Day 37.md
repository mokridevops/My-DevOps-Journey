# Terraform
<img width="1257" height="643" alt="image" src="https://github.com/user-attachments/assets/a6e267c7-75e7-4835-b18d-754f638b90ae" />

Configuring database instance:
 - two ways:
 1) user_data -> only runs at the run time of creation
 2) provisioners -> requries ssh connection from where terraform is running

Connect to bastion host -> run the terraform commands there, so now bastion host creates ec2, r53, etc..
two ways:
1) aws configure
2) IAM roles

so, in our project of Roboshop -> we give bastion host the permissions to configure the MondoDB database that is in Database subnet, where we don't have access to do any configurations.

   IAM - Identity and Access Management

   User -> console access through username and password, keys for programmatic access
   Group -> a group of users
   Role -> non human users. Services in aws, users in other accounts and third party users called federated users can assume role.
   We can create role for EC2 service to provide access for creating other AWS services
   Permissions -> what resources and actions
   Policy -> a list of permissions is called policy
   Policy can be attached to a User, group or Role


   Non -> resource
   Verb -> Action on resource

   EC2, S3, Cloudfront, LoadBalancer, etc.... -> resources
   Create EC2, Update EC2, Read EC2, Delete EC2 -> Actions on resources

   <img width="1901" height="838" alt="image" src="https://github.com/user-attachments/assets/29ccde60-92b3-4f50-87f1-96f9bdc0c831" />

   
<img width="912" height="706" alt="image" src="https://github.com/user-attachments/assets/68ffee27-7752-405f-b3e9-ebe008ef682c" />

<img width="1587" height="521" alt="image" src="https://github.com/user-attachments/assets/8666e0d1-b565-4bef-921f-b617d4345db1" />

<img width="1533" height="824" alt="image" src="https://github.com/user-attachments/assets/ba7c8c36-1c68-4c24-9f22-04bb4276ed04" />
<img width="1853" height="848" alt="image" src="https://github.com/user-attachments/assets/8cab36d9-ef1e-4157-96b1-2592c7d27f3d" />
<img width="842" height="294" alt="image" src="https://github.com/user-attachments/assets/abb0f466-acc2-4a91-8370-05fd0c68adb8" />



## to create all the services at once in terraform command:

> for i in 00-vpc/ 10-sg/ 20-sg-rules/ 30-bastion; do cd $i; terraform apply -auto-approve; cd ..; done


<img width="1375" height="889" alt="image" src="https://github.com/user-attachments/assets/09a93943-437f-4fd3-853f-8aee82dcf085" />

<img width="1327" height="202" alt="image" src="https://github.com/user-attachments/assets/ef46c30b-dc1f-4bc2-8a74-0e19a4f6bb32" />



----------------------------------------------

Bastion host - setup

check session - 36

While setting up EC2 instance for Bastion - AWS give us 20GB by default, which is not enough, lets increase it to 50 GB


<img width="982" height="856" alt="image" src="https://github.com/user-attachments/assets/75a561e9-a8af-4ef5-9e71-d0d895250ff8" />

<img width="1110" height="734" alt="image" src="https://github.com/user-attachments/assets/ba4a9db2-aa6d-4980-97b4-2a7fdd75e1f0" />

this root volume that we are attaching to Bastion host (EC2 Instance) will automatically be destroy when terminating the EC2 instance.

<img width="1414" height="666" alt="image" src="https://github.com/user-attachments/assets/64af77f2-7e82-4cd7-8287-e5969b9b30aa" />

so, here usage is only 20GB, remaining 30 GB - we have to manually mount it












  

   




