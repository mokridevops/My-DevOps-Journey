
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

Before pushing or raising PR, pull the changes and resolve conflicts locally.

