
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
main branch
develop branch
release branch
feature branch
hotfix branch

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

Git Squash: interactive rebase
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
This is used for shared/remote branches

