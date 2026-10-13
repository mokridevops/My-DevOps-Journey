
# Hashicorp Terraform Associate 004:

https://developer.hashicorp.com/terraform/tutorials/certification-004/associate-review-004

HCL - configuration language - declarative approach

Plan -> Desired state + current state (state 1) (of infrastructure) = plan

Apply -> takes the plan and applies the plan and creates new state -> stage 2

<img width="443" height="381" alt="image" src="https://github.com/user-attachments/assets/16c30253-02e6-4428-9645-e109ef15028c" />


Terraform workflow:
3 stages:
1) Write -> define infra in config files
2) Plan -> review changes Terraform will make to your infra
3) Apply -> terraform provisions your infra and updates the state file

Terraform -> split into two main parts:
1) Terraform Core
2) Terraform Plugins  - ex: providers - interact with coud providers SAAS providers, and other APIs.

   Terraform Registry - main directory of publicly available terraform providers


   Running terraform init-> locally installs a provider and updates the dependency lock file, with the latest version matching the version string you configured in your required_providers block.


   Require providers: provider requirements are declared in a required_providers block

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

> terraform -version  -> to check current version of terraform

Authenticate Terraform AWS provider

> export AWS_ACCESS_KEY_ID =
> export AWS_SECRET_ACCESS_KEY =

> aws configure -> to configure terraform with aws
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

> terraform fmt -> automatically reformats all configuration files in the current directory according to Hashicorp's recommended style.

<img width="286" height="112" alt="image" src="https://github.com/user-attachments/assets/4c4e10ff-1a37-49af-a40c-e963c1808fdb" />


## Initialize your workspace:

> terraform init -> terraform downloads and installs the providers defined in your configuration in your current working directory.

<img width="975" height="622" alt="image" src="https://github.com/user-attachments/assets/60c04a7b-d21e-4c36-a005-4437949b3bda" />

Terraform downloaded the aws provider and installed it in a hidden .terraform subdirectory of your current working directory.  Terraform also created a file named .terraform.lock.hcl which specifies the exact provider versions used with your workspace, ensuring consistency between runs.


## Validate configuration:
to make sure your configuration is syntactically valid and internally consistent

<img width="484" height="108" alt="image" src="https://github.com/user-attachments/assets/d96627fd-093c-4857-8611-e70be51a487e" />














   
