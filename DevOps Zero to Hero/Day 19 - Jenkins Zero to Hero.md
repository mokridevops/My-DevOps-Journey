
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
to run docker as agent




<img width="588" height="329" alt="image" src="https://github.com/user-attachments/assets/c7fd0365-8703-460a-a7cb-48f34f1b7cb6" />



<img width="525" height="230" alt="image" src="https://github.com/user-attachments/assets/35d8f970-6689-4372-a789-a099b8ca1c5c" />


ArgoCD is the modern day Continuous Deployment tool


<img width="568" height="307" alt="image" src="https://github.com/user-attachments/assets/513f51f8-a4a6-48a4-9c47-56a817d5d004" />

the above is the standard CICD process
























