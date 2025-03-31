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







