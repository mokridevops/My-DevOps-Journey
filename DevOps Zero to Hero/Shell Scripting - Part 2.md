
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



<img width="875" height="730" alt="image" src="https://github.com/user-attachments/assets/f65d56c8-3f6c-409c-a723-12bd2e125326" />

set -x # to enable debug mode
set -e # to error out when any step in the script fails, and not execute other rows
set -o pipefail  # set - e will only look for the last command in the script line,  for example:

the script is:


adfasdfasdfas | echo   --> set -e will execute without any issue

if the script is:

asdfasdfasdfas | echo | asdfasdfasdfas  --> set -e will error out --> basically it only looks for the last command and see if it is working fine or not, so we use ---> set -o pipefail



so, whenever you use set -e, you make sure you also use -> set -o pipefail










<img width="844" height="685" alt="image" src="https://github.com/user-attachments/assets/056cd833-0bd5-4bc8-b570-c4fcdd9b72ef" />

also people will write as:

set -exo pipefail - this is also correct, but it is not a good practice.


LOG FILES:



<img width="1373" height="489" alt="image" src="https://github.com/user-attachments/assets/ac905e14-b026-432a-9009-da9a942ef8f1" />


<img width="1398" height="748" alt="image" src="https://github.com/user-attachments/assets/563ed85c-9c91-4103-b556-ff16f700757c" />

<img width="845" height="82" alt="image" src="https://github.com/user-attachments/assets/675329c0-841c-414e-b6a6-2828b6bb40a5" />


<img width="875" height="180" alt="image" src="https://github.com/user-attachments/assets/f804c6da-98b8-41a0-9761-63a5aebb29a0" />

where ever there are more and more logs, people will usually upload them to --> Google storage, or Amazon S3 or Azure Blob storage

now, it is our responsibility to pull it from there:

<img width="1372" height="557" alt="image" src="https://github.com/user-attachments/assets/dce5e4ab-0d37-4421-b3a5-f2bc2db1694e" />

curl command retreives the information from Internet

<img width="1367" height="453" alt="image" src="https://github.com/user-attachments/assets/a615abc8-3394-4d86-8d98-2146873ab17f" />

curl storage_location_of_the_logs | grep ERROR



Another command: wget --> it downloads the log file to the local

<img width="1374" height="678" alt="image" src="https://github.com/user-attachments/assets/9164c3bc-8a3e-45ea-8d19-d8050ba3f188" />

Curl - shared the output to you
wget - stored the information in the log file in the local



<img width="927" height="156" alt="image" src="https://github.com/user-attachments/assets/ee4deeac-5411-4cf1-b28b-12a012f63368" />



<img width="1369" height="615" alt="image" src="https://github.com/user-attachments/assets/716682b0-0fc6-4681-934e-bf1b7e43e637" />

<img width="1370" height="298" alt="image" src="https://github.com/user-attachments/assets/a06d1b3f-af92-4d3e-837b-a9f16c53b7a2" />


# Interview Question

# what is the difference between Curl and Wget?



------------------

Another command:  Find
<img width="700" height="46" alt="image" src="https://github.com/user-attachments/assets/52bb69ae-0562-43d0-9dad-8a9a2fe34a62" />

find / -name pam.d

/ - is - find everything
-name - name of the file
pam.d - is actual file name


-----
# Root User

Root - is a powerful user - we can delete anything, if the file is deleted - if there is no snapshot and file is not mounted on a volume - there will be no backup


sudo su -       ---> sudo means - substitute user do

su - is switch user

<img width="752" height="288" alt="image" src="https://github.com/user-attachments/assets/457e2b67-0e88-4942-9d9b-d4bbf67d00a1" />


<img width="545" height="163" alt="image" src="https://github.com/user-attachments/assets/8bb49ffe-292e-48b0-89bb-cade862ae10d" />


sudo su -   ---> it will take to root user

sudo will give you sudo privileges

not everybody will be going to root user

always use - ubuntu user -> only when you need to use root user -> then only switch to root user




<img width="594" height="178" alt="image" src="https://github.com/user-attachments/assets/fc30251d-cbf8-40bc-81d1-3cae32e1ab3f" />

 when you type --- logout --- you will be switched from root user to the ubuntu user

 


<img width="949" height="325" alt="image" src="https://github.com/user-attachments/assets/e45a361c-2d36-4417-a670-265df4fa68e5" />


if we do --> find / -name pam   ---> we get access denied



<img width="884" height="278" alt="image" src="https://github.com/user-attachments/assets/74adce72-ed6e-45a3-9b18-ca7783d2dc97" />



<img width="1029" height="678" alt="image" src="https://github.com/user-attachments/assets/deaebdb9-468d-43d0-8b8d-0d9b639fceb5" />

<img width="730" height="326" alt="image" src="https://github.com/user-attachments/assets/6c619833-dfac-416e-b039-6782a1202399" />



#  if loop, ifelse loop, for loop

<img width="772" height="149" alt="image" src="https://github.com/user-attachments/assets/c859bbc7-7c59-40a1-9f02-f5bb1da7604c" />



<img width="433" height="308" alt="image" src="https://github.com/user-attachments/assets/f6f1a1cc-46c0-4796-85d8-5343361df9cb" />


<img width="534" height="349" alt="image" src="https://github.com/user-attachments/assets/5ca67e0b-8117-4d0b-97df-c435bd874748" />

<img width="665" height="431" alt="image" src="https://github.com/user-attachments/assets/d9d034d9-1601-4dc7-aaed-9cbcedd9677b" />





# iteraations -> for

for i in {1.100}; do echo $1; done

for 
do
     increment

done




# another command: trap

<img width="1115" height="583" alt="image" src="https://github.com/user-attachments/assets/e19cdd8e-e8e9-44f3-ac70-0e4d669ae418" />

trap ^C

trap "echo dont use the ctrl+C"  SIGINT^C
































