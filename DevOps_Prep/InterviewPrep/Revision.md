### 1)  why ansible cannot be used for Iac, even though we can use ansible for building the Infrastructure as code?
Ans:  Due to the following reasons:
1) Terraform is stateful, Ansible is stateless - terraform maintains a state file - terraform.tfstate - it tracks what infrastructure exists
2) Terraform does - infrastructure dependency management, that means - it knows what all resources are need to be created before the targetted resource needs to be created, hence it will create all the pre required resources automatically, where as for Ansible, we have to explicitly give the order for creation of resources, as it doesnot have the dependency management.
3) Terraform has - execution planning, i.e. Terraform Plan -> which will show what infra is going to get created? where as anisble playbook does the changes immediately, we dont have a preview mode before it applies the changes
4) Terraform has full life cycle management - 1) Create 2) Update 3) Replace 4) Destroy
5) Drift Detection - Terraform, anisible not
6) Multicloud support - Terraform, ansible not


### 2) what is NodePort, LoadBalancer and Ingress?
Ans: NodePort exposes a service on a port of every Kubernetes node, and is mainly used for testing.
LoadBalancer creates a cloud provider load balancer and exposes a service externally, but each service typically gets its own load balancer.
Ingress is a layer-7 routing mechanism that sits in front of the Load Balancer and does Path Based routing and host based routing for the services using the single load balancer, making it preferred solutions for production Kubernetes environments.

NodePort => expose through node's IP and port on each kubernetes node
LoadBalancer => one cloud load balancer per service
Ingress => One load balancer for many services with routing on path based and host based.

### 3) what is startup probe, readiness probe and liveness probe?

