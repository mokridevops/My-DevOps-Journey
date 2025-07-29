# Git and Github


<img width="1510" height="931" alt="image" src="https://github.com/user-attachments/assets/73271342-299c-4f17-a213-a15dba98ead4" />


<img width="1398" height="562" alt="image" src="https://github.com/user-attachments/assets/d5afb536-1547-4962-997e-0f13edc12809" />


# Interview question:
# what is the difference between Centralized vs Distributed Version control system? and how is GIT solving the problem?

<img width="1477" height="852" alt="image" src="https://github.com/user-attachments/assets/a9fa1d94-dd29-4588-ab74-b906593c1f86" />

SVN - is centralized version control system, if the Central Version control server goes down, then there won't be any communication between the two developers who are working on the same code.


In distributed version control system - you can copy the central distributed system and make multiple copies



<img width="802" height="400" alt="image" src="https://github.com/user-attachments/assets/6aeda28a-e3fc-4d2a-a134-4f8f6ffddc66" />





<img width="1457" height="947" alt="image" src="https://github.com/user-attachments/assets/cd6e92d1-cef0-49a2-b9d2-fe457fd3ec26" />


<img width="1481" height="938" alt="image" src="https://github.com/user-attachments/assets/7f0b1228-e3ad-49b0-80af-dc2a4ac6e26f" />

# Interview Question:

# What is a fork?

Fork is nothing but, you create an entire copy of your original source, 


for ex: example.com

you creating a copy of example.com, where Abhishek is the name of my git repository.

Fork Abhishek, will create a copy of the git repository, if the main repository is down, then also the developers can communicate and share the code since they have the copy of the repo.



<img width="1481" height="957" alt="image" src="https://github.com/user-attachments/assets/3ac33222-9d1d-4316-8548-ad484ac6d07f" />

Git Vs Github:

Git : is the version control system, Github is a wrapper on top of git to solve many issues and providing capability for: Reviewing the code, commenting, usability, project management, etc



###  Git Commands:

Install Git:



<img width="1440" height="969" alt="image" src="https://github.com/user-attachments/assets/3d84b8f3-90ae-447d-aebd-d3c208347a6a" />

<img width="673" height="784" alt="image" src="https://github.com/user-attachments/assets/2f4c78c7-6c9c-4370-a45f-3292b357134c" />



to install git on Linux:
# apt-get install git

git init - to initialze an empty Git repository


<img width="965" height="510" alt="image" src="https://github.com/user-attachments/assets/186a491f-9c8d-4638-a982-2a1af9661917" />


<img width="676" height="448" alt="image" src="https://github.com/user-attachments/assets/86ed9025-e693-41bf-b85c-8a68b21aa3d7" />


after you intialize an empty git repository, a hidden .git file is created which is in blue color, essentially it tracks every thing using this .git file

never delete this .git file, if you delete it will not track the changes


git add, git commit, git push



three commands that every devops engineer should learn:

basically life cycle of git:

<img width="1152" height="580" alt="image" src="https://github.com/user-attachments/assets/f418d7bd-ef79-45ad-b6dc-80d20ee02d8d" />


<img width="681" height="111" alt="image" src="https://github.com/user-attachments/assets/a77fcb01-de4c-4a9a-a84b-0595945fcb99" />

these are the things that git uses for tracking and commiting this entire repository


refs and objects - every file that you create inside git - is tracked as objects 
hooks - is a folder - ex: if someone unintentionally commiting some passwords or tokens, using hooks you can prevent such things
config - to configure your git credentials, secure git repository which need secrets, or TLS or certificates
HEAD - 


git status - 
 
<img width="1287" height="449" alt="image" src="https://github.com/user-attachments/assets/a7afd834-88b9-4d3d-acf8-e6d3d86614f9" />




<img width="1084" height="664" alt="image" src="https://github.com/user-attachments/assets/2eaf077d-02cb-4404-be88-784f1f08cefb" />


git add  filename -

git diff - to track the differences after the file is added to git and then doing some change to the file after adding the file to git

<img width="595" height="397" alt="image" src="https://github.com/user-attachments/assets/ea9ddd8b-46be-4d5f-9922-8440a6ed8383" />

<img width="961" height="380" alt="image" src="https://github.com/user-attachments/assets/b8f77719-b448-4de0-a5ba-d1ec1a0863a9" />

it is saying - you added a new line + echo a+b

<img width="941" height="268" alt="image" src="https://github.com/user-attachments/assets/a861307d-42e4-4ca1-a41a-0353417fbc6b" />


<img width="905" height="678" alt="image" src="https://github.com/user-attachments/assets/689b85e1-8dd3-4861-8094-9a0f00350b8a" />





git commit -m "comments"

git diff

git status

git log





<img width="1036" height="149" alt="image" src="https://github.com/user-attachments/assets/3f35bee8-f5af-475f-9c63-a20df01f9732" />




<img width="429" height="45" alt="image" src="https://github.com/user-attachments/assets/3303f7d5-54c4-436d-ae48-78ae5e01a076" />



<img width="892" height="338" alt="image" src="https://github.com/user-attachments/assets/bfbca952-6361-4fc3-8f8c-51a575c37e69" />

if we want to go back to commit number 1:

git reset --hard commit number 1

<img width="702" height="321" alt="image" src="https://github.com/user-attachments/assets/513b0096-4d8d-411a-9e40-b356bd37c478" />



<img width="929" height="159" alt="image" src="https://github.com/user-attachments/assets/cf390796-dafe-41d0-a946-3128b4bfcd55" />


so using git, you can switch to any previous version


<img width="735" height="98" alt="image" src="https://github.com/user-attachments/assets/3dd6b000-fbbb-42e6-a161-75e02c514a89" />










