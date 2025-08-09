
# Containers

Introduction
Docker
Buildah - integration with scopio and podman

VM is advancement to Physical Servers
Containers are considered - advancement to Virtual Machines



<img width="902" height="591" alt="image" src="https://github.com/user-attachments/assets/6a0f6eda-2c56-419e-8b34-a104cd76987e" />


Why to move towards containers if Virtualization is working well?

<img width="982" height="610" alt="image" src="https://github.com/user-attachments/assets/e74012a4-8b70-4b67-a538-1df2ff46da58" />


<img width="992" height="627" alt="image" src="https://github.com/user-attachments/assets/dc142297-ed0c-48f2-a6fe-0f00b097bda1" />

Docker containers - light weight:

Application
+ libraries
+ system dependencies


Docker containers are ligh weight in nature, and they dont have their own full operarting system, they use the resources from the base operating system, with very minimalistic packages.

<img width="1007" height="636" alt="image" src="https://github.com/user-attachments/assets/4aef3bdd-f440-4cd5-b1cf-f95ecadfd05a" />


why Docker is very famous?

<img width="722" height="541" alt="image" src="https://github.com/user-attachments/assets/2fc67390-58c0-4a45-8746-a08a117ff315" />

famous docker commands - using which you can create containers:

Write Docker file, submit it to docker engine -> and generate a docker image -> using the image you create a container.

lif cycle of Docker:

<img width="931" height="592" alt="image" src="https://github.com/user-attachments/assets/2a11c2ba-fc74-45e5-8844-d63c4a329cd5" />


# Buildah


<img width="680" height="497" alt="image" src="https://github.com/user-attachments/assets/0d8dc18d-12db-4e8a-8442-5ebc8167613a" />


If your Docker engine is going down, all of your containers will not be responding, and Docker Engine could be a single point of Failure (SPOF).

<img width="793" height="473" alt="image" src="https://github.com/user-attachments/assets/5ac2b128-73ce-415b-8bf6-6d89c9e5ec45" />

to create docker image, docker engine creates lot of layers, and it takes lot of space, hence buildah came up with a tool to create a docker image to resolve above issues.


<img width="875" height="612" alt="image" src="https://github.com/user-attachments/assets/cabbdd3a-7306-4b34-b21d-ad9ab5e1b804" />








