
# Kubernetes:
<img width="652" height="329" alt="image" src="https://github.com/user-attachments/assets/05cad8cd-4f92-48e5-910b-f10be8fe6ef5" /> <br>


<img width="247" height="179" alt="image" src="https://github.com/user-attachments/assets/9f6c2a3d-6217-49f7-a733-2d43ed321d54" />


### Docker installation instructions:

sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/rhel/docker-ce.repo -y
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
sudo usermod -aG docker ec2-user

<img width="943" height="524" alt="image" src="https://github.com/user-attachments/assets/5468ea65-1b92-4baf-9068-ac16efcdbf4e" />

### eksctl installation instructions:
# for ARM systems, set ARCH to: `arm64`, `armv6` or `armv7`
ARCH=$(uname -m | sed 's/x86_64/amd64/' | sed 's/aarch64/arm64/')
PLATFORM=$(uname -s)_$ARCH
curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"
tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz
sudo install -m 0755 /tmp/eksctl /usr/local/bin && rm /tmp/eksctl

<img width="698" height="528" alt="image" src="https://github.com/user-attachments/assets/64a07e71-1a90-40a3-9b5f-aa4609892b75" />


Note: we are adding eksctl to /usr/local/bin -> that means it will be globally accessible.

<img width="913" height="503" alt="image" src="https://github.com/user-attachments/assets/798f2572-b0ba-4785-950d-fa80c42bd4ac" />



### kubectl installation instructions:

<img width="680" height="530" alt="image" src="https://github.com/user-attachments/assets/08b0d875-3836-4e6e-9b0e-f91ee092a792" />

curl -O https://s3.us-west-2.amazonaws.com/amazon-eks/1.36.2/2026-07-05/bin/linux/amd64/kubectl

chmod +x ./kubectl

sudo cp kubectl /usr/local/bin/kubectl

<img width="942" height="503" alt="image" src="https://github.com/user-attachments/assets/23157e33-0219-4267-ac05-779cc9534787" />


### AWS Configure:

<img width="928" height="505" alt="image" src="https://github.com/user-attachments/assets/bb0c807f-cead-4d98-9c10-afcca3d11078" />

<img width="880" height="497" alt="image" src="https://github.com/user-attachments/assets/94ce52eb-27f4-4497-9bc4-5d0954ea719e" />


check if aws is properly configured by : > aws s3 ls
it should list the aws s3 buckets you created

---------

through out Kubernetes we will keep seeing : 
Kind:
api_version:
meta_data:




<img width="425" height="130" alt="image" src="https://github.com/user-attachments/assets/62c71ed6-aa4d-4ba5-adc5-608ad068f767" />



## eksctl - cluster creation examples:

<img width="942" height="531" alt="image" src="https://github.com/user-attachments/assets/429e7d39-0a66-4c90-ac69-a9432967f828" />



<img width="924" height="486" alt="image" src="https://github.com/user-attachments/assets/bec30667-53ae-400d-ada6-e1304cc06c34" />

<img width="666" height="315" alt="image" src="https://github.com/user-attachments/assets/39be82fe-ef70-42a9-95fd-34688a0b4dfa" />


<img width="831" height="350" alt="image" src="https://github.com/user-attachments/assets/170270fd-6d3b-4c98-8ce8-c60fa004eadf" />

<img width="791" height="414" alt="image" src="https://github.com/user-attachments/assets/e1344eba-3291-43b7-8337-421c7f991e6b" />

this command will start cluster creation, it will take around 20 mins to create the cluster with two nodes

<img width="957" height="554" alt="image" src="https://github.com/user-attachments/assets/3c799349-518c-449a-8215-3f20524daad1" />

it is creating the cluster :

<img width="956" height="529" alt="image" src="https://github.com/user-attachments/assets/51c43561-7854-4bb4-b2f9-2fd77fe97ea5" />

you can see the cluster creation under -> Amazon Elastic Kubernetes Service

Now, we see the cluster got created:


<img width="946" height="426" alt="image" src="https://github.com/user-attachments/assets/b21e6649-82cf-4087-a217-8f65835249c1" />


and we also see that two nodes got created, apart from the workstation:

<img width="949" height="543" alt="image" src="https://github.com/user-attachments/assets/5c0f9038-e4db-49f5-8fa4-c4e81c1c81a1" />

How to authenticate to the created cluster:

> aws eks update-kubeconfig --name roboshop-dev --region us-east-1













