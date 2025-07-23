
# Shell Scripting - Part 2

df | free | nproc | top
disk space | free memory on the disk | number of CPU's | Analyze node health status

df - available storage space on the VM
free - memory of the machine
nproc - number of cpu's of current machine
top - what are currently running processes, how many tasks are running at this point, stopped processes, sleeping processes, which processes are consuming how much amount of CPU, how much amount of memory.


![image](https://github.com/user-attachments/assets/493d4c35-0c7b-4aa1-9399-e0e25d5dbefe)

![image](https://github.com/user-attachments/assets/690f5892-1bc4-41eb-bf71-8af6b698159d)


![image](https://github.com/user-attachments/assets/1997030e-28e6-43f7-beeb-97ef287d5bb8)


![image](https://github.com/user-attachments/assets/1e75d83c-83ca-4b77-9ed0-d554f24d9adb)

![image](https://github.com/user-attachments/assets/1eae9add-c706-4e2b-96d3-f0848c2164e1)

![image](https://github.com/user-attachments/assets/135ea5c6-5b39-4f7a-8df9-2bb7669905d9)



Linux Command:

To get list of processes running on your Machine

ps -ef

![image](https://github.com/user-attachments/assets/1eabcc64-1347-4e0b-9a87-9c544e15400b)

ps -ef | grep "amazon"

![image](https://github.com/user-attachments/assets/8ef4dc09-8ed3-4086-8fac-1bee1adf5911)

| -> pipe command - sends the output of the first command to the second command

![image](https://github.com/user-attachments/assets/77343efa-2b50-4b92-8a92-4392bbf8362d)

![image](https://github.com/user-attachments/assets/9ed6266d-111c-48f2-b3a1-37db638b8b5e)



Shell commands to work on files:

-> Set -x  # debug    ----> this is to print your command in debug mode, and print the shell commands before displaying the output
-> ps -ef             ----> displays all the processes that are running on a virtual machine
-> grep               ----> filter some some information from the output
-> |    (pipe command)----> get the output from the first command and send it to the second command


# Interview Question
what is the output of this command?

date | echo "today"

Answer: today

why  is it displaying only - today

Reason:  date command is a system default command which sends it's output to stdin, however | (pipe) command receives the output from the previous command, not from stdin, that's why it only displays "today".

![image](https://github.com/user-attachments/assets/b7ad81e9-082a-43dd-91f4-c81417845097)



Linux Command:  awk - is a pattern scanning and processing language

awk - to ge process id from the row that we got from grep command

![image](https://github.com/user-attachments/assets/d961c019-3d6b-4065-9260-eefa2e19deae)





![image](https://github.com/user-attachments/assets/867a25be-27ea-453d-8f49-4419a14764da)

![image](https://github.com/user-attachments/assets/af599f8a-7022-4489-bf20-397de1ab61ab)

Awk command:
Awk - F " " '{print $4}'
![image](https://github.com/user-attachments/assets/5afe684a-4261-4c70-b93b-6768da5ec015)


![image](https://github.com/user-attachments/assets/902a3ac9-2aa9-4014-aac2-06b744584d3c)

![image](https://github.com/user-attachments/assets/eade9807-b596-4d9d-91a2-998e91735cc8)









