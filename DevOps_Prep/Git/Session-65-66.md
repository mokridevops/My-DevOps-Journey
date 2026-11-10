
Git:
====

Create repo
clone repo
adding files
adding files to stagging/temp area; commit to local repo; push to remote repo;
pull the changes
add origin


branch:
=======
master
main -> always pointing to production

we create new branch, we do changes and test in all environments

merge vs rebase
===============
1. merge creates one extra commit with 2 parents called as merge commit
2. merge preserves history of changes

rebase:
=======
1. rebase will not create extra commit
2. it will not preserve the history, it has linear history like main branch moved ahead alone
3. it will rewrite commits




<img width="1269" height="637" alt="image" src="https://github.com/user-attachments/assets/2d1e04c0-7b98-47af-9cf7-bece42229177" />

use merge, if a branch is used by multiple users.
use rebase for private and local branches.

<img width="999" height="437" alt="image" src="https://github.com/user-attachments/assets/73746193-1476-4741-bbf9-069d72701fab" />


Git Conflicts:
==============

While merge if git finds different code in the same line number, then git give conflicts. It is the developers responsibility who developed this code to resolve the conflict.

eggdosa-suresh
eggdosa-ramesh

Before pushing or raising PR, pull the changes and resolve conflicts locally by merging main branch on to local branch.


Branching Strategy:
===================
Feature branching strategy or GitHub Flow

main/master and feature branch

main/master -> long lived branch
feature branch -> short lived branch

whatever change we want to do, we create feature branch.  When development is completed, we create PR to bring the changes to main branch.  If we get conflicts we resolve them.

We can do the deployment into DEV, UAT, PROD from main branch.  When PROD is success, we can tag the commit using our version. v1.4.0

In olden days - around 10 years ago, people were using:
main branch <br>
develop branch <br>
release branch <br>
feature branch <br>
hotfix branch <br>

-> Same code across all the environments, configuration can be changed.


-> When there is any emergency release, developers do the changes in feature branch, and then merge to main branch, then deploy it in DEV environment, and test it, if everything looks good, directly deploy it in PROD environment.



  Git reset:
  ===========
  Reset the code already committed. Undo the local commits.  This is only useful for local branches:
  1. Soft -> code comes to staging area
  2. Mixed -> code comes to workspace
  3. Hard -> code will be deleted

     > git reset --soft HEAD~1
     it pulls the code from committed state to stagging area, HEAD~1 -> means 1 commit before

     <img width="1095" height="934" alt="image" src="https://github.com/user-attachments/assets/70d3064e-3163-4553-b982-e1088739570e" />

> git log --oneline
<img width="1110" height="667" alt="image" src="https://github.com/user-attachments/assets/8b3ee45b-2dfd-4996-b77f-f855107afb44" />

<img width="984" height="227" alt="image" src="https://github.com/user-attachments/assets/96d0ec0f-c248-43c6-9dbc-93d263bfe4d1" />

> git reset HEAD~1  -> this is mixed -> it is bringing the committed code to workspace.
<img width="1008" height="348" alt="image" src="https://github.com/user-attachments/assets/e02a651b-fa7c-4a57-a4a5-ef90bf36f306" />
<img width="1032" height="595" alt="image" src="https://github.com/user-attachments/assets/87e09919-2172-404a-b4f6-9ef136394b15" />



<img width="1068" height="243" alt="image" src="https://github.com/user-attachments/assets/5037b0e1-b148-475e-8470-b677d4a15bba" />

> git reset --hard 28bf896

<img width="1074" height="728" alt="image" src="https://github.com/user-attachments/assets/0e3eed0a-3bd3-4f79-a10f-978412431d1d" />

<img width="821" height="442" alt="image" src="https://github.com/user-attachments/assets/65399dd6-c5b7-4ddd-8c46-8c296bdfab33" />

<img width="999" height="573" alt="image" src="https://github.com/user-attachments/assets/6b0d52b8-4ee9-42ee-856f-ab88515bca0a" />

Git Squash: or interactive rebase
===========
<img width="1107" height="618" alt="image" src="https://github.com/user-attachments/assets/6d79a97e-adf3-4cc5-a996-e9bc86788795" />

We can combine multiple commits into single commit using squash.  But don't do this for shared branches, do this only for private branches.

git rebase -i d4c10f5

<img width="1036" height="608" alt="image" src="https://github.com/user-attachments/assets/95e1f943-ee43-464a-aef4-315151799d48" />

<img width="922" height="753" alt="image" src="https://github.com/user-attachments/assets/4bb6e049-4557-49c6-b42a-a89c3a3d3e18" />

it picked those three commits

pick 8bf896 (HEAD -> masala-dosa, origin/masala-dosa) Aloo masala added
squash 5389532 Oil added
squash 3972056 Dosa Batter added
give proper commit message for this squashed commit.



Git Revert:
===========
This is used for shared/remote branches. If we want to undo changes which went into shared branches already, we can use revert.  This will not undo the commit. This will create extra commit correcting those changes.

History is preserved, nothing is rewritten...

<img width="1564" height="979" alt="image" src="https://github.com/user-attachments/assets/5d975f2e-f08e-49bd-8978-c34d8c8f4078" />

