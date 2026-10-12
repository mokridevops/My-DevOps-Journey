# Terraform
<img width="1257" height="643" alt="image" src="https://github.com/user-attachments/assets/a6e267c7-75e7-4835-b18d-754f638b90ae" />

Configuring database instance:
 - two ways:
 1) user_data -> only runs at the run time of creation.  Disadvantage of User data: If we there are any changes in the script(configuration) - we have to destroy the existing terraform configuration, and then create again, for the changes to take place.
 2) provisioners -> Provisioners can be used - to avoid destroying the configuration, and running the script, however there is one disadvantage: requries ssh connection from where terraform is running.

We will take provisioners approach, then 
Connect to bastion host -> run the terraform commands there, i.e. terraform should be installed here, so now bastion host creates ec2, r53, etc..
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

after attaching the role - 


<img width="903" height="181" alt="image" src="https://github.com/user-attachments/assets/9b0dd504-cf53-42b3-ba06-d24333d3ec11" />

now login to the Bastion host -(EC2 instance):


<img width="533" height="416" alt="image" src="https://github.com/user-attachments/assets/23952f8f-4453-44e6-86f6-8762758b5586" />

# command to see the user logs: (very important)

> less /var/log/cloud-init-ouput.log


<img width="574" height="458" alt="image" src="https://github.com/user-attachments/assets/c48e499d-07d3-457e-a496-82f4e9121122" />


<img width="664" height="493" alt="image" src="https://github.com/user-attachments/assets/cd0848c0-1319-49e2-beab-c904829345ab" />

able to do > aws s3 ls

that means aws is getting access throug bastions host, that we we got connected to AWS.

<img width="1546" height="988" alt="image" src="https://github.com/user-attachments/assets/f5c07324-5de3-4ca3-a60f-07fdd7370ddc" />




adding a policy attachment:


<img width="1718" height="861" alt="image" src="https://github.com/user-attachments/assets/0a0f6d4f-b114-4d18-bf75-e60a095a1d2c" />

<img width="1658" height="886" alt="image" src="https://github.com/user-attachments/assets/bfb7230e-be50-41d6-b91a-63a100ed4844" />

<img width="1874" height="896" alt="image" src="https://github.com/user-attachments/assets/27630aca-69f3-453f-85c2-efdabcc91d24" />


<img width="1326" height="816" alt="image" src="https://github.com/user-attachments/assets/0d2c3068-a15b-4976-b1e3-d173ba167953" />


<img width="1437" height="771" alt="image" src="https://github.com/user-attachments/assets/9e28e016-3d7e-4591-9c44-e22051d84195" />


detaching the manually added IAM access role:



<img width="1770" height="887" alt="image" src="https://github.com/user-attachments/assets/31a5611f-1c39-49e2-ab2e-547855689b63" />

lets detach the role that was added manually, and then run the terraform code to do it attach it automatically.


<img width="773" height="254" alt="image" src="https://github.com/user-attachments/assets/dcd34b57-dcd3-458c-8ad9-3e373eeb8d8d" />


Deleting the role too from front end:



<img width="1417" height="777" alt="image" src="https://github.com/user-attachments/assets/7be7f915-90f6-40a3-a4af-1a219c760875" />



while doing terraform apply, i mistakenly interrupted by pressing- ctrl+C,

<img width="1889" height="461" alt="image" src="https://github.com/user-attachments/assets/7ba21e66-f3b4-49e9-8e52-a76b2b3b2325" />

I got this Error:

I have to force unlock the state file : terraform force-unlock <lock-id>


<img width="1111" height="364" alt="image" src="https://github.com/user-attachments/assets/9d6ea737-a072-46a1-b463-e5a035796dad" />


after terraform apply -auto-approve, I am able to access aws:



<img width="1629" height="1116" alt="image" src="https://github.com/user-attachments/assets/781ad29f-66ba-4e98-b755-d96fd5c4a36c" />

<img width="1040" height="884" alt="image" src="https://github.com/user-attachments/assets/311cf425-8852-4206-b484-0c8fe4829a2d" />


We use something called as Terraform_data, as Provisioners - also we need to write in the instance, so it will be used during the time of instance creation:

<img width="1232" height="862" alt="image" src="https://github.com/user-attachments/assets/f98c339f-5c0b-40d1-a57a-2677c363035b" />
this is the code for remote-exec provisioner


lets us see Terraform data


Terraform_data
===============
Earlier called as null resource, actually will not create any resources but used for terraform life cycle.  Lifecycle means - Create, update, read, delete

We can have triggers to control when to run.  terraform_data used for provisioners and file copy, etc..


Through terraform_data, we can write the provisioners outside of the instance, instead of inside instance.  If we write inside the instance, it will get triggered only during creation and deletion.


<img width="1235" height="879" alt="image" src="https://github.com/user-attachments/assets/1acf7d5f-88a1-44b3-8617-d9418593a07e" />

ansible controller -> node -> push

we can install ansible in any node, we can pull the repos and self configure

mongodb:
========
install ansible
pull git ansible repos
run playbooks against localhost



Now, we login to bastion host, using MobaXterm

<img width="945" height="378" alt="image" src="https://github.com/user-attachments/assets/9de77ba3-c41c-406e-baff-913810ece6b5" />
<img width="1839" height="519" alt="image" src="https://github.com/user-attachments/assets/28ecce38-13f2-4544-86e9-9ec34ab647c0" />


<img width="851" height="526" alt="image" src="https://github.com/user-attachments/assets/202fbee9-a0a5-4f73-82b7-16d595684740" />




