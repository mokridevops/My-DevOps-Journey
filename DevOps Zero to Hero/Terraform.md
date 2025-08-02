


<img width="742" height="472" alt="image" src="https://github.com/user-attachments/assets/0acaeff6-ce58-4ad6-86ef-b568ddae3c7e" />


# Advantages of Terraform:

1) Manage any infrastructure : AWS, AZURE, GCP, Open Stack, Oracle Cloud

2) Track your infrastructure:

login to Terraform - and check State file - it could be stored in S3 bucket, etc - thenyou can see all the resources that were created

3) Automate changes:

you can automate, instead of login to AWS 

put the terraform files, except state files in GIT, and 

4) collaborate with your peers

5) Standardize configurations - we maintain standards - for all the cloud providers

 


# Terraform Lifecycle:

1) Write: terraform configuration files

   <img width="925" height="691" alt="image" src="https://github.com/user-attachments/assets/2fdc30a0-81a9-41f4-b407-9e07dbbe7d1b" />

   <img width="1024" height="621" alt="image" src="https://github.com/user-attachments/assets/c0261555-7a16-463c-93c2-075e92ec9093" />

   

<img width="586" height="501" alt="image" src="https://github.com/user-attachments/assets/6f3a66ab-4d0e-46d3-a67f-5d47a10fc217" />

1. Write: we first write terraform templates: we can use Hashicorp Terraform documentation to write these files
2. Plan:  we can click on Pan to review the changes before clicking Apply, it is like a preview of the changes that are going to be impacted.
3. Apply:  once written the terraform files and did the dryrun ( i.e. Plan ), we will click Apply
4. Destroy: Terraform Destroy is used to delete the resourced applied.




# Install Terraform:

<img width="701" height="488" alt="image" src="https://github.com/user-attachments/assets/a7b9f17d-5b3c-41b3-a444-6a6f68e7664f" />

<img width="943" height="468" alt="image" src="https://github.com/user-attachments/assets/a3155fc3-b6dd-4e96-8fcc-a8aae028d24e" />






<img width="1461" height="897" alt="image" src="https://github.com/user-attachments/assets/89dc66dc-7d1f-4e9e-b8ea-2e21d8b9480f" />

for Ubuntu: copy these commands and run them

wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(grep -oP '(?<=UBUNTU_CODENAME=).*' /etc/os-release || lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform



<img width="743" height="761" alt="image" src="https://github.com/user-attachments/assets/73cb6010-48cf-4e17-8c30-1952776356d6" />





<img width="827" height="447" alt="image" src="https://github.com/user-attachments/assets/6e064ad6-47aa-420d-907d-95de8b1a9558" />


terraform init : initialize your terraform



terraform plan

terraform apply

terraform destroy










   


