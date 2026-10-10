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

  

   




