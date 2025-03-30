
# Linux Operating System & Basics of Shell Scripting




![Screenshot 2025-03-30 073432](https://github.com/user-attachments/assets/62e43f6a-a44d-47f7-bc3b-7dfee9aa8c4f)

Linux:
  Free
  Open Source
  Secure
  Contains lot of distributions: CenOS, Ubuntu, etc
  Fast
  
![Screenshot 2025-03-30 073949](https://github.com/user-attachments/assets/f86bbdae-cac1-4c41-a620-9dded954bd7e)


Kernel - communication b/w hardward to software (Heart of the Operating System)
1. Device Management
2. Memory Management
3. Process Management
4. Handling System related calls

System Libraries - responsible for performing a task

 Example: LibC, GNU - is an example of System Libary

 Compilers - OS will compile the software code

 ### Architechture of Linux Operating System

 ![Screenshot 2025-03-30 074844](https://github.com/user-attachments/assets/a032e709-e26e-4bc5-9dcb-915483d551b8)


## Fundamentals of Shell Scripting:

Shell - is a way to talk to your operating system

EX: Create a file - 
Command Line

In linux - you talk to your operating system using Shell Commands

Shell commands are common across different distributions:
CentOS
Fedora
Ubuntu

Now login to Ubuntu machine by using MobaXterm

![Screenshot 2025-03-30 075948](https://github.com/user-attachments/assets/a06a8c65-2a7d-4bc2-ae54-1ef7e9867968)


###Shell Commands:
ls - list
pwd - present working directory
cd - change directory
mkdir directory_name - make directory
rm -r directory_name - to remove directory
cd .. - go back to one directory
cd ../.. - go back to one more directory
cd ubuntu/bundle - go back to two directories more
ls -ltr - list of files with timestamp, owner, group owner, file or dir, permissions, etc

 if it starts with d - directory
 
![image](https://github.com/user-attachments/assets/79599f07-50a5-428c-82b6-3563e7ef7d27)

touch - create a file
vi file_name - to create a file and write content into the file
Esc + I - to write conent into the file
Esc + :wq! - to save the file

cat file_name - to print the file

free -  for looking into the memory

![image](https://github.com/user-attachments/assets/f3f33eaa-1ca4-4b64-90e4-5b29f939498d)

free -g    --- for better readability

![image](https://github.com/user-attachments/assets/14b9aa15-9129-441d-acf9-39c68794080d)

nproc - number of CPU's on your machine

![image](https://github.com/user-attachments/assets/08ebc12f-edac-4db4-a0d1-20ad98d7c52e)


df -h    ---- disk size

![image](https://github.com/user-attachments/assets/a101766c-7b79-49ab-b44a-6ab6d1542ef4)

top --- to find memory, cpu usage - monitor all at one place

![image](https://github.com/user-attachments/assets/e40e2dd8-92c6-49c9-934e-acf75f988616)

![image](https://github.com/user-attachments/assets/151bf8ff-2d42-4a92-a1da-dcc80bb78518)


### - Interview Question:
what is the shell command that you use to manage all memory, cpu utilization - all at one place?
Ans: top

![image](https://github.com/user-attachments/assets/a4c306eb-d03d-4980-912b-b3b326b6bf77)

![image](https://github.com/user-attachments/assets/93c58b78-ab69-41b3-a171-7625ecc42401)

![image](https://github.com/user-attachments/assets/c91bf060-6e65-41ab-8d76-2783bd243b36)















