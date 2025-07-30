# Configuration Managment:

<img width="986" height="610" alt="image" src="https://github.com/user-attachments/assets/bc1a0a53-2ab5-4069-a13c-b626b8993697" />



Configuration Management is a way - how devops engineer manages the configuration of the infrastructure

<img width="996" height="631" alt="image" src="https://github.com/user-attachments/assets/c755de90-8d80-4b27-b425-d55583a9a8f1" />


earlier - before Ansible, what system admins used to to is:

suppose if there are 100 servers that needs to be upgraded or install secure patches or do some git or any other software installation:
the used to write scripts:

shell scripting - if it is unix box
Powersheel - if it is windows box

and they have to counter in all possibilities such as:

25 machines are windows
25 machines are linux
25 machines are centOS
25 machines are Ubuntu

after that the entire configuration was moved to cloud:

with cloud the number of server getting created were : 10X

while the size of the server has shrinked down by 10X

so there is a definite need for a tool to solve this problem

<img width="996" height="631" alt="image" src="https://github.com/user-attachments/assets/380ed2c9-2030-4cac-930c-5e1e37eb55d5" />


to address this problem - Configuration Management concept came in

Redhat Ansible

<img width="957" height="602" alt="image" src="https://github.com/user-attachments/assets/c6b3875c-121f-4ace-a1b0-2c4520c7caee" />


# Interview Questions

# When you have Puppet, Chef and Ansible, why Ansible?

Puppet is a Pull mechanism model

Ansible is a Push mechanism model



<img width="977" height="372" alt="image" src="https://github.com/user-attachments/assets/5f1f65e6-b4cd-4b34-a5a2-a9739f303d7a" />

what is Push model for ansible?

so the devops engineer, can write ansible palybook script on his laptop and the configuration is updated using PUSH mechanism to the 10 EC2 instances

- Ansible uses Agentless model i.e

- put names (DNS/IP Addresses) of these Servers in an inventory file  and have password less authentication enabled, with just one click of a button or running the ansible playbook, all the configurations are updated on these 10 EC2 instances.

- So using Ansible, if you have to scale up or scale down - just add public IP addresses in the inventory file and you are good to go, so simple.

- Dynamic Inventory - Ansible will auto detect - if we are adding 100 new servers, Ansible will understand that these new 100 servers are also to be configured along with the existing servers.

- Ansible is pretty easy with both Windows and Linux - support for windows and Linux is very good with Ansible.
- Ansible is pretty simple - uses simple yaml manifests

- - Ansible is written in python - you can write your own Ansible modules
 
  - sharing is always possible between two devops teams using Ansible Galaxy.
 
  


Puppet - uses - Master/Slave architecture

1 master puppet server

configure 10 EC2 instances as Slaves

now Puppet can make the changes on these respective EC2 instances.

Puppet language




<img width="1011" height="636" alt="image" src="https://github.com/user-attachments/assets/6735212a-af02-4602-ba03-2278b9f501ca" />




<img width="1032" height="642" alt="image" src="https://github.com/user-attachments/assets/3082c894-3644-4f67-bf1f-a32fc6ae346a" />



Ansible - Disadvantages:

windows configuration management is slightly difficult compared to linux configuration management
Debugging - no proper mechanism to understand where has the playbook execution ran in to a problem
Performance - issues  --- it can execute on 10,000 servers - but you might run into performance issues, Ansible is dealing with these issues

<img width="524" height="476" alt="image" src="https://github.com/user-attachments/assets/309bbe44-4c56-4093-858b-beb5cbd0ba7d" />


<img width="936" height="629" alt="image" src="https://github.com/user-attachments/assets/66c6f743-799c-443a-af04-839f50f9b9c8" />




# 18 most asked Ansible Interview Questions:

1) what is the programming language that Ansible uses? did you write any custom modules in Ansible?
   python is the programing language which Ansible is using.  you can write your own modules using python and contribute to Ansible. I didn't get any requirement to write custome modules in python for Ansible.

2) Does Ansible support Linux and Windows or only Linux?
   Supports both linux and windows .
   For linux - it uses protocal called - SSH
   For windows - it uses protocol called - Win Rm
   
<img width="940" height="570" alt="image" src="https://github.com/user-attachments/assets/0af1b737-4a58-4ea0-be35-e65d02278685" />

3) Why did you choose Ansibel over other configuration management tools like Puppet and Chef?

4) Is Ansible PUSH mechanism or PULL mechanism ?

PUSH mechanism

5) what programming language that Ansible supports?
   Yaml manifests in Anisible to wirte Anisble playbooks

6) does Ansible supports all the cloud providers?
      For Ansible it does not matter clould providers
      what matters is: IP Address
      do you have SSH enabled to this machine, or is the SSH for this machine allowed from your Ansible host or your laptop. 
   



