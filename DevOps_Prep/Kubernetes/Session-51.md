Since pod is ephimeral (it does not exist forever), we can't use pod ip as DNS, K8 is giving us option to use services.
1. pod to pod communication
2. load balancing

<img width="264" height="170" alt="image" src="https://github.com/user-attachments/assets/fb81c264-83e2-48ac-9489-8578715d56af" />


Each of the pods, register their IP address with the Service. (Kubernetes Service)

once the request hits the service, the service acts as a load balancer, and sends the request to each of the pods in a round robin algorithm.
