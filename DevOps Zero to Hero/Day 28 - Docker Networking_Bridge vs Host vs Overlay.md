
# Docker Networking | Bridge vs Host vs Overlay | Secure containers with custom bridge network



Networking allows containers to communicate with each other and the host systems


<img width="1032" height="694" alt="image" src="https://github.com/user-attachments/assets/bb40dd56-abcb-49a5-a5c1-66165c59c328" />


<img width="1129" height="681" alt="image" src="https://github.com/user-attachments/assets/c1f0a336-a9a1-4993-b6b0-827c211a6a4f" />


Container communications:

1) communicate with each other
2) Isolation between two containers, where one container might be payments container where that container must be higly secured.

Container networking offer both of these solutions:
 


<img width="1127" height="681" alt="image" src="https://github.com/user-attachments/assets/7f7f47a6-23bb-4a61-bf64-9d8bcdc2cd5a" />


When a container is created, in a host operating system, there is by default a veth (virtual eth) or docker0 network bridge is created between the host operating system and the container.  without this network brigde the communication with the container is lost


other ways the container will talk to host:

1) Bridge networking:
2) Host networking: container will directly use the network of your host, when you create a container docker will directly bind your container with the eth0 of the host

   <img width="1205" height="710" alt="image" src="https://github.com/user-attachments/assets/36794340-c7e7-4f79-8b72-5e6f41e03e87" />

   but this is a problem, security issue, everyone who as access to your host will be able to access container application

   Primary reasons to go to containers is - they are highly secure.  If they are not secure, we make them very secure.

   3) Overlay Networking:
     Kubernetes
     Docker Swarm

 or COE - container orchestration

 Overlay networking is very useful - when there are multiple hosts, when we want to create clusters on multiple hosts, overlay network will create a network that is common to multiple hosts.
   



<img width="834" height="622" alt="image" src="https://github.com/user-attachments/assets/0ec2a102-7491-48aa-84c8-bd7c01d3cb3f" />

when there are multiple containers, where C1 is talking to host using veth,and other container C2 is also talking to host using vithual , then it is very easy for the hacker to talk to all containers that are connected to the host through veth - > virtual ethernet

<img width="834" height="622" alt="image" src="https://github.com/user-attachments/assets/14c0e05e-e135-412e-9928-f31b617050f8" />



   
