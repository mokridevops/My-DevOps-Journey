#  Shell Scripting for DevOps - Part 1

to create file on Linux machine:
touch first-shell-script.sh

![image](https://github.com/user-attachments/assets/0f92b25c-b30c-448a-829f-fbac5299a523)



Linux command:

man ls    (man stands for manual) - prefix any command with - man - it will give the details about that command

man touch
 
  ![image](https://github.com/user-attachments/assets/24e77fe8-760a-460d-94b7-30aae2d0d6da)

  
To wirte a shell script:
 1) Open the shell script file - vi or vim command

![image](https://github.com/user-attachments/assets/2ebb73c1-51da-4f1e-bb1d-5cea201b8cb1)


## Interview Question
If we are able to create a file using - touch command, and then user vi to create and open the file, or directly use vi to create and open the file, then what is the use of touch commmand?

Answer: 
Touch command is used in automations, Vim is used to wirte inside the file, but for automations we need touch command to create a file, we dont need it to be opened, and we will be having some thousands of files, for which when we automate - we cannot use the command vi file_name, as in automation it will create 1000 files, and opens 1000 files, which can make the system hang.




![image](https://github.com/user-attachments/assets/0dc1bdb1-98bf-4894-9bb7-8cde1c8cf999)

INSERT

#!/  --- this is called shebang

#!/bin/bash
#!/bin/dash
#!/bin/ksh
#!/bin/sh

--- the above is the first line in any shell script -- these are different executables of our shell script


Linking:

#!/bin/sh ----> redirects to #!/bin/bash, this is called linking (this is done previously - may be around 2 years ago)

these days ---> some of the operating systems like Ubuntu, they have started linking -> #!/bin/sh to #!/bin/dash

so, if you want to use bash, directly write like this:   #!/bin/bash, instead of using #!/bin/sh, since sh is linked to dash, not bash


## Interview Question:  

What is the difference between #!/bin/sh and #!/bin/bash?

Answer: previously both are same as #!/bin/sh is redirected to #!/bin/bash, however in recent years, #!/bin/sh is redirected to #!/bin/dash, so our script might not execute if we use bash scripting where dash is default.



![image](https://github.com/user-attachments/assets/ebadd716-284a-4123-a976-d8905bead47d)


![image](https://github.com/user-attachments/assets/b96132fb-f018-43fc-b82a-64a483b7c64e)



Linux Command:

Cat first-shell-script.sh ---> to view the contents of the file

![image](https://github.com/user-attachments/assets/a8f3cbda-c0fe-4c8e-86f0-64082d33d0b5)


How to execute the file:

sh first-shell-script.sh

or

./first-shell-script.sh

![image](https://github.com/user-attachments/assets/f1ce5da6-5677-4df6-910c-5266a136641f)




Linux Command to grant permissions:

chmod -> grants permissions


![image](https://github.com/user-attachments/assets/b4817b10-1c96-4e6b-b738-bbe6ac57a4a6)


chmod - is divided into 3 categories:
-> what are permission for admin user?
-> what are permissions to the group?
-> what are permission for you?


chmod 777 first-shell-script.sh -> this means granting the access to eveybody, now you can execute the file:

![image](https://github.com/user-attachments/assets/3212c0d1-6c20-47f6-9cd4-4c88278f89d9)


![image](https://github.com/user-attachments/assets/68677021-3f8e-47a3-8d74-9db6d88445e3)



![image](https://github.com/user-attachments/assets/0c485743-7e3b-4484-a223-cc90a95481a6)


![image](https://github.com/user-attachments/assets/38e04302-0459-49c2-ac5d-4740638d8b18)


![image](https://github.com/user-attachments/assets/0e53b6f4-75d8-4664-aa6d-0f6463f4902a)


Linux Command:

history

![image](https://github.com/user-attachments/assets/6a7109ee-a997-47a1-a869-4292609682bc)



![image](https://github.com/user-attachments/assets/49458418-a3d7-4139-a2a0-d8631bba86e1)




![image](https://github.com/user-attachments/assets/ceea656e-6ee8-470c-b5c5-e56d022a90f8)



![image](https://github.com/user-attachments/assets/e44df2e8-c394-4509-bfc0-a66015b76265)

![image](https://github.com/user-attachments/assets/5b2f9ddb-01a9-4ebd-a907-acfda2822761)


![image](https://github.com/user-attachments/assets/9eca73fd-a1e1-41c7-95c5-4a91b06efd0a)

![image](https://github.com/user-attachments/assets/6451420b-fb02-4b7c-a54d-53a2f968047b)

![image](https://github.com/user-attachments/assets/9eb88d17-d4b0-413e-af74-0178bf86ac9f)










