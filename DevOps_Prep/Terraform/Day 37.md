# Terraform
<img width="1257" height="643" alt="image" src="https://github.com/user-attachments/assets/a6e267c7-75e7-4835-b18d-754f638b90ae" />

Configuring database instance:
 - two ways:
 1) user_data -> only runs at the run time of creation.  Disadvantage of User data: If we there are any changes in the script(configuration) - we have to destroy the existing terraform configuration, and then create again, for the changes to take place.
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

lets continue after bastion and Route53 records creation from Session - 36:

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

<img width="808" height="657" alt="image" src="https://github.com/user-attachments/assets/fad8cb5a-60c0-4c11-a660-68443baa037d" />


*******************************************


for bastion - we created 50 GB root volume:

lets login to the bastion host, since it got created after doing the following:

> c/devops/daws-90s/repos/roboshop-dev-infra/30-bastion > terraform apply -auto-approve
> 


<img width="744" height="892" alt="image" src="https://github.com/user-attachments/assets/c3f0a06b-ae31-4698-acf1-4c6f63bafc36" />

by checking df -hT and sudo lsblk, we see that the volume is created for 50G, but we are using only 20GB

we need to extend partition 4:

<img width="764" height="517" alt="image" src="https://github.com/user-attachments/assets/1885f37c-8e19-4494-be8b-fa9460d938ad" />

<img width="1079" height="534" alt="image" src="https://github.com/user-attachments/assets/f0234883-706d-4e13-baca-73695690bbfd" />

sudo growpart /dev/nvme0n1 1

we need to increase the partition 4 in -> sudo lsblk

<img width="812" height="402" alt="image" src="https://github.com/user-attachments/assets/3eba3ea3-1eed-428a-b0cc-0b28a9d49412" />


dev - devices

nvme0n1 - is disk

so disk is under devices


<img width="845" height="100" alt="image" src="https://github.com/user-attachments/assets/1477e299-96e8-4a93-a126-fcb294541d21" />


<img width="719" height="301" alt="image" src="https://github.com/user-attachments/assets/a409906e-59b9-4391-8eb8-49cc149a346a" />




now, I want to add 30GB volume in partition 4 to RootVG-rootVol which has 6GB currently:



<img width="514" height="240" alt="image" src="https://github.com/user-attachments/assets/3556c28c-dfe6-4a50-8522-5f587007c0e3" />

lvextend -r -L +30G /dev/mapper/RootVG-rootVol

<img width="878" height="570" alt="image" src="https://github.com/user-attachments/assets/7220ade4-6384-447d-836d-3a2cc2d3a0a1" />

<img width="676" height="194" alt="image" src="https://github.com/user-attachments/assets/2499da85-ff67-4f48-b9e5-ea06d26ef289" />

<img width="684" height="177" alt="image" src="https://github.com/user-attachments/assets/5aecf3e0-3073-43ba-9261-f99dff774f99" />


lsblk
growpart /dev/nvme0n1 4
lvextend -r -L +30G /dev/mapper/RootVG-rootVol
xfs_growfs /
df -hT

The above steps are being done manually, how about doing these steps when the system starts?
-> User Data

lets create - a terraform template file -> bastion.sh.tftpl

tftpl -> template file

<img width="1078" height="647" alt="image" src="https://github.com/user-attachments/assets/a3882f80-32fd-445c-9450-fefd4e063dd6" />

since we wanted to do it for homevol rather than root val, since we use the user - EC2-user rather than root user, we would target to use - homeVal

<img width="1129" height="434" alt="image" src="https://github.com/user-attachments/assets/31199b97-a16b-412c-a139-ed15ef368bf6" />

<img width="1752" height="827" alt="image" src="https://github.com/user-attachments/assets/a0ece2e1-9986-4bd6-bd99-8f5537b9322c" />



lets destroy the resources created for bastion in 30-bastion folder, and reapply, so that these user data changes will take place while creating the instance.

Note: User Data will always apply during creation of the instance.

After doing the > 30-bastion> terraform apply -auto-approve

<img width="1687" height="790" alt="image" src="https://github.com/user-attachments/assets/63da097a-60f1-4081-85bd-8eb1ad2b87da" />

bastion host got created, lets check the config of the disk in the bastion by doing SSH to bastion:

<img width="1520" height="922" alt="image" src="https://github.com/user-attachments/assets/c1d0dbcf-b64a-4bd8-b7df-51285adfc04d" />


-------------------------------------------

Now since the bastion is done, lets look at creating Databases:


<img width="1777" height="872" alt="image" src="https://github.com/user-attachments/assets/8d16b543-885f-4b14-a1b5-390d7ad08bd6" />

<img width="1149" height="735" alt="image" src="https://github.com/user-attachments/assets/a71213e6-b983-4fae-b216-482b3d50d657" />

<img width="1570" height="616" alt="image" src="https://github.com/user-attachments/assets/ec48613c-e085-4ac1-9704-cf93ce7cc6b8" />


now, the instance for MongoDB will be created, how do we configure MongoDB?
two ways:
1) User Data
2) Provisioners

We can also do this by - going to that instance, and installing ansible, and run the ansible playbooks -> roboshop.yaml -> to configure MongoDB.



so, apart from creating database, we need Route53 record too: like this: #mongodb-dev.daws90s.shop


<img width="1170" height="654" alt="image" src="https://github.com/user-attachments/assets/1bb60f20-2388-48b8-93c3-e2d923103272" />

<img width="874" height="643" alt="image" src="https://github.com/user-attachments/assets/f2eddca7-f64e-4cec-ba04-b8048ff6c218" />

now let's do > 40-databases > terraform apply -auto-approve

the route53 record is now created:

<img width="1737" height="830" alt="image" src="https://github.com/user-attachments/assets/2cfcfe6b-fe6c-41ad-9d6b-162afcc6ce6e" />


--------------------------------------------------------------------------------------------------------------------------------------

Let's get back to Session 37-after creation of Bastion host and Route53 records for database:

<img width="1559" height="530" alt="image" src="https://github.com/user-attachments/assets/5b036bcf-2a75-45fe-82e2-4c05a24a05ae" />

the role - Roboshop-dev-bastion is created, and you can assign it to EC2 instances only.

so, once I create Bastion host, and attach this role, now I can have access.

here, we have to install terraform too - where ? in userdata.tf file of Bastion host - i.e. bastion.sh.tftpl

<img width="1457" height="830" alt="image" src="https://github.com/user-attachments/assets/dacd1b6f-57bc-4969-998f-4d6650904d6c" />

<img width="1312" height="536" alt="image" src="https://github.com/user-attachments/assets/4be7defb-2b6c-46b7-8608-5df29a795a0b" />


after running this terraform will also get installed


***Important***
So, we don't have to go to Bastion host and run aws configure, since to Bastion host, we assigned a role -> that role has  ->  AdministratorAccess permission, it automatically sets up - aws keys by default!


<img width="1900" height="749" alt="image" src="https://github.com/user-attachments/assets/6101779a-1f09-4518-9c87-44535f0afbd6" />


now you can add the IAM role to the roboshop-dev-bastion
<img width="1889" height="628" alt="image" src="https://github.com/user-attachments/assets/5618732b-7358-434e-9d28-b793502fa594" />

<img width="935" height="302" alt="image" src="https://github.com/user-attachments/assets/d4d0a4c3-9c49-4455-bcf3-6de8cf4d06ec" />




























  

   




