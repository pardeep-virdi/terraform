# terraform

Terraform is a tool that allows you to automate your interactions with services like AWS (and indeed others) and record the state, giving you the ability to place your infrastructure in source control.


To see what Terraform will do: terraform plan -var-file terraform.tfvars

To bring up the infrastructure we’ll run: terraform apply -var-file terraform.tfvars

And to destroy it, we’ll run: terraform destroy -var-file terraform.tfvars


.tf files are all combined to provide the full configuration.
This gives us a handy way to break the configuration up into thematic sections.
.tfstate and .tfstate.backup holds the last-known state of the infrastructure, you’ll want to store this, too.
.tfvars contain values for the declared variables, typically called: terraform.tfvars.


Terraform install on linux :-

SSH into your cloud server
sudo yum install -y zip unzip (if these are not installed)
wget https://releases.hashicorp.com/terraform/0.9.8/terraform_0.9.8_linux_amd64.zip
unzip terraform_0.9.8_linux_amd64.zip
sudo mv terraform /usr/local/bin/
Confirm terraform binary is accessible: terraform --version


Use terraform init, a command to initialize download provider plugins to your local system. The output of the above command is shown below:
terraform init

Initializing provider plugins...
 - Checking for available provider plugins
 - Downloading plugin for provider "aws" (0.1.4)...
* provider.aws: version = "~> 0.1"
Terraform has been successfully initialized!




terraform plan

command to see what are you going to deploy.

+ aws_instance.example
      id:                           <computed>
      ami:                          "ami-4fc58420"
      associate_public_ip_address:  <computed>
      availability_zone:            <computed>
      ebs_block_device.#:           <computed>
      ephemeral_block_device.#:     <computed>
      instance_state:               <computed>
      instance_type:                "t2.micro"
      ipv6_address_count:           <computed>
      ipv6_addresses.#:             <computed>
      key_name:                     <computed>
      source_dest_check:            "true"
Plan: 1 to add, 0 to change, 0 to destroy.
  
  
  terraform apply command to apply the changes.
  
 $ terraform apply
 aws_instance.example: Creating...
 ami:                          "" => "ami-4fc58420"
 associate_public_ip_address:  "" => "<computed>"
 availability_zone:            "" => "<computed>"
 ebs_block_device.#:           "" => "<computed>"
 ephemeral_block_device.#:     "" => "<computed>"
 instance_state:               "" => "<computed>"
 aws_instance.example: Still creating... (10s elapsed)
 aws_instance.example: Still creating... (20s elapsed)
 aws_instance.example: Creation complete after 22s (ID: i-07fcaa5435207dac7)
 Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
  
  



