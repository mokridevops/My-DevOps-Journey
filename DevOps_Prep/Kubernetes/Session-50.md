
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


<img width="938" height="509" alt="image" src="https://github.com/user-attachments/assets/d60733be-e936-4219-9f7e-3f92f1601abb" />

<img width="936" height="505" alt="image" src="https://github.com/user-attachments/assets/faefac95-411f-4c0e-b6e2-7ce7b3b45cd5" />

<br>

<img width="411" height="140" alt="image" src="https://github.com/user-attachments/assets/bb3118c1-821d-4758-ba24-b363c78eb107" />

<img width="755" height="330" alt="image" src="https://github.com/user-attachments/assets/a0c7c282-c8da-4e77-afd2-1b3f92c11581" />

<img width="778" height="449" alt="image" src="https://github.com/user-attachments/assets/77e28273-4e4e-4935-9c70-fe5cc682e85c" />

<img width="487" height="447" alt="image" src="https://github.com/user-attachments/assets/8e2ad3f1-570e-4e25-b0d7-002d1e767249" />

so, the aws and kubectl - will use this config file

so, Kuberbetes (K8s) authentication and authorization config will be at -> .kube/config

<img width="602" height="149" alt="image" src="https://github.com/user-attachments/assets/c07b15fc-bc0d-425f-b710-0ae661f790db" />

Here, we cannot access EKS control pane, only UI, it is completely managed by Kubernetes, and workloads will not run on EKS control pane, workloads will only run on the nodes, that were created

Amazon EKS - in the below picture is called Master node, and the other EC2 instances are called worker nodes.


<img width="653" height="328" alt="image" src="https://github.com/user-attachments/assets/e65622af-fc89-42cd-9f2d-9a2f5d21448b" />

<img width="643" height="321" alt="image" src="https://github.com/user-attachments/assets/9614dd19-9ce5-4c68-97b0-aa5ee46b0497" />



Everything is called a resource in Kubernetes, any resource we can configure through YAML:

> Kubectl api-resources

<img width="772" height="384" alt="image" src="https://github.com/user-attachments/assets/29ff02aa-c623-4175-b578-eb932cc169f4" />

there are two types of resources:
1. namespace level
2. cluster level

Namespace: 
---------
An isolated project space where we can create our Kubernetes resources, just like VPC.
roboshop, expense, amazon, hdfc, flipkart, etc

In aws - we have vpc resources and non-vpc resources:

Route53 - non vpc resource
Security Group - vpc resource
CloudFront - non vpc resource  

the resources that are binded to vpc - are vpc resources
the resources that are not binded to vpc - are non vpc resources

<img width="783" height="457" alt="image" src="https://github.com/user-attachments/assets/db830856-1730-4943-9f22-e288e6faa533" />


apiversion: in api version, there are a lot, so all one type of resources are grouped together and are given a name in apiversion, such as: v1, apps/v1, authentication.k8s/io/v1, authorization.k8s.io/v1
kind: # resource type


mostly our core apiversion is v1:

<img width="776" height="459" alt="image" src="https://github.com/user-attachments/assets/c90ee15b-649b-4c60-b796-bbce87b6fcf1" />

we will have everything we need in v1 apiversion only


apiversion:
kind:
metadata:
spec: the specifications that we give to run an image


To create a Namespace:
namespace.yaml
apiVersion: v1
kind: Namespace
metadata: 
  name: custom-namespace  # this is the name of the namespace
  labels:
    environment: production


    <img width="452" height="193" alt="image" src="https://github.com/user-attachments/assets/bd837a67-1853-4bc0-8e36-9a79ee35c176" />

    


K8 - resources:

<img width="653" height="384" alt="image" src="https://github.com/user-attachments/assets/7d775fb8-f17f-4d31-af68-e30ff16b3d72" />

to apply this resources:

> kubectl apply -f 01-namespace.yaml

<img width="642" height="259" alt="image" src="https://github.com/user-attachments/assets/b3822674-69d4-4876-a2bb-42af247978d4" />

to see the resources:

> kubectl get namespace

<img width="610" height="160" alt="image" src="https://github.com/user-attachments/assets/791e4213-bef5-4886-af79-9635069c1dc7" />

to describe the namespace resource

> kubectl describe namespace roboshop

<img width="615" height="222" alt="image" src="https://github.com/user-attachments/assets/ea44e24d-2e59-4b0b-a820-44b5f331d14f" />

to see in yaml format

> kubectl get namespace roboshop -o yaml

<img width="787" height="292" alt="image" src="https://github.com/user-attachments/assets/401ef32f-1f82-4df9-be72-0d42d41c3bf0" />

to delete namespace:

> kubectl delete -f 01-namespace.yaml

<img width="586" height="53" alt="image" src="https://github.com/user-attachments/assets/bd996cbf-0768-452e-b78f-2ad657438299" />

<img width="635" height="233" alt="image" src="https://github.com/user-attachments/assets/0c69635f-ffb0-4096-8a7a-1057ff1d56fe" />

