Since pod is ephimeral (it does not exist forever), we can't use pod ip as DNS, K8 is giving us option to use services.
1. pod to pod communication
2. load balancing

<img width="264" height="170" alt="image" src="https://github.com/user-attachments/assets/fb81c264-83e2-48ac-9489-8578715d56af" />


Each of the pods, register their IP address with the Service. (Kubernetes Service)

once the request hits the service, the service acts as a load balancer, and sends the request to each of the pods in a round robin algorithm.


### A Kubernetes (K8s) Service is an abstract way to define a logical set of Pods and a policy to access them.

<img width="1851" height="1051" alt="image" src="https://github.com/user-attachments/assets/267a1c98-3123-4f05-968c-45f565e986bf" />


<img width="1699" height="1004" alt="image" src="https://github.com/user-attachments/assets/a38fa5a2-a9ac-430a-94f9-02fc9028eabf" />

if you hit on the service name: nginix-service, then the service -> will consider the pods (ip addresses) that are registered to that service, it will send the traffic to port 80 (container port)

<img width="1134" height="137" alt="image" src="https://github.com/user-attachments/assets/7ffb1e41-40af-49e0-9b17-b7108afc4940" />


<img width="1104" height="150" alt="image" src="https://github.com/user-attachments/assets/9eca2062-e6d3-4905-b846-255126c093e8" />

<img width="1533" height="416" alt="image" src="https://github.com/user-attachments/assets/2c114cda-bed2-4eb2-b569-3297bc64ce29" />

<img width="1234" height="488" alt="image" src="https://github.com/user-attachments/assets/737dd84d-aba7-4fed-8a2b-1a1d43469eab" />


<img width="1136" height="383" alt="image" src="https://github.com/user-attachments/assets/ebda7051-e2ea-4bda-8387-1dc91fd34133" />


<img width="1149" height="804" alt="image" src="https://github.com/user-attachments/assets/56de2917-e81f-4f5e-b96e-7675713820d9" />



<img width="1600" height="209" alt="image" src="https://github.com/user-attachments/assets/11e415ac-cb87-41c9-9bdc-396285338719" />


there are 3 types of services:
1. ClusterIP - internal to kubernetes

<img width="1141" height="144" alt="image" src="https://github.com/user-attachments/assets/abeead44-36e8-4e81-9832-a099b3c4c6a7" />

this is the IP address for the service

2. nodePort -> expose pod to outside world in internet

3. 








