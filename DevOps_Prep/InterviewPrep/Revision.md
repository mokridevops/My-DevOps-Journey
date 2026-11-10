### 1)  why ansible cannot be used for Iac, even though we can use ansible for building the Infrastructure as code?
Ans:  Due to the following reasons:
1) Terraform is stateful, Ansible is stateless - terraform maintains a state file - terraform.tfstate - it tracks what infrastructure exists
2) Terraform does - infrastructure dependency management, that means - it knows what all resources are need to be created before the targetted resource needs to be created, hence it will create all the pre required resources automatically, where as for Ansible, we have to explicitly give the order for creation of resources, as it doesnot have the dependency management.
3) Terraform has - execution planning, i.e. Terraform Plan -> which will show what infra is going to get created? where as anisble playbook does the changes immediately, we dont have a preview mode before it applies the changes
4) Terraform has full life cycle management - 1) Create 2) Update 3) Replace 4) Destroy
5) Drift Detection - Terraform, anisible not
6) Multicloud support - Terraform, ansible not
