
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



