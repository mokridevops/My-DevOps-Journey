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
