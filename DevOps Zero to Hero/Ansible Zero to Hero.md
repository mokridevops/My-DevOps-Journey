# Ansible Zero to Hero

sudo apt update

sudo apt install ansible

<img width="1094" height="265" alt="image" src="https://github.com/user-attachments/assets/9230cb74-a219-4ddc-a716-fa9c62deefeb" />



<img width="1400" height="684" alt="image" src="https://github.com/user-attachments/assets/f2e20144-2a21-470c-9934-4383cc5a12fd" />



<img width="975" height="163" alt="image" src="https://github.com/user-attachments/assets/9f1d6564-fb44-4930-bc5f-52e59927c6ec" />

once ansible is installed, you would need one more server, i.e using the server where you have ansible, you will configure the other server



<img width="1396" height="327" alt="image" src="https://github.com/user-attachments/assets/02c81594-fd18-4552-b30e-677edf0f89a1" />


Ansible requires is that passwordless authentication, then Ansible can configure anything on the server

 since both the servers are in same  Amazon on EC2, always talk to private IP address

 
  <img width="941" height="278" alt="image" src="https://github.com/user-attachments/assets/b8ed848e-60e7-4c64-beef-d3a66f013871" />


  ssh-copy-id 172.31.62.28 - this will make it passwordless, but not always ssh-copy-id will work due to permission issues, so we follow other route

  we use ssh-keygen

  <img width="1012" height="340" alt="image" src="https://github.com/user-attachments/assets/0769b637-ebfd-4143-8d6b-767bff63c0a9" />

  <img width="1119" height="724" alt="image" src="https://github.com/user-attachments/assets/c425481b-9619-4fab-93ae-81365715602a" />


this directory get created with ssh-keygen

<img width="826" height="206" alt="image" src="https://github.com/user-attachments/assets/d72f3517-8dc5-4779-840f-0354fd08631f" />


id_rsa - private key

id_rsa.pub - public key

<img width="1437" height="521" alt="image" src="https://github.com/user-attachments/assets/ab63c94d-6b93-4fd9-b0a0-7185617a5c77" />

<img width="1897" height="803" alt="image" src="https://github.com/user-attachments/assets/01d18496-3f6c-452c-bb05-2abedfff0ef7" />


ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDGAAsKaJgdsqNu2xNHAFZr9utqpGrt+UI59PIrJeo3mRL0EV3awDrY+PyFjtWqffPrPfkmx9go+18uPdIO4kLlCUDiWUv+1QNUl07ipV6RKh3OXsPnlkmDkFlQTZKpNsgplx63p1nwVzk7atOnky4RalKZ3Dm9rh4cHu3mulO9b+AoXK26cLISSbIxDJsS7KzjRPuW/HOm5HX2OyusJSLUfMWmvO+Y5L3g44HWBdrzqzpUF2rFuYjd2KQdU5jZG+4S8TVJBsDpuWnGGzrl/LYoq0OaHHg7Lv3MHe52/Ytpv8JXGPOG7c45P46txhrrx8gN5Ko392NO76/Xjys6vvEIZ7wQK8h4DgvQUFOMdv73x0pNXXGfQtHFhao4zQ0oD1Q/EgvMprBfk9/cmqdTsKGNCLTrEzinh4l/7GyOlpxF9RZAwEwFMFp2HnQkNJK0iqauyXVP9URw4c+tONzp/orjM0mXRj1k2a3Qw16vGkXnAgzc1ta93Ovgy9h6fZ3yUBk= ubuntu@ip-172-31-82-122


now login to second target machine copy the public key of the ansible server above to the authorized keys of the target server



so on the target server:


do ssh-keygen here on target server as well


<img width="1130" height="666" alt="image" src="https://github.com/user-attachments/assets/0c69e4f8-2e26-4b83-ab2d-7b3d4c1502af" />


<img width="597" height="125" alt="image" src="https://github.com/user-attachments/assets/9e5bc70e-2bd0-4014-9f8d-b7684c77b97f" />


