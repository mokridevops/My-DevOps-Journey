# Ansible Zero to Hero

sudo apt update

sudo apt install ansible

<img width="1094" height="265" alt="image" src="https://github.com/user-attachments/assets/9230cb74-a219-4ddc-a716-fa9c62deefeb" />



<img width="1400" height="684" alt="image" src="https://github.com/user-attachments/assets/f2e20144-2a21-470c-9934-4383cc5a12fd" />



<img width="975" height="163" alt="image" src="https://github.com/user-attachments/assets/9f1d6564-fb44-4930-bc5f-52e59927c6ec" />

once ansible is installed, you would need one more server, i.e using the server where you have ansible, you will configure the other server



<img width="1396" height="327" alt="image" src="https://github.com/user-attachments/assets/02c81594-fd18-4552-b30e-677edf0f89a1" />


Ansible requires is that passwordless authentication, then Ansible can configure anything on the server

 since both the servers are in same  Amazon on EC2, always talk to private IP address

 
  <img width="941" height="278" alt="image" src="https://github.com/user-attachments/assets/b8ed848e-60e7-4c64-beef-d3a66f013871" />


  ssh-copy-id 172.31.62.28 - this will make it passwordless, but not always ssh-copy-id will work due to permission issues, so we follow other route

  we use ssh-keygen

  <img width="1012" height="340" alt="image" src="https://github.com/user-attachments/assets/0769b637-ebfd-4143-8d6b-767bff63c0a9" />

  <img width="1119" height="724" alt="image" src="https://github.com/user-attachments/assets/c425481b-9619-4fab-93ae-81365715602a" />


this directory get created with ssh-keygen

<img width="826" height="206" alt="image" src="https://github.com/user-attachments/assets/d72f3517-8dc5-4779-840f-0354fd08631f" />


id_rsa - private key

id_rsa.pub - public key

<img width="1437" height="521" alt="image" src="https://github.com/user-attachments/assets/ab63c94d-6b93-4fd9-b0a0-7185617a5c77" />

<img width="1897" height="803" alt="image" src="https://github.com/user-attachments/assets/01d18496-3f6c-452c-bb05-2abedfff0ef7" />


ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDGAAsKaJgdsqNu2xNHAFZr9utqpGrt+UI59PIrJeo3mRL0EV3awDrY+PyFjtWqffPrPfkmx9go+18uPdIO4kLlCUDiWUv+1QNUl07ipV6RKh3OXsPnlkmDkFlQTZKpNsgplx63p1nwVzk7atOnky4RalKZ3Dm9rh4cHu3mulO9b+AoXK26cLISSbIxDJsS7KzjRPuW/HOm5HX2OyusJSLUfMWmvO+Y5L3g44HWBdrzqzpUF2rFuYjd2KQdU5jZG+4S8TVJBsDpuWnGGzrl/LYoq0OaHHg7Lv3MHe52/Ytpv8JXGPOG7c45P46txhrrx8gN5Ko392NO76/Xjys6vvEIZ7wQK8h4DgvQUFOMdv73x0pNXXGfQtHFhao4zQ0oD1Q/EgvMprBfk9/cmqdTsKGNCLTrEzinh4l/7GyOlpxF9RZAwEwFMFp2HnQkNJK0iqauyXVP9URw4c+tONzp/orjM0mXRj1k2a3Qw16vGkXnAgzc1ta93Ovgy9h6fZ3yUBk= ubuntu@ip-172-31-82-122


now login to second target machine










  


  