shortcuts:

<img width="791" height="348" alt="image" src="https://github.com/user-attachments/assets/2d36d0e0-ae74-477e-9337-7e112e32d9b7" />


# pod:

pod is the smallest deployable unit in kubernetes.  Pod contains one or more containers.  Containers in pod share same network space and storage.

 kubernetes.io

 <img width="487" height="353" alt="image" src="https://github.com/user-attachments/assets/7976404c-fc0f-40d8-94fd-ae70ff2503a6" />

 <img width="565" height="314" alt="image" src="https://github.com/user-attachments/assets/8d2619c5-6829-4f67-8c75-dab9d2dcd246" />


<img width="665" height="255" alt="image" src="https://github.com/user-attachments/assets/894e949a-10a1-4797-985b-50074b3db2ee" />

<img width="590" height="56" alt="image" src="https://github.com/user-attachments/assets/52ee1234-5f16-417e-af28-2362e4a1ed19" />

<img width="718" height="273" alt="image" src="https://github.com/user-attachments/assets/acfec6a4-de8d-467f-978c-8756f53a8055" />
<img width="777" height="448" alt="image" src="https://github.com/user-attachments/assets/c5fccc6b-3304-468b-844e-d8e9e6cfff46" />



<img width="1553" height="895" alt="image" src="https://github.com/user-attachments/assets/f4406415-b8aa-4edc-8bc0-415e8db266d8" />


<img width="791" height="432" alt="image" src="https://github.com/user-attachments/assets/cf48ea60-4384-4266-9898-f2cff5113020" />

so the container is created in the first node, which is matching that ip address

<img width="710" height="420" alt="image" src="https://github.com/user-attachments/assets/93c7ba60-13cd-4f2b-839d-8543f038ef7b" />


two types of issues, that we encounter:
1) ImagePullBackOff/ErrImagePull -> node is not able to pull the image
   1. authentication issues
   2. image address is not correct
2) CrashLoopBackOff -> unable to start containerd
   check the container command

to check the events to troubleshoot : kubectl describe pod nginx


to get in to the pod:
<img width="566" height="46" alt="image" src="https://github.com/user-attachments/assets/17858e6d-d827-40ae-9385-a6a26cb14746" />

> kubectl exec -it nginx -- bash


<img width="780" height="407" alt="image" src="https://github.com/user-attachments/assets/e7312526-f432-4492-a663-2bc08d17b32b" />

changed the name to nginx - and tried to do kubectl apply -f 02-pods.yaml

<img width="565" height="117" alt="image" src="https://github.com/user-attachments/assets/9e187368-fa40-49cc-aad5-85c8fd0aa858" />

got ErrImagePull

<img width="648" height="382" alt="image" src="https://github.com/user-attachments/assets/727ca2c0-0827-4f89-a6c0-46dff644ad7a" />

-----------------
<img width="742" height="492" alt="image" src="https://github.com/user-attachments/assets/96c71abe-f45d-4741-80f0-9b2d6cba4276" />

each time i am getting different error message why?
From the screenshot, Kubernetes is not actually showing different root causes. It is showing different phases of the same problem.

You are seeing:

ErrImagePull
ImagePullBackOff
CrashLoopBackOff
What each status means
1. ErrImagePull
Kubernetes tried to pull the container image and failed.

Common reasons:

Wrong image name
Wrong image tag
Docker Hub authentication/rate limit issues
No internet access from the node
Example:



image: nginx123:latest
Since nginx123 doesn't exist, Kubernetes returns:



ErrImagePull
2. ImagePullBackOff
After repeated image pull failures, Kubernetes stops trying continuously and starts backing off.

Flow:



Pull Image
    ↓
Fail
    ↓
ErrImagePull
    ↓
Retry
    ↓
Fail Again
    ↓
ImagePullBackOff
This is expected behavior and not a new error.

3. CrashLoopBackOff
This happens after the image is successfully pulled but the container keeps crashing.

Flow:



Image Pulled
     ↓
Container Started
     ↓
Container Exits
     ↓
Restart
     ↓
Exits Again
     ↓
CrashLoopBackOff
Common reasons:

Invalid startup command
Application crashes
Missing environment variables
Missing files/configuration
Why are you getting alternating statuses?
Kubernetes continuously reconciles the pod state.

Your pod might be going through:



ErrImagePull
      ↓
ImagePullBackOff
      ↓
Image becomes available OR pull succeeds temporarily
      ↓
Container starts
      ↓
Container crashes
      ↓
CrashLoopBackOff
Or the pod may have been recreated multiple times.

Don't rely on kubectl get pods
The real answer is always in:



kubectl describe pod nginx
Run:



kubectl describe pod nginx
Look at the Events section at the bottom.

You'll see something like:



Failed to pull image "nginx123"
or



Back-off pulling image
or



Back-off restarting failed container
Also check the YAML
Show me the contents of:



cat 02-pod.yaml
and the output of:



kubectl describe pod nginx
That will reveal the exact root cause in a few lines.

--------------------------








   



 





















