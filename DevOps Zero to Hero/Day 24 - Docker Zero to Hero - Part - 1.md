
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



   
Now, lets clone the repository:


<img width="1141" height="258" alt="image" src="https://github.com/user-attachments/assets/cb44c013-4793-4581-977e-f07e06d66f6b" />





<img width="951" height="442" alt="image" src="https://github.com/user-attachments/assets/b9fbfe9a-285b-46d9-b0b1-7453dcead4a4" />

<img width="1115" height="491" alt="image" src="https://github.com/user-attachments/assets/425c815c-2141-4027-b0ca-75b25f9e91b1" />



<img width="867" height="701" alt="image" src="https://github.com/user-attachments/assets/aacd5a84-906c-40a2-80f3-4edcb7ee10ce" />

Explanation:

FROM ubuntu: latest

-> we have to get base image for our docker container - very very important


<img width="1512" height="656" alt="image" src="https://github.com/user-attachments/assets/90e26b75-56ba-4029-8478-860abaf34a2b" />

copy ../app.py .  -> this means app.py is copied to here in the current location

WORKDIR /app -> making my working directory as /app

COPY . /app  -> copying everything to /app folder  - so that I can run all the docker commands on this folder only





RUN apt-get update && apt-get install -y python3 python3-pip  --> we are installing python, because my application is a python application, and we want to get all this information into the docker image, and next time when someone runs the docker image, they will also execute the same set of actions

they dont need to execute, because the docker image is already created, they just run the container directly

so, we provide all the dependencies that are required for the application

finally run a command called:

CMD ["python3", "app.py"]
--> that means we are running this app.py file in python3



<img width="880" height="786" alt="image" src="https://github.com/user-attachments/assets/54e7ed87-ebd1-41b9-a90d-83cd0dcc2dae" />

<img width="1881" height="927" alt="image" src="https://github.com/user-attachments/assets/b64014a1-acd3-47ac-ab05-230dd81cde79" />






<img width="1877" height="986" alt="image" src="https://github.com/user-attachments/assets/760af85b-9c2f-41fc-ba3a-40697ff7a557" />

<img width="1885" height="938" alt="image" src="https://github.com/user-attachments/assets/d66d2f3a-38a8-4c64-aabb-98374285623c" />



<img width="1366" height="937" alt="image" src="https://github.com/user-attachments/assets/f953035b-1145-4244-8f62-dc1f9b8c48c8" />

to build the docker file:

docker build -t abhishekf5/my-first-docker-image:latest .

build docker file, . represents build docker file in the same directory

this is the tag that I am giving:

-t abhishekf5/my-first-docker-inmage:latest

why are we giving a tag?
Answer: on our EC2 instance, there could be hundred's of images - if you are not using a tag, your image will be lost
Your image will be generally created with Docker image id, and it is very difficult to remember, so we usually give tag to recognize it easily.

abhishekf5 - is the login info of my docker - in the dockerhub

my-first-docker-image -> is the repository that I am going to use

when we actually push this image on to a registery, inside a repository - the image gets created - with the name: my-first-docker-image



<img width="1187" height="876" alt="image" src="https://github.com/user-attachments/assets/0a3de409-d1e6-4c87-9033-9286dcb27433" />

<img width="1420" height="868" alt="image" src="https://github.com/user-attachments/assets/eb31ed44-1354-4098-a5ed-363e20f0b0f7" />

<img width="1420" height="868" alt="image" src="https://github.com/user-attachments/assets/b795cb51-f96b-4e7e-9c67-35bbc12d268c" />


docker build -t mokridevops/my-first-devops-image:latest .

so, the image build was soccesful

now, lets execute this image and see how my application runs

 docker run -it mokridevops/my-first-docker-image:latest 

 it -> means interactive terminal

 <img width="1192" height="152" alt="image" src="https://github.com/user-attachments/assets/9a71c4e0-6b07-4449-8132-ff6cf3e4dd51" />

 since this is a command line application, you got the output displayed as hello world.

 What if it is a web application - your application will start running on this specific machine, and you can access the application from your EC2 instance or from your browser

 

In order to share this application with my friends, before that lets see what is there on my dockerhub:

<img width="1895" height="951" alt="image" src="https://github.com/user-attachments/assets/8953b25a-6b4e-496f-93fe-bbbfdfbccb77" />





lets login to docker hub

<img width="935" height="239" alt="image" src="https://github.com/user-attachments/assets/cb9aafd5-ec72-49bf-9ee5-0206e5292b0d" />



<img width="1067" height="162" alt="image" src="https://github.com/user-attachments/assets/07590845-f9e1-4923-a47e-1b58a165c04d" />

<img width="1875" height="758" alt="image" src="https://github.com/user-attachments/assets/427fee35-44ae-4526-b751-35a53d156630" />

<img width="1886" height="950" alt="image" src="https://github.com/user-attachments/assets/cff229f7-bb12-4f90-9c3f-3a4d1c829c56" />

<img width="1902" height="914" alt="image" src="https://github.com/user-attachments/assets/e7d8cb91-1d13-4816-a0e2-259fafd2e1ca" />

<img width="1091" height="178" alt="image" src="https://github.com/user-attachments/assets/d6dc46da-bf75-46e2-b2e5-0150f7136ff4" />

now the image is pushed

lets go to docker hub and check there:

<img width="1891" height="942" alt="image" src="https://github.com/user-attachments/assets/684fd055-8908-4523-bce0-ec54ac11bca6" />

<img width="1881" height="766" alt="image" src="https://github.com/user-attachments/assets/0ae93096-5793-47b5-8315-e31624383fdd" />

<img width="1900" height="927" alt="image" src="https://github.com/user-attachments/assets/0ba32079-3e24-424c-b95b-402c05c827b7" />

by using this command: docker pull mokridevops/my-first-docker-image:latest -> people can get this Docker image on their local
they can verify by using -> Docker images

<img width="757" height="119" alt="image" src="https://github.com/user-attachments/assets/88a3a761-5142-4c91-a1e4-340f11a1e784" />


















