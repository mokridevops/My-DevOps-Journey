
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