<img width="884" height="212" alt="image" src="https://github.com/user-attachments/assets/edc80b23-5e8a-4ceb-a2dc-cd5eee277c6e" />

<img width="1288" height="221" alt="image" src="https://github.com/user-attachments/assets/d49f4c02-500e-4d39-9b3b-377dfed29499" />

now lets do ssh to target server from ansible server



<img width="859" height="122" alt="image" src="https://github.com/user-attachments/assets/bad218af-44e6-4aed-ab90-eb41925f759e" />

<img width="1122" height="689" alt="image" src="https://github.com/user-attachments/assets/1c843ffa-e2eb-4abc-aaf7-02e6a80a7f5e" />


we were able to authenticate target server without any password

this ithe prerequisite for anisble - we need to have password less authentication


# How did we achieve the password less authentication:

I just copied the public key of the Ansible server to the authorized keys of the target server






---------------------------


# ANSIBLE PLAYBOOK:



Ansible playbooks are nothing but ansible files



You dont have to write ansible playbooks all the time, you can as well run the ansible commands from the CLI.

those are called - Ansible Adhoc Commands



----------------------------------------

to find size of shell files:

<img width="679" height="44" alt="image" src="https://github.com/user-attachments/assets/d5ff707d-4db6-4722-8215-3f91eb410e73" />



<img width="617" height="220" alt="image" src="https://github.com/user-attachments/assets/11aa4ec9-77ec-4917-a73f-456c061ebe10" />

----------------------------------------

Inventory files: file that stores IP Addresses of target server


<img width="850" height="355" alt="image" src="https://github.com/user-attachments/assets/abaa8701-388f-4664-aafd-2d1c08db7f77" />

if I have 10 servers, I will have to open the inventory file, and append the IP Addresses of the 10 servers

two ways to give the ansible command:

ansible -i inventory "ip address of target file"

or

ansible -i inventory all -m "shell" -a "touch devopsclass"

-a - arguments
-m - module


<img width="716" height="35" alt="image" src="https://github.com/user-attachments/assets/bf29169c-8fc2-4e07-98fa-6282fb9cdd17" />

now checking in the target server:

<img width="608" height="111" alt="image" src="https://github.com/user-attachments/assets/8fec7399-377a-454b-ab7b-368b102f8024" />

now, by giving all instead of single ip address

<img width="740" height="120" alt="image" src="https://github.com/user-attachments/assets/5b55c476-62f7-45c5-92be-c565ff6544a1" />


it will execute the above scirpt - touch devopsclass in all the target servers that are listed in the inventory file in the ansible server

now checking in the target server:

<img width="654" height="202" alt="image" src="https://github.com/user-attachments/assets/25b95dad-d121-43cc-b611-231e4865c852" />

whenever we see the yellow color lines - it means it is successfully executed.

If there are any errors, there will be red color lines


we write a playbook, only when we want to execute set of these commands, just or executing one or two ansible adhoc commands we dont really need to write a playbook




# Interview Question:

what is the difference between Ansible Adhoc commands and Ansible Playbook:

Ansible Adhoc Commands - for one or two tasks
Ansible Playbook - for multiple commands


Ansbile modules:

<img width="1825" height="708" alt="image" src="https://github.com/user-attachments/assets/1871f057-5acb-4a71-8e5c-9d26ac06c82a" />

<img width="1083" height="659" alt="image" src="https://github.com/user-attachments/assets/d60f8f9f-b328-47ea-a559-d118f3af82ad" />


Let's check number of processes on the target server: by using nproc on the Ansible adhoc command:
<img width="1149" height="137" alt="image" src="https://github.com/user-attachments/assets/8cd78938-e611-4429-9706-777b2d0fd9f8" />




# Interview Question:

Use case: run certain number of playbooks only on dbservers, and other number of playbooks only on webservers

so do grouping in the inventory


<img width="776" height="200" alt="image" src="https://github.com/user-attachments/assets/e0bc4bea-c37f-48f7-8493-39429119c4f4" />

square brackets are very important

<img width="257" height="196" alt="image" src="https://github.com/user-attachments/assets/a9cb0617-aa51-4888-9006-4d5773bbcb2b" />