<img width="1261" height="334" alt="image" src="https://github.com/user-attachments/assets/86dcc0fe-bdb1-42bd-91b1-f782b0e7b792" />

<img width="1138" height="356" alt="image" src="https://github.com/user-attachments/assets/1418f29c-977f-4dc6-aae6-455740876ba5" />

<img width="1340" height="662" alt="image" src="https://github.com/user-attachments/assets/cb097fd6-2a44-4b90-bc24-f6bfa505fdba" />


Note: Git reset - for local branches, Git Revert for shared/remote branches.



Git Cherry pick:
================
if the required code is already developed, then we can pick that code using cherry pick, we will get new code added using that commit.

c1
c2 -> extra code added as part of this commit

> git cherry-pick c2

<img width="928" height="758" alt="image" src="https://github.com/user-attachments/assets/7a0136a7-8d17-408d-8544-6c6fb51d5fef" />

> git cherry-pick afffd23

you will get conflicts, you need to resolve

<img width="1117" height="322" alt="image" src="https://github.com/user-attachments/assets/ce7f5ac9-43ee-44d0-ab2d-e4401e6d2616" />

<img width="1760" height="971" alt="image" src="https://github.com/user-attachments/assets/076e4402-3ae6-4aab-864a-1f2462deabd3" />

<img width="1354" height="983" alt="image" src="https://github.com/user-attachments/assets/04364ea0-523f-403d-afa6-5bbd64b6a603" />


<img width="1135" height="351" alt="image" src="https://github.com/user-attachments/assets/9cee6066-4fbd-442a-9f0c-f20cad7d0734" />

<img width="1819" height="895" alt="image" src="https://github.com/user-attachments/assets/8fa2ff0c-43df-4259-a776-c6fbf87418fc" />

<img width="1884" height="954" alt="image" src="https://github.com/user-attachments/assets/3058a705-d0e4-44f9-8907-34642256fca0" />

<img width="1800" height="931" alt="image" src="https://github.com/user-attachments/assets/2e9d9e58-9802-451d-a46e-590d7a439cba" />

<img width="1699" height="936" alt="image" src="https://github.com/user-attachments/assets/01e44916-0125-43be-a9d2-44adf32fba60" />

<img width="1699" height="936" alt="image" src="https://github.com/user-attachments/assets/eac5b681-84c9-4aa4-9138-776ec14abb1f" />
<img width="1750" height="965" alt="image" src="https://github.com/user-attachments/assets/96488ad4-3af9-49a4-a01a-5baf49941f05" />

<img width="1844" height="840" alt="image" src="https://github.com/user-attachments/assets/8a9b6b5a-baea-4ebf-95a4-0c56e1e90518" />
<img width="1740" height="875" alt="image" src="https://github.com/user-attachments/assets/1dd4092b-c000-4160-996c-c6604a91cfac" />

<img width="1849" height="949" alt="image" src="https://github.com/user-attachments/assets/f7e1ade3-2b1e-43ba-83d9-c47bc9911c48" />
<img width="1405" height="905" alt="image" src="https://github.com/user-attachments/assets/1f93bc55-fa75-401c-9bea-8151b54ef92f" />


git stash:
==========
We are actively developing a code, suddenly we got emergency defect in production, we can stash current changes and move to another branch to fix the production issue.
<img width="922" height="548" alt="image" src="https://github.com/user-attachments/assets/8b3343a4-9783-4fe8-adf2-c46b60dd278c" />

<img width="1104" height="977" alt="image" src="https://github.com/user-attachments/assets/9dba8b14-ceb3-484a-a63b-99de6363ea4e" />
<img width="1106" height="676" alt="image" src="https://github.com/user-attachments/assets/e3a75411-934b-438e-98ac-770eda2b856d" />

i pushed the code to my local branch, now suddendly i got a defect to fix in production

so, I have to go to main branch, and create a new branch from that branch

so, if i give > git checkout main
it will not allow, as we have pending items that needs to be checked in or pushed to main

<img width="1192" height="751" alt="image" src="https://github.com/user-attachments/assets/c9219825-d004-476c-a7be-1359b4948e8c" />


now, two options:
1) either you commit your changes
2) or stash your changes


I dont want to commit because, I have not yet reached to a good standard base in my coding, so I would stash the changes for now

<img width="1046" height="690" alt="image" src="https://github.com/user-attachments/assets/c0744969-ccde-4bd7-8638-48bb410386a0" />

now, you can go to main branch and then create a new branch from there

<img width="1049" height="270" alt="image" src="https://github.com/user-attachments/assets/5ab0248a-03e7-4ad0-9456-108da7c3317f" />

once you are done with fixing the hotfix branch, you will go back to your original branch - i.e. egg-karam branch

<img width="1056" height="415" alt="image" src="https://github.com/user-attachments/assets/ab50cf3d-d1fe-412e-a85a-888180d16b26" />

to get those changes back from stash to our workspace -> > git stash pop

<img width="956" height="319" alt="image" src="https://github.com/user-attachments/assets/31a3fa73-8c3e-4c1a-afad-c13f169ee0eb" />





