
# Docker Compose:

# Difference between Docker compose and kubernetes

Docker: Is a container platform, developed by Docker Inc
Main goal of docker platform : manage lifecycle of containers

Using docker platform
 -> install docker desktop
 -> install docker cli
 -> install VM

 using docker cli - start a container,
                    delete a container, 
                    run background process




Suppose we have - Python Flask application - which runs a calculator
Developer asked DevOps engineer to containerize the application

Steps:
1) Create a docker file - sit with developer and  understand what goes into docker file, decide on base image
   Using RUN - install all dependencies that are required in the docker image
   export a port - if needed
   CMD - or EntryPoint -> you will provide the process that needs to be executed, when the container is started

2) Create the docker image:
   login to VM
   Run the docker command: docker build ...parameters
   Run the docker container - which is python flask application, you will use the command
   Docker run -p ....  -v .....
   p - parameters
   v - volumes

   3) docker ps -> to verify the state of the docker container
  
Docker is fine to manage the lifecylce of entire container, why should i need docker compose?

Docker Compose - tool developed by Docker Inc
Docker Compose - used to manage - multi container applications

multi container applications?
-> E-Commerce application
   -> it has multiple microservices
   -> lot of databases
   -> messaging queues
   -> cachine service


   Redis
   Mysql
   python appl
   python login
   python payments
   python transactions appl

   How would you manage life cycles of all these containers at once

   you can individually run docker build for each of the above applications

   you can individually run docker run command with dependencies for each of abvoe applications

   dependencies: payments application should only be installed if database is up and running
   if database is not avilable, most of the applciation will not display certain items, which is waste

   you might want to mount volume for each of these applications


  So, you prepare a shell script with all the above docker commands and provide it to the developer, so they can execute this shell script in different envirnonments when needed.


  If there are some changes - 6 months later in the docker commands, you know those changes - but giving back to developer again is not a complete declarative approach.  Instead provide the developer with just one single YAML file, it would be great!

  Instead of running 20 docker single commands, if you have just one single YAML file, which is standarized YAML file , provided by docker, which provides backward compatibility, which does not break when there are new changes - that's where docker-compose comes into picture.

<img width="1823" height="847" alt="image" src="https://github.com/user-attachments/assets/54ecff12-ae41-4f81-8e05-676341f0f0ce" />


  ------------------------------------------

  3 tier architechture demo:

  

  <img width="1747" height="981" alt="image" src="https://github.com/user-attachments/assets/cfd91fe1-b4a5-4362-9719-563470f9478e" />

  there are 12 services - deploys complete ecommerce application


If the developer is trying to fix an issue, he is doing trial and error to fix the issue, as he is also not sure - what is causing that issue.

Then every time he has to run each time - docker build, docker run, etc for all the 12 services which are not at all impacted by the fix, then it is simply waste of time.  If something goes wrong, he has to delete all the containers, which is very tedious process. 

Instead as a devops engineer - you write a simple - docker-compose.yaml file



  

  

  


   


    





