

resource "terraform_data" "mongodb" {
  triggers_replace = [
    aws_instance.mongodb.id
    
  ]

// connection block
 connection {
    type        = "ssh"
    user        = "ec2-user"
    password    = "DevOps321"
    host        = aws_instance.mongodb.private_ip
  }

provisioner "file" {
  source = "bootstrap.sh"
  destination = "/tmp/bootstrap.sh"
  
}

  provisioner "remote-exec" {
    inline = [ // to run multiple commands we use inline
      "chmod +x /tmp/bootstrap.sh",
      "sudo sh /tmp/bootstrap.sh mongodb ${var.environment}"
     ]
  }



-------------------------------------------------------
The short answer: this Terraform block is using terraform_data as a modern replacement for null_resource to run provisioners (file upload + remote-exec) on your MongoDB EC2 instance whenever that instance is replaced.  
Below is a clear, line‑by‑line explanation.

🧩 What this resource actually does
1. resource "terraform_data" "mongodb"
Terraform 1.4+ introduced terraform_data as the successor to null_resource.
It behaves like a resource but does not create infrastructure — it only hosts provisioners and lifecycle triggers.
  
scalr.comscalr.com. A Concise Guide to terraform_data Resource

You are using it to run scripts on your MongoDB EC2 instance.

🔁 2. triggers_replace = [ aws_instance.mongodb.id ]
This tells Terraform:

“If the MongoDB EC2 instance ID changes, destroy and recreate this terraform_data resource.”

Why?
Because provisioners only run on create, not on update.
So this ensures your bootstrap script re-runs whenever the EC2 instance is replaced.

This is exactly how null_resource.triggers used to work, but terraform_data supports all value types.

🔐 3. Connection block
hcl
connection {
  type        = "ssh"
  user        = "ec2-user"
  password    = "DevOps321"
  host        = aws_instance.mongodb.private_ip
}
This tells Terraform how to SSH into the MongoDB EC2 instance.

⚠️ Important:  
Using password for EC2 is unusual — AWS normally uses SSH keys.
But Terraform will attempt SSH using this username/password.

📁 4. File provisioner
hcl
provisioner "file" {
  source      = "bootstrap.sh"
  destination = "/tmp/bootstrap.sh"
}
Terraform uploads your local bootstrap.sh file to the EC2 instance at /tmp/bootstrap.sh.

🚀 5. Remote-exec provisioner
hcl
provisioner "remote-exec" {
  inline = [
    "chmod +x /tmp/bootstrap.sh",
    "sudo sh /tmp/bootstrap.sh mongodb ${var.environment}"
  ]
}
Terraform SSHs into the instance and runs:

chmod +x /tmp/bootstrap.sh → makes the script executable

sudo sh /tmp/bootstrap.sh mongodb <environment> → runs your bootstrap script with parameters

This is typically used to install MongoDB, configure repos, set up users, etc.

🧠 Putting it all together
This block means:

“Whenever the MongoDB EC2 instance is replaced, upload bootstrap.sh to it and run it over SSH.”

It is a provisioning mechanism — not infrastructure creation.

📌 Why use terraform_data instead of null_resource?
According to HashiCorp:

It is built-in (no provider needed)

It supports any trigger type

It is the recommended replacement for null_resource  
  
