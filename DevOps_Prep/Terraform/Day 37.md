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

in 20-sg-rules:
for this to work:
<img width="1688" height="630" alt="image" src="https://github.com/user-attachments/assets/5babb921-575e-4745-a9d3-e61e5108b153" />

we need in data.tf the following:
<img width="1075" height="622" alt="image" src="https://github.com/user-attachments/assets/edf6a1de-5e31-4bb6-8cd6-2e777dc673e8" />

I missed ipv4 - then in terraform plan - got the following error:

<img width="1646" height="195" alt="image" src="https://github.com/user-attachments/assets/88cce853-e66c-4959-a333-41d21484c7fe" />

now, it is fixed in 20-sg-rules/

<img width="1190" height="644" alt="image" src="https://github.com/user-attachments/assets/413fcfdf-ddb9-4297-a6b1-557fa6b3807d" />

<img width="944" height="948" alt="image" src="https://github.com/user-attachments/assets/4618821b-a812-4e1c-9982-f63cdfe4a4e8" />



coming back to bastion:

Now we have VPC's, security groups, and security group rules, now we can create databases, however to connect to databases, we need bastion - so we setup bastion:

<img width="341" height="877" alt="image" src="https://github.com/user-attachments/assets/3c1d2970-6a71-4780-b189-8fd64167f42d" />

00-vpcs
10-sgs
20-sg-rules
30-bastion
40-databases

*******************************************
Question: 
<img width="958" height="305" alt="image" src="https://github.com/user-attachments/assets/2fd242d5-2b7e-409a-a71a-03e675a69461" />

what is the meaning of terraform = true in the above code:
In your Terraform code, the line

hcl
Terraform = "true"
inside the common_tags block is simply defining a resource tag — a key-value pair that will be attached to your AWS resources.

Here’s what it means:

Key: Terraform

Value: "true"

This tag acts as a marker indicating that the resource was created or managed by Terraform.
It doesn’t affect Terraform’s behavior directly — it’s purely metadata stored in AWS.

💡 Why it’s useful
Helps you identify which resources were provisioned by Terraform versus manually created ones.

Makes it easier to filter or audit resources in the AWS console using tags.

Can be used in automation scripts or cost tracking to group Terraform-managed infrastructure.

So, it’s a best practice for clarity and governance — not a functional command.

***************************************
















  

   