<img width="1152" height="71" alt="image" src="https://github.com/user-attachments/assets/0cbded2a-d089-48b9-b3e4-40b972c56a67" />

Ansible will go to the inventory file, see what is the list of webservers and execute the ansible commands on the list of webservers






# Interview  Question:  How do you group the servers in Ansible, or how do you execute certain number of tasks only on certain number of servers in ansible?

In Ansible all the server names are configured in inventory files, you can do group of the servers in the inventory file, and tell ansible to execute this playbook or run these ansible commands only on certain number of servers


-------------------

# ANISBLE PLAYBOOK


<img width="1024" height="127" alt="image" src="https://github.com/user-attachments/assets/6f21f150-9390-474e-b4c3-1c2821f68f23" />

scenario : we will install Nginx and then start Nginx in the target servers using Ansible playbook,

Ansible playbook we write as .yml files



Yml playbook

--> starts with --- '3 hyphens' - indicating it is yml file

then you start explaining about your playbook

- name: Install and Start Nginx  ---> this hyphen indicates that it is a list of playbooks, we can write one playbook or multiple playbooks
  hosts: all   ---> it executes on all servers on inventory
  become: root ---> it will execute ansible playbook as root user

  tasks:
    - name: Install nginx
      shell: apt install nginx
      or
      apt:
         name: nginx
         state: present

    - name: Start nginx
      service:
         name: nginx
         state: started
         


- name: my second playbook   




<img width="622" height="520" alt="image" src="https://github.com/user-attachments/assets/7ea1d7f1-215c-4adc-98d4-05e9f456953c" />


<img width="1293" height="697" alt="image" src="https://github.com/user-attachments/assets/50aa1402-35ac-46e3-9547-4763ae24822f" />


now go to the target server and check:

sudo systemctl status nginx


add the verbose -v ---> to get more details of what ansible is doing?

-vvv ---> will give you more info


<img width="1276" height="65" alt="image" src="https://github.com/user-attachments/assets/ade69710-3cfa-4a26-9327-a3cbe1d55e54" />


<img width="1302" height="433" alt="image" src="https://github.com/user-attachments/assets/5d6abf73-7ea6-4125-a412-62d2450573d8" />


writing ansible for kubernetes cluster:

<img width="795" height="193" alt="image" src="https://github.com/user-attachments/assets/2d40f744-94d3-4c2f-9fee-8065f7682946" />


<img width="896" height="234" alt="image" src="https://github.com/user-attachments/assets/60b6f212-f493-46fa-af12-024f9afebf04" />


Now, this will become too big - as it will involve more than 50 tasks

so, Ansible has comeup with something called as Ansible Roles



Ansible Roles: is efficient way to write Ansible Playbooks, that will implrove efficiency to write complex playbooks

Ex: Lets say If I want to configure kubernetes using Ansible, it will have close to 50 - 60 tasks, and you will have lot of variables, parameters, certificates, secrets that you have to configure while creating this kubernetes cluster, for that reason if you try to do it with roles you can segregate each and everything, and properly structure Ansible Playbooks

ansible-galaxy role init kubernetes


  <img width="1161" height="211" alt="image" src="https://github.com/user-attachments/assets/96274d72-490e-42ba-b16d-97d6ec730cf6" />


<img width="1235" height="390" alt="image" src="https://github.com/user-attachments/assets/b926084f-c379-48c0-9659-7143aac78469" />


<img width="1302" height="732" alt="image" src="https://github.com/user-attachments/assets/3b648da2-c2dc-4439-a971-76ed7f16c318" />

using these files and folders, you can structure your playbooks



meta - used to write some metadata information inside these files
ex: details of this entire playbook, licensing information

defaults: store some variables, etc - 
vars folder
group vars folder
tests: unit tests
handlers: handling some kind of exception, send some mail notification - when this nginx server is failing to start, etc
tasks: 
readme.md: tells the content of what is being stored in playbook
files: certificates, etc - if you want to pass the index.html on to the tasks, so that it can be copied to other machine

















































  


  