we clone the repo:


<img width="1330" height="910" alt="image" src="https://github.com/user-attachments/assets/e0d624c4-1490-4b8f-997e-4b05204a990d" />

here the disk size - has not increased - need to see why?


<img width="1334" height="910" alt="image" src="https://github.com/user-attachments/assets/4fda44b4-ebf2-460b-bb90-9eb59b719b4b" />

we need 50GB for Bastion host, as we run terraform init multiple number of times, each init will generate .terraform folder with more than 1 GB.

<img width="1332" height="910" alt="image" src="https://github.com/user-attachments/assets/a08d6a82-789a-4849-aff3-39121f32dad2" />
<img width="1294" height="660" alt="image" src="https://github.com/user-attachments/assets/d3cc0b35-aa55-4a6f-9a16-a1b7e7560340" />



<img width="1049" height="510" alt="image" src="https://github.com/user-attachments/assets/d2d169fc-5667-4547-b005-a7fb549450d0" />


<img width="798" height="308" alt="image" src="https://github.com/user-attachments/assets/85d84877-0480-4e1b-b21b-1b99eb53025e" />




<img width="622" height="273" alt="image" src="https://github.com/user-attachments/assets/5848ef4b-22ef-4127-a945-0cf32635e3b7" />

3 resources are getting created:
1) EC2 instance for MongoDB
2) Route53 record for MongoDB
3) terraform data -> terraform data will not create any resources, it follows standard terraform lifecycle, we can use terraform data for provisioners, and we can use triggers to control terraform data, earlier this is called as null resource.

<img width="392" height="149" alt="image" src="https://github.com/user-attachments/assets/eafb00db-1bf6-41d3-b380-99317c54607d" />


Now, when we click on terraform apply, resources will get created, and the following connection gets established - from bastion to mongodb, because there is a security group connection that will allow bastion to mongodb connection:

<img width="1356" height="922" alt="image" src="https://github.com/user-attachments/assets/03941fa8-23d3-477c-ae5f-564d10619311" />

first the bootstrap.sh file will be place in the mongodb server
next the remote-exec will be called, and it will execute the bootstrap.sh , after execution what will happen?
<img width="1319" height="948" alt="image" src="https://github.com/user-attachments/assets/66174d9b-6578-41d6-a58e-fcfc4cd6face" />

component will get -> mongodb
environment will get -> dev
and it will install ansible, create /var/log/roboshop/ directory
and creates ansible.log file with the necessary permissions

then it will clone the roboshop-ansible-v3.git
 and then git pull before, to check if there are any things missing

 and then execute ansible-playbook  with component = mongodb, and environment = dev  roboshop.yaml file

 <img width="1069" height="796" alt="image" src="https://github.com/user-attachments/assets/c1306a2a-bbc8-4f7f-9038-eec1e188e51f" />

 Flow:

 these ansible variables below, gave it to terraform:
 
 <img width="1240" height="879" alt="image" src="https://github.com/user-attachments/assets/c7ad2e33-8c3b-4294-9d1a-5c90a6a378e9" />

 now, terraform gave the enviornment variable to shell script:
<img width="1286" height="847" alt="image" src="https://github.com/user-attachments/assets/ab40cd35-c0e2-4ec2-bfae-6f2fe19742fb" />

shellscript took it, and gave it to ansible:

<img width="1578" height="962" alt="image" src="https://github.com/user-attachments/assets/7104166f-b000-4fbe-855f-46f4263c7077" />



 # to run this:  I logged in to Bastion host on mobaxterm:

 
 <img width="947" height="463" alt="image" src="https://github.com/user-attachments/assets/a6b763ab-cfb9-4c2c-8ccb-690fcb24a1fd" />des

 
<img width="1232" height="123" alt="image" src="https://github.com/user-attachments/assets/ecc8bbb1-6e6f-44bf-bdd5-1620a030afa5" />


<img width="1520" height="936" alt="image" src="https://github.com/user-attachments/assets/6128e797-d993-4739-87d0-2b28afc0de48" />

<img width="1321" height="102" alt="image" src="https://github.com/user-attachments/assets/3068b613-0286-4b09-83e9-3b5f00bfcf4b" />




<img width="1030" height="469" alt="image" src="https://github.com/user-attachments/assets/b01fe8d4-36ef-4986-ba9e-0ecd7786d203" />



 
<img width="730" height="280" alt="image" src="https://github.com/user-attachments/assets/6e59a4b6-d751-443a-a916-546c6e8028bd" />

<img width="598" height="193" alt="image" src="https://github.com/user-attachments/assets/17b2e985-1e1b-41b0-9e6b-58c199498c78" />


<img width="1105" height="934" alt="image" src="https://github.com/user-attachments/assets/968f6a87-a219-4b9c-bd5e-8fa476e306dc" />

<img width="1485" height="928" alt="image" src="https://github.com/user-attachments/assets/4dd481c8-edc4-4245-b045-0517e5047c3f" />

<img width="1473" height="273" alt="image" src="https://github.com/user-attachments/assets/afc6b402-b1ac-4880-adf2-9d5b8bd7607f" />


<img width="1480" height="349" alt="image" src="https://github.com/user-attachments/assets/1fd59d77-08b3-4af9-b861-b9f7f9e337d4" />

<img width="1534" height="654" alt="image" src="https://github.com/user-attachments/assets/7a67128e-90d6-4b87-8334-1f9430c51dd9" />

Mongodb is installed now.








 


 






   




















  

   




