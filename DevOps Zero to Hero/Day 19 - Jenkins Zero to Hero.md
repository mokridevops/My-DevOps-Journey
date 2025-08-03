
<img width="767" height="44" alt="image" src="https://github.com/user-attachments/assets/f817b02c-175e-43c6-9cf8-1d4acb1857e6" />


<img width="773" height="466" alt="image" src="https://github.com/user-attachments/assets/d6f3719c-e442-45fe-8ff0-2793951da80a" />

<img width="515" height="67" alt="image" src="https://github.com/user-attachments/assets/b45ddf16-fd1e-4bfe-8a56-b31eda00ce48" />


ubuntu@ip-172-31-89-41:~$ sudo cat /var/lib/jenkins/secrets/initialAdminPassword
278372bc11bf41a3a9f8101f942ba325
ubuntu@ip-172-31-89-41:~$




<img width="944" height="465" alt="image" src="https://github.com/user-attachments/assets/b9bdbbfe-1c61-41ba-8c8c-af33b020e0c4" />

Jenkins architecture:


<img width="552" height="269" alt="image" src="https://github.com/user-attachments/assets/cf98e169-7386-4ef7-b1d1-2d10b67cd860" />

always use Jenkins Master - to offload the load

each worker node is an EC2 instance

new approache:

configrure worker node with docker agent:


Note: We have used docker as agent in our jenkins project setup, and we found this is very useful in terms of cost and also in terms of efficiency - in terms of spinning up and tearing down the containers.



we shall install docker on the same machine that has jenkins

sudo apt update
sudo apt install docker.io

<img width="421" height="305" alt="image" src="https://github.com/user-attachments/assets/3c4eb9b9-54fb-41ce-9b1e-dab413a1253d" />


<img width="273" height="91" alt="image" src="https://github.com/user-attachments/assets/680b3cec-68e1-4505-8548-13a354182c57" />

sudo su -
usermod -aG docker Jenkins
usermod -aG docker ubuntu
systemctl restart docker

docker daemon - is by default is not accessible to other users.

we installed docker using root, only this root user is having access to this daemon, we have to grant access to this docker daemon

we will grant the access to jenkins user as well as ubuntu user


sudo su -  ---> switching to root user
usermod -> used to grant access to jenkins - making it part of docker group

docker installation creates a group called docker

restarting docker daemon


<img width="643" height="179" alt="image" src="https://github.com/user-attachments/assets/a9f9d1e0-4799-4dda-ae19-4a860586adb1" />

changing to user jenkins by giving the command -> su - jenkins


<img width="649" height="272" alt="image" src="https://github.com/user-attachments/assets/e800d419-6e47-4488-81cc-a4b34a7bcb99" />



now jenkins user was also able to create or run the containers

it is a good practice to restart your jenkins by doing this:

<img width="648" height="247" alt="image" src="https://github.com/user-attachments/assets/97efabb4-5045-48de-9081-aba1d1254401" />

<img width="938" height="459" alt="image" src="https://github.com/user-attachments/assets/e367a824-771c-4f50-a984-38084750806d" />


<img width="914" height="442" alt="image" src="https://github.com/user-attachments/assets/ea643f79-41d7-435f-9cc2-39787ffb1b4d" />

now that jenkins has restarted, now install the docker pipeline plugin in jenkins

why? 
to run docker as agent, jenkins should understand that whenever I am executing a job, I have to make sure that if the user provides in the jenkins file to run this specific job on the docker I need to have the configuration.

 you will install the docker pipeline so that jenkins will execute your pipelines on Docker Agent if the required configuration is provided in the jenkins file.




<img width="588" height="329" alt="image" src="https://github.com/user-attachments/assets/c7fd0365-8703-460a-a7cb-48f34f1b7cb6" />



<img width="525" height="230" alt="image" src="https://github.com/user-attachments/assets/35d8f970-6689-4372-a789-a099b8ca1c5c" />


ArgoCD is the modern day Continuous Deployment tool


<img width="568" height="307" alt="image" src="https://github.com/user-attachments/assets/513f51f8-a4a6-48a4-9c47-56a817d5d004" />

the above is the standard CICD process


<img width="808" height="289" alt="image" src="https://github.com/user-attachments/assets/efe32140-cbe2-4358-9a58-469022c87182" />







<img width="335" height="219" alt="image" src="https://github.com/user-attachments/assets/3088f077-4bc3-465e-acfa-234697e3283e" />



docker run hello-world

Hello from Docker!


This message shows that your installation appears to be working correctly:

1. Docker client contacted Docker Daemon
2. Docker Daemon pulled the Hello-World Image from Docker Hub (amd64)
3. Docker Daemon created a new container from that image which runs the executable that produces the output that you are currently reading.
4. Docker Daemon streamed that output to the Docker client, which sent it to your terminal.

   



<img width="911" height="418" alt="image" src="https://github.com/user-attachments/assets/98393e6b-9345-4c0b-99aa-ccf9cd638bcf" />

Freestyle project - you cannot share with peers

Pipeline - you can write declarative or script, you can put it in git repository, and get peer review and verify if anything is wrong


Always go with pipeline approach - groovy scripting


<img width="685" height="375" alt="image" src="https://github.com/user-attachments/assets/d4291e30-9fa2-4cb6-acb2-cce27684502a" />


Jenkins is all about - picking up the code from your local develoment or any version control system and delivering it to production or stagging envirnoment where automating all the stages that are invovled in between.  If there are 10 stages, your job is to use jenkins and automate 10 stages in between, so Jenkins acts as Orchestrator.

<img width="790" height="496" alt="image" src="https://github.com/user-attachments/assets/30fbe6d2-a74c-422a-a4ac-af69963208b5" />

<img width="1708" height="932" alt="image" src="https://github.com/user-attachments/assets/0399fd91-e9fd-44b5-a5aa-85d991b34f59" />

<img width="686" height="342" alt="image" src="https://github.com/user-attachments/assets/22b1f164-2f3f-44f3-93b3-556ec3f9381f" />

<img width="479" height="203" alt="image" src="https://github.com/user-attachments/assets/1b8f4794-7e03-4fc6-b4c2-5ce2ddbf4eeb" />

after the execution of the pipeline script is done, Jenkins deleted the container

<img width="479" height="203" alt="image" src="https://github.com/user-attachments/assets/d5a86827-2f19-4318-9cc6-8f35aa7f6d6b" />






-----------------

multistage multi agent


3 tire application

front end - Ubuntu - Java
back end  - Ubuntu - Oracle
database --  CentOS

using worker nodes is very complicated, and not a right approach



----
<img width="774" height="331" alt="image" src="https://github.com/user-attachments/assets/23bb41ce-941a-431b-909b-2608e7fb2b77" />

using ArgoCD for continuous delivery





<img width="774" height="331" alt="image" src="https://github.com/user-attachments/assets/812a3c69-81af-4485-becc-ff0368b7394c" />

ArgoCd - is actually pointing towards Git or Jenkins because.

ArgoCd will be watching for any new versions available on Git, and then takes that version and deploys it on Kubernetes










