
# Multistage Docker Builds


<img width="1607" height="1011" alt="image" src="https://github.com/user-attachments/assets/8bdbd7dd-ef91-4735-8916-4f8a28e9a359" />

For a beginner, this docker file is very good, but there is a problem with this docker file:

 The problem is - you would only require a python runtime to run this application, but this docker image that is created has 100 other things, it has Ubuntu base image - that means will come with lot of system dependencies, apt packages, apt repositories, it has lot of overload on your simple docker image on 


<img width="1182" height="757" alt="image" src="https://github.com/user-attachments/assets/2afd35fb-6dbb-4a65-83fb-b1c4c0c7bcd6" />



# Multistage builds

<img width="1097" height="682" alt="image" src="https://github.com/user-attachments/assets/8ee8d1cb-ff0c-4e58-9c15-7b833474e952" />


Advantage: you have reduced your image size significantly

all the stage 1 content will not be in your final image

stage 1 will be only part of your build image

stage 2 will be your final image

So, final image will have the following:

1) Python run time
2) Binary of the build stage
3) Executable


    What is the fundamental advantage of Multistage docker build:

   Lets take complex application that has front end, back end and DB related stuff - 3 tier architechture application

   React
   Java
   MySQL


   Base Image:
   
   From Ubuntu         ---> 400 MB
   Java dependencies   ---> 100 MB
   React dependencies  ---> 200 MB
   MySQL dependencies  ---> 400 MB

   Build Java application
   Build Front end application
   EntryPoint [/app.ear]


   this could be our output - this docker image will go crazy and it will be around 1.5 GB


   Final Image

   From OpenJDK:11          ----> 100 MB
   Copy --From build        ----> 50 MB
   EntryPoint [app.ear]


final image size will only be 150 MB

so, you reduced the docker image size from 1.5 GB to 150 MB - 10 times reduction in size - great achievement!

This is the advantage of multistage docker build

<img width="1196" height="722" alt="image" src="https://github.com/user-attachments/assets/9168a01d-a9da-45bd-b115-8a310314057f" />


 # Multiple stages:

 Front end stage
 Back end stage
 Final end stage  --> final docker image

 <img width="1132" height="673" alt="image" src="https://github.com/user-attachments/assets/80f7af6d-67cb-4538-8254-a818c0fd93b1" />


 # Interview question:

 1) what are the number of stages that can be in a multistage docker build?
    Ans: Countless number of stages, there can be n number of stages, but there will be one final stage, which will be a minimalistic image


# Distroless Docker Image:

Distroless Docker image - is a very minimalistic image - that will hardly have any packages

for ex:

Python distroless image - will only have python runtime, nothing else


there are another type of images:

Golang -> these are statically typed application - they dont even require run times -> so you dont require a Go run time for executing Go application

so you drastically reduce your docker image to 10 MB or 15 MB size



# What is a Distroless Image:

Ans: Distroless image is a very minimalistic or light weight docker image that will have only the run time environments.

Biggest advantage of having distroless image is -> very high Security + reducing drastically the container image size.



# what is one of the production issue that you faced with docker containers and how did you resolve it?

Ans: Previously we were using Ubuntu base images or python run time images or any other run time images, which were exposed to some king of vulnerabilities by hackers, or people used to have some kind of issues with these images, so we moved to Distroless images.

for example: In our organization, we moved to python distroless image, which only had python runtime, because of which even it did not have basic packages like find, ll, wget, curl, etc -> so it was providing us highest level of security.   After implementing Distorless images we are safe to say that - our applications are not exposed to any OS or operating system vulnerabilities.

Suppose, if we are using Golang based distroless images, then we are 99% of times not exposed to vulnerabilities, as they don't even have run time environment.

<img width="1197" height="718" alt="image" src="https://github.com/user-attachments/assets/15e3c931-6b08-4f4b-8b1c-66d1929d6ab6" />










    


    


    

 

 

 
