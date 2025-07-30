# Git Interview Q & A and Commands for DevOps


<img width="921" height="130" alt="image" src="https://github.com/user-attachments/assets/d19fc206-39db-45a9-8b07-0f2a93341b32" />

# Interview Question:
how to create or initialize a git repository:

git init


once you do - git init
and do ls -a
you will see -> .git file listed, before doing git init, this file will not be there



<img width="901" height="335" alt="image" src="https://github.com/user-attachments/assets/0980c6f7-a40f-4d30-98d8-213798f51f3c" />


to prevent - developers from mistakenly push password or secrets to git,  write a pre-commit hook

<img width="686" height="232" alt="image" src="https://github.com/user-attachments/assets/d0597f37-1372-44f9-91ca-b78beebf4c8f" />


it will block the developer from commiting the code after the pre-commit statement

<img width="902" height="412" alt="image" src="https://github.com/user-attachments/assets/423a568b-662a-4f63-9690-52b2f49631a6" />

<img width="576" height="127" alt="image" src="https://github.com/user-attachments/assets/633d1750-1735-4961-a24f-50b24e56e3f5" />


<img width="615" height="276" alt="image" src="https://github.com/user-attachments/assets/ea5fe318-ba69-44be-b4b9-9d74eb15e94b" />

you can use - git checkout calc.sh - to remove the file from git



<img width="641" height="408" alt="image" src="https://github.com/user-attachments/assets/4691e476-ca72-48fe-a36c-96d83c789fd8" />

<img width="820" height="642" alt="image" src="https://github.com/user-attachments/assets/2615de47-cc90-4235-84b1-d27e0f29ef16" />

git log - git will show you list of commits



<img width="380" height="77" alt="image" src="https://github.com/user-attachments/assets/6ef65ae4-2138-4241-8b12-c59af263df94" />

<img width="758" height="172" alt="image" src="https://github.com/user-attachments/assets/0d9d91e6-2afc-4518-b4b1-8bfae6918c16" />


<img width="560" height="202" alt="image" src="https://github.com/user-attachments/assets/0da8b3c9-8cbd-4283-be33-b923bfecb445" />


git push - now put the code from local to github - for every body to access - to push to git repository - either github, or bitbucket or any self hosted repository

# Interview question

# what is the git workflow that you use in your organization

git add && git commit -m " " && git push


<img width="1273" height="594" alt="image" src="https://github.com/user-attachments/assets/7eac6d36-95ab-40f3-a6e9-9daee449c150" />


<img width="1302" height="494" alt="image" src="https://github.com/user-attachments/assets/15372407-2842-482a-bb93-e0ce643eb55c" />





<img width="595" height="152" alt="image" src="https://github.com/user-attachments/assets/84e40466-b4a8-43b0-9372-50127de091a3" />



<img width="1029" height="605" alt="image" src="https://github.com/user-attachments/assets/3df2bc3f-53e9-499d-ba53-e9a43b47918c" />


to push to a remote repository that is already present:

<img width="1784" height="915" alt="image" src="https://github.com/user-attachments/assets/dc357142-bbf3-4e02-b8e0-7136de00c107" />

you clone the repository


<img width="818" height="270" alt="image" src="https://github.com/user-attachments/assets/e3e79252-2edd-4290-b712-7a79a0dafe68" />




# Interview Question:

# How to pull code from github

git clone



<img width="1273" height="617" alt="image" src="https://github.com/user-attachments/assets/cbcc2f5f-27fb-4f4b-bcee-756665c6e2ef" />

3 ways to clone:

https

<img width="907" height="89" alt="image" src="https://github.com/user-attachments/assets/343a2527-6db3-4947-9ec5-4e6d3ac1166e" />


ssh

<img width="1279" height="675" alt="image" src="https://github.com/user-attachments/assets/cac33995-f981-48e9-8bae-52c51ca02807" />


when you are using ssh - you are authenticating using public key, https - you authenticate using your password

to generate your ssh public key

ssh-keygen -t rsa

<img width="1176" height="387" alt="image" src="https://github.com/user-attachments/assets/6b37f4e3-0641-4b8c-900a-bce1437f3e91" />

id_rsa.pub is the public key

open the id_rsa.pub file and then paste in the settings of the github UI

<img width="1299" height="727" alt="image" src="https://github.com/user-attachments/assets/d027facd-7ff5-4689-85ab-cf843161130c" />



<img width="1293" height="721" alt="image" src="https://github.com/user-attachments/assets/c3dd0833-fc82-4e4b-880a-c645fc39b097" />

copy the contents of id_resa.pub in to Key text box


once you add ssh public key on the UI settings - from next time whenever you clone using ssh mode - it will not ask you for the password from next time.


# Interview Question

# CLONE vs FORK

CLONE: download a specific repository

FORK: is to create a copy of a specific repository.  If we fork a repository today, then that is the latest code that we have and we can work on that repository and make our own changes we will never get any udpates

if we CLONE - it will download the repository and also our repository can be updated regularly by using git pull

due to FORK - we call git as distributed system





<img width="473" height="85" alt="image" src="https://github.com/user-attachments/assets/9a76ead0-1d7d-4f11-86cd-d6ff84316355" />

'cd -'  will show you your repository



--------------

to create branch

git branch

git checkout -b division  : division is new branch


<img width="509" height="107" alt="image" src="https://github.com/user-attachments/assets/5107ac9b-3cff-4e82-bd2d-ac4a14de5a53" />

gitdemo git:(main) git checkout -b 

the above means: create a branch from main branch 














github cli










