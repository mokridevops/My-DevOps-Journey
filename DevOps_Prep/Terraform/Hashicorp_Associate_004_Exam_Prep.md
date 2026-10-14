
# Hashicorp Terraform Associate Exam 004:

https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004

HCL - configuration language - declarative approach

Plan -> Desired state + current state (state 1) (of infrastructure) = plan

Apply -> takes the plan and applies the plan and creates new state -> stage 2

<img width="443" height="381" alt="image" src="https://github.com/user-attachments/assets/16c30253-02e6-4428-9645-e109ef15028c" />


### Terraform workflow:
3 stages:
1) Write -> define infra in config files
2) Plan -> review changes Terraform will make to your infra
3) Apply -> terraform provisions your infra and updates the state file

Terraform -> split into two main parts:
1) Terraform Core
2) Terraform Plugins  - ex: providers - interact with coud providers SAAS providers, and other APIs.

###   Terraform Registry - main directory of publicly available terraform providers


   Running terraform init-> locally installs a provider and updates the dependency lock file, with the latest version matching the version string you configured in your required_providers block.


 ### Require providers: provider requirements are declared in a required_providers block

   terraform {
      required_providers {
       aws = {
          source = hashicorp/aws"
          version = "6.48.0"
   }
}


## connect to terraform enterprise:

terraform {
  cloud {
    organization = "example_corp"
    hostname = "my.terraform-enterprise.host"
    workspaces {
      tags = ["app"]
      }
    }
  }
    
resources from hashicorp/aws all begin with aws, like aws_instance or aws_security_group


Track your infrastructure:  statefile  -> terraform keeps track of your infrastructure in a state file - it is single source of truth

Collaborate: HCP terrafrom - free for up to 5 users, 

version "~> 5.92" -> means terraform can support major version 5, and any minor version greater than 0.92.

Version >= 1.2 -> means terraform supports any version of terraform greater than or equal to 1.2.

### > terraform -version  -> to check current version of terraform

### Authenticate Terraform AWS provider

> export AWS_ACCESS_KEY_ID =
> export AWS_SECRET_ACCESS_KEY =

### > aws configure -> to configure terraform with aws
>
> aws configure list:
<img width="996" height="262" alt="image" src="https://github.com/user-attachments/assets/921b7920-3fa7-4f30-b569-53d9eee97855" />


## Data Sources: 
-> query your cloud provider for information about other resources.
-> help keep the configuration dynamic and avoid hardcoded values that can become stale.

<img width="982" height="394" alt="image" src="https://github.com/user-attachments/assets/1481755a-5133-498f-bdda-29c74e1a3459" />

## Resources:
-> resource block -> defines components of your infrastructure.

<img width="972" height="325" alt="image" src="https://github.com/user-attachments/assets/0ab245c1-327d-4c2e-b6fa-5a054d7b95ac" />

aws_instance -> resource_type
app_server -> resource_name

resource address for your EC2 instacne is: aws_instance.app_server


## Format Configuration:

### > terraform fmt -> 
automatically reformats all configuration files in the current directory according to Hashicorp's recommended style.

<img width="286" height="112" alt="image" src="https://github.com/user-attachments/assets/4c4e10ff-1a37-49af-a40c-e963c1808fdb" />


## Initialize your workspace:

### > terraform init -> 
terraform downloads and installs the providers defined in your configuration in your current working directory.

<img width="975" height="622" alt="image" src="https://github.com/user-attachments/assets/60c04a7b-d21e-4c36-a005-4437949b3bda" />

Terraform downloaded the aws provider and installed it in a hidden .terraform subdirectory of your current working directory.  Terraform also created a file named .terraform.lock.hcl which specifies the exact provider versions used with your workspace, ensuring consistency between runs.


## Validate configuration:
to make sure your configuration is syntactically valid and internally consistent

<img width="484" height="108" alt="image" src="https://github.com/user-attachments/assets/d96627fd-093c-4857-8611-e70be51a487e" />


## Create Infrastructure:

Terraform makes changes to infrastructure in two steps:
1) Execution plan
2) Apply - once you approve step 1


<img width="650" height="769" alt="image" src="https://github.com/user-attachments/assets/5940cfa4-9931-4121-b0a9-0605eafb889d" />

<img width="653" height="702" alt="image" src="https://github.com/user-attachments/assets/5b8eb3c7-be01-4268-8e82-4664bbe5bb10" />

<img width="655" height="297" alt="image" src="https://github.com/user-attachments/assets/1dc045bc-d859-4c91-aaad-f4063d068d95" />



## Inspect State:
When clicked Apply, terraform wrote data about your infrastructure into a file called state file -> terraform.tfstate

### > terraform state list ->
> list the resources and data sources in your terraform workspace's state
<img width="650" height="91" alt="image" src="https://github.com/user-attachments/assets/51db078d-0b91-45e7-91ca-f55b52d516e2" />

-> even though the data source is not an actual resource -> terraform tracks it in your state file

### Terraform show -> print out your workspace's entire state

<img width="642" height="440" alt="image" src="https://github.com/user-attachments/assets/2907cb62-6376-4d9c-865d-e61cdee3fca0" />

When clicking plan + apply -> terraform compares 
   -> what is current configuration
   -> what is in cloud via the data providers
   -> what is the last know state in the state file

By default -> terraform -> creates state file locally
As your infrastructure mature -> storing your state remotely using HCP terraform -> will let you collaborate with your team more easily and keep your state file secure.
               
State file can include ->
    - sensitive info such as passwords or security keys -> store state file securely and restrict access.
    
    


# Variables and Outputs:

## Input Variables: 
parameterize the behavior of your terraform configuration.

variables.tf
<img width="442" height="266" alt="image" src="https://github.com/user-attachments/assets/fba297f0-173d-4d47-b808-ec7dfe27f74d" />
<img width="345" height="247" alt="image" src="https://github.com/user-attachments/assets/a40c5701-f199-4109-a7f5-70484e0de77f" />

changing the variables, in command line:

### > terraform plan -var instance_type=t2.large

<img width="644" height="590" alt="image" src="https://github.com/user-attachments/assets/274b00a2-8959-4e9c-8e85-3b8d250aca51" />

## Output values: 
to expose data about the resources you create.

<img width="424" height="142" alt="image" src="https://github.com/user-attachments/assets/018ff923-4fc3-4e5c-8daa-ba0485c5af29" />

this output value exposes your EC2 instances hostname from your terraform workspace.

 you can review your output values using:
### > terraform output 
<img width="544" height="73" alt="image" src="https://github.com/user-attachments/assets/252dc814-27d9-476e-b04e-fd43acf9d819" />


# Modules
Reusable sets of configuration - with multiple sets of resources and data sources




   
