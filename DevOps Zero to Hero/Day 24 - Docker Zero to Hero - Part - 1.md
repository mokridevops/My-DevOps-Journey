
# Docker Zero to Hero - Part 1


<img width="771" height="336" alt="image" src="https://github.com/user-attachments/assets/5d0ddb34-70d1-4218-a116-7650ba3bed4a" />




<img width="802" height="503" alt="image" src="https://github.com/user-attachments/assets/cdfbd0ea-f317-4f56-8203-e0450d25ba22" />


<img width="790" height="396" alt="image" src="https://github.com/user-attachments/assets/62d6da80-1906-40c6-aad2-1444f78fa5b6" />

 
<img width="787" height="433" alt="image" src="https://github.com/user-attachments/assets/5f0ff9e9-67e7-4b74-b055-6aac39d4fce1" />

These are the files and folders in the containers base images, these basic folders will form a logical isolation from one container to another container.

these files and folders cannot be shared, and these are not part of your kernel.


what files and folders that containers use from host operating system or kernel:

host file system
networking stack
system stack
namespaces
control groups

<img width="1126" height="485" alt="image" src="https://github.com/user-attachments/assets/23990b9f-bf17-440b-bb9b-59e7aca3f476" />


How small is this image?

<img width="1147" height="798" alt="image" src="https://github.com/user-attachments/assets/702067a7-68a2-491d-861f-3a181147d7bd" />



# DOCKER

Containerization is a concept, and Docker is a containerization platform which provides easy way to containerize your applications, which means with Docker you can build container images, run the images to create containers and also push these containers to container registries such as DockerHub, Quay.io and so on.


# Architechture of Docker:

<img width="1160" height="683" alt="image" src="https://github.com/user-attachments/assets/a1bd2f27-c905-4924-aab6-7ba59e5d3806" />

Docker Daemon - is heart of docker

 


Podman - is a competitor for Docker

docker build -> command from docker client (CLI) given to docker daemon -> to build Images
docker run   -> command from docker client (CLI) given to docker daemon -> to create containers from Images
docker pull  -> command from docker client (CLI) given to docker daemob -> to pull image from docker registery



# Life Cycle of Docker:


<img width="1316" height="452" alt="image" src="https://github.com/user-attachments/assets/339a3bc8-fc85-4de1-a9ec-5d45986d8a2e" />

docker file - set of instructions - to tell docker daemon - get me a Ubuntu base image -> 




# Terminology of Docker:

1) Docker Daemon -> dockerd -> listens to your docker requests, and acts upon your requests - heart of docker

2) Docker Client

3) Docker Desktop

4) Docker Registeries -> place where you store your docker images, you share these images whcih are stored in a centerailized place.

5) Dockerhub - popular place to store the images and share them


   <img width="1201" height="582" alt="image" src="https://github.com/user-attachments/assets/466c929a-f48c-4df1-832a-c15c3a0b49eb" />

   <img width="1282" height="662" alt="image" src="https://github.com/user-attachments/assets/2cefc894-1922-4ef5-9ba4-062a2d280764" />

   dockerhub
   quay.io - public registery + private registeries

   # Interview Questions:

   ## what is the difference between github and dockerhub?

   Answer: Github - to store your source code,
           Dockerhub - is to store your images


   # Docker file:
   set of instructions - where you are sharing with docker daemon


   # Images:

   # Install Docker


<img width="1276" height="638" alt="image" src="https://github.com/user-attachments/assets/db610d9b-b632-403c-9863-339cb85c81d5" />

to run the above python code:
1) create EC2 instance
2) select VM
3) install python 3
4) install pip
5) etc


   Using docker:

   download the image and run the image

   
sudo apt update

sudo apt install docker.io -y

<img width="930" height="637" alt="image" src="https://github.com/user-attachments/assets/76267423-6014-4112-b875-530c3516ed9c" />

   
   
if you want to do it on your laptop, download docker desktop - it will create VM on your laptop and go from there

<img width="1182" height="670" alt="image" src="https://github.com/user-attachments/assets/959b33f9-bc22-46d8-a289-441b5347285d" />



   <img width="451" height="253" alt="image" src="https://github.com/user-attachments/assets/113f438c-e429-4bd4-b465-7723c7935a9a" />

   

<img width="1292" height="607" alt="image" src="https://github.com/user-attachments/assets/a8e005fc-37dd-4e96-86e0-b0ddb7f00631" />


<img width="1292" height="156" alt="image" src="https://github.com/user-attachments/assets/27dfa9b4-8d0a-4b93-b317-33f439028fe2" />

we are adding the ubuntu user to the docker group

sudo usermod -aG docker ubuntu

usermod - is adding the ubuntu user to the docker group
once you run the above command you have to logout an login back





<img width="852" height="647" alt="image" src="https://github.com/user-attachments/assets/6889b7aa-4ecd-4dab-9da0-5d022ce589b9" />



   










