
# Learning-Terraform

- Source : https://www.youtube.com/watch?v=fgp-t5SqQmM&list=PLdpzxOOAlwvI0O4PeKVV1-yJoX2AqIWuf
- Github repo for instructor notes : https://github.com/iam-veeramalla/terraform-zero-to-hero/blob/main/README.md
- Terraform Registry for getting code for infrastructure : https://registry.terraform.io/providers/hashicorp/aws/latest/docs

##
## What I Learned
| Topic | Status |
|---|---|
| Terraform Lifecycle | ✅ |
| EC2 Provisioning | ✅ |
| Variables & Outputs | ✅ |
| Modules | ✅ |
| Remote Backend (S3) | ✅ |
| Workspaces | ✅ |
| Provisioners | ✅ |
| Secrets Management (Vault) | 📖 Conceptual |
##
## Started with Terraform-Zero-to-Hero by Abhishek Veeramalla
**Setup:**

1.  Installed Terraform on my macbook-pro

    <img width="436" height="88" alt="Screenshot 2026-05-06 at 8 59 47 AM" src="https://github.com/user-attachments/assets/34b94d90-8a53-47ea-9215-83b85a7a2d1b" />
2.  Using VSCode to run terraform 


    <img width="1440" height="900" alt="Screenshot 2026-05-06 at 9 26 41 AM" src="https://github.com/user-attachments/assets/31efc2bd-a65d-4aec-b9ab-c5910d5bc7f7" />
3.  Installed AWS CLI using-


     ``` brew install awscli ```


    <img width="1440" height="281" alt="Screenshot 2026-05-06 at 5 53 32 PM" src="https://github.com/user-attachments/assets/483b8b80-ac52-453e-aa2f-701e9d5256a0" />


4.  Adding programmatic access to already created IAM User- AdminRP 

   
      - <img width="1398" height="797" alt="Screenshot 2026-05-06 at 6 04 15 PM" src="https://github.com/user-attachments/assets/8bcaf792-0900-4e1d-ae25-fb8c4ca8d1fc" />
      
      
      - <img width="1406" height="676" alt="Screenshot 2026-05-06 at 6 06 12 PM" src="https://github.com/user-attachments/assets/fd24dcdb-87de-4c4d-8fe0-261a6b2cc555" />
      
      
      - <img width="2880" height="618" alt="tempImage3IsTRR" src="https://github.com/user-attachments/assets/1e3f623b-9765-4920-99ee-735b8abfc487" />
 ##
 ##
 
### Mini-Project : Creation of EC2 instance 


 Using Terraform AWS Documentation to create main.tf file to create EC2 instance. 

 <img width="1440" height="900" alt="Screenshot 2026-05-06 at 7 44 20 PM" src="https://github.com/user-attachments/assets/821e452f-ba24-4617-9a9d-8103a157301f" />




     ```
        provider "aws"{
               region = "ap-south-1"
    }

        resource "aws_instance" "RPinstance" {
               ami = "ami-0dcc1e21636832c5d"
               instance_type = "t3.micro"
    }
     ```


  
  After writing the tf file ran terraform commands in the same folder where our file is stored to create the infrastructure

 
 <img width="517" height="255" alt="Screenshot 2026-05-07 at 7 02 30 AM" src="https://github.com/user-attachments/assets/6a1ce120-bfee-4165-8116-5851bd3085c3" />


## Lifecycle of terraform- init, plan, apply, destroy 


 ### terraform init


  <img width="585" height="340" alt="Screenshot 2026-05-07 at 7 30 37 AM" src="https://github.com/user-attachments/assets/27403598-df4a-4a53-a586-bb9dd1b8ebbf" />


### terraform plan


 <img width="1000" height="823" alt="Screenshot 2026-05-07 at 7 39 18 AM" src="https://github.com/user-attachments/assets/eb170c84-da2f-416f-8f11-d05fe6d9d9d6" />


### terraform apply


##### Error on terraform apply - ec2 instance related issue


<img width="1165" height="541" alt="Screenshot 2026-05-07 at 7 45 21 AM" src="https://github.com/user-attachments/assets/bc342482-2ac8-4ac6-b4fd-2ae55dc5cebb" />


Went to the console to get the ami-id of the ubuntu instance I am creating


<img width="921" height="655" alt="Screenshot 2026-05-07 at 7 49 33 AM" src="https://github.com/user-attachments/assets/d423fc79-98ad-40e8-b612-7218ee02b5b7" />


<img width="765" height="847" alt="Screenshot 2026-05-07 at 7 57 29 AM" src="https://github.com/user-attachments/assets/7fc85464-e648-4601-810f-217c7b3675b2" />


#### ec2 instance created sucessfully


The instance created here is having [id=i-0f1dffdbd2870e283]



we can cross-verify this in our AWS management console- 


And we can see that our instance is up and running which was made by coding- 


<img width="1174" height="334" alt="Screenshot 2026-05-07 at 8 09 01 AM" src="https://github.com/user-attachments/assets/baf0bc85-b706-4815-919c-e583282c8019" />



Ran this command to stop the instance


<img width="725" height="273" alt="Screenshot 2026-05-07 at 8 17 06 AM" src="https://github.com/user-attachments/assets/17b46bf5-69f7-4e0b-be04-774b51f7f3a7" />


### terraform destroy


now completely deleting the ec2 instance 


<img width="691" height="547" alt="Screenshot 2026-05-07 at 8 18 24 AM" src="https://github.com/user-attachments/assets/4acc6f88-4c4d-4e4f-abc2-04aaf34f108b" />


Rechecking on console if the EC2 instance is destroyed or not. 


<img width="1170" height="283" alt="Screenshot 2026-05-07 at 8 19 31 AM" src="https://github.com/user-attachments/assets/2dba7e09-0bdf-4351-9d6f-8b9055091e2a" />


##
##

Provider is a medium to understand where the infrastructure needs to be created. In terraform providers page we can find n number of providers that are mainly classified into 


3 types : Official, Partner & Community Providers.
 

 *for multiple regions we use alias

 
 *for multiple clouds the syntax is different for which we can always refer to Hashicorp documentation



Variables here are of 2 types- Input & Output Variables


****terraform.tfvars


when using terraform apply (terraform.tfvars values are taken automatically)


But if default/initial values are in some other files (eg. dev.tfvars) then we use command terraform apply --dev.tfvars


Created 3 terraform files-


<img width="310" height="367" alt="Screenshot 2026-05-07 at 5 44 38 PM" src="https://github.com/user-attachments/assets/df040c41-05e2-4df2-ba24-597e988e7be2" />



- ### main.tf

   ```
       provider "aws" {
       region = "ap-south-1"
        }

       resource "aws_instance" "e1" {
       ami = var.ami_value
       instance_type = var.instance_type_value
        }

   ```
- ### variables.tf


   ```
       variable "ami_value" {
       description = "value for ami_value"
        }

       variable "instance_type_value" {
       description = "value for instance_type"
        }
   ```

- ### terraform.tfvars

   ```
       ami_value = "ami-07a00cf47dbbc844c"
       instance_type_value = "t3.micro"
   ```


### Ran Terraform commands: terraform init , terraform plan , terraform apply


And EC2 Instance got created-

  
  <img width="1133" height="259" alt="Screenshot 2026-05-07 at 7 09 51 PM" src="https://github.com/user-attachments/assets/942edad5-1416-48fa-9c66-c70785e8f243" />


Checking in console for instance created-

 
  <img width="1185" height="384" alt="Screenshot 2026-05-07 at 7 10 39 PM" src="https://github.com/user-attachments/assets/257b1819-94ab-4f64-96c0-ee84e2c59d55" />



Adding ***output.tf*** file to the folder to display the public IP address of the ec2 instance created




   ```
       output "public_ip" {
        value = aws_instance.e1.public_ip
         }
   ```



The output.tf file that was written to show public IP of the instance created is now showing the output after creating instance.


<img width="1129" height="406" alt="Screenshot 2026-05-07 at 8 47 37 PM" src="https://github.com/user-attachments/assets/4032ad5c-6bab-4be7-8996-ffa0c89d489a" />


##
##

### Modules


Modules are a set of files grouped in a single directory and they can be accessed by multiple users any no. of times if only the path of module is known to the user. 


### Creating module



Created a folder modules/M1 and put the files main.tf , variables.tf and output.tf in it.

 - <img width="311" height="359" alt="Screenshot 2026-05-07 at 9 32 46 PM" src="https://github.com/user-attachments/assets/2e118f2e-901c-406e-a435-677d75e47a4c" />



Outside modules folder created the follwing main.tf file inside project2 folder

 - <img width="765" height="812" alt="Screenshot 2026-05-07 at 9 33 17 PM" src="https://github.com/user-attachments/assets/aa907987-addb-4e53-acde-e7117be6e0cf" />



Ran the terraform commands to get our EC2 instance created again. 

- <img width="1178" height="339" alt="Screenshot 2026-05-07 at 9 33 44 PM" src="https://github.com/user-attachments/assets/54a604df-b1c0-414a-8435-008fb03e56ab" />

##
##


Importance of statefiles: 


It recorde the infrastructure that it has created, helps in updating the created infrastructure, and also what to destroy. 


But there are 2 drawbacks to statefiles: 

1. Sensitive information may be stored in the state file if it's committed to a Version Control System. This poses a security risk because VCS repositories are often shared among team members.

 
2. Managing state files in VCS can lead to complex versioning issues, especially when multiple team members are working on the same infrastructure.


### Remote Backends

Terraform gives an option of storing terraform statefile in external resources instead of local/virtual machine.
eg. using S3 bucket, Terraform cloud


S3 bucket helps with that- 
   - S3 bucket access is completely restricted and secured as it can be configured with IAM policies
   - all modifications done to code can easily be updated in S3 automatically 


<img width="746" height="618" alt="Screenshot 2026-05-16 at 8 08 14 AM" src="https://github.com/user-attachments/assets/cbee7157-5bd4-4258-b787-1f9056f603ed" />



first create main.tf to create s3 bucket: 


<img width="463" height="529" alt="Screenshot 2026-05-16 at 8 16 31 AM" src="https://github.com/user-attachments/assets/a7bd6a25-0691-4a9c-b600-5ae8cfc310b5" />


<img width="640" height="845" alt="Screenshot 2026-05-16 at 8 27 29 AM" src="https://github.com/user-attachments/assets/6ee9cb32-1e3e-4b68-ba28-efcf3536006c" />


created backend.tf and again ran 'terraform init' command. 



Following image shows that my already created s3 bucket is not ready to be used to store terraform state files. There is also a question asking if the user wants to transfer the local statefile to s3 bucket or not. 


<img width="626" height="769" alt="Screenshot 2026-05-16 at 8 29 22 AM" src="https://github.com/user-attachments/assets/91cb88d7-4943-4f41-96b7-734ca77f7ea1" />

terraform plan


<img width="960" height="420" alt="Screenshot 2026-05-16 at 8 32 16 AM" src="https://github.com/user-attachments/assets/7ebaca03-f378-4498-a570-7f6f3b2159d5" />

terraform apply


<img width="997" height="454" alt="Screenshot 2026-05-16 at 8 33 27 AM" src="https://github.com/user-attachments/assets/f5c9c6f0-995a-4249-9abc-8a5a17d5c87e" />

Verification on AWS console 


<img width="1417" height="456" alt="Screenshot 2026-05-16 at 8 34 01 AM" src="https://github.com/user-attachments/assets/efc4ad4e-c871-4fce-ad73-acba95905780" />


if we run command 'terraform show'
the state file will be shown directly from the s3 bucket that was created


on using terraform destroy got this interruption
<img width="1130" height="296" alt="Screenshot 2026-05-16 at 8 50 29 AM" src="https://github.com/user-attachments/assets/9307a096-473f-456e-b0d3-95759865ef80" />


Learned 3 methods to delete contents of s3 bucket
- Using terraform to empty it
     - <img width="909" height="374" alt="Screenshot 2026-05-16 at 8 53 49 AM" src="https://github.com/user-attachments/assets/88dea215-848d-45c5-9eaa-164e2f0cfd6d" />
- Manually empying the bucket using AWS CLI
     - <img width="907" height="210" alt="Screenshot 2026-05-16 at 8 56 03 AM" src="https://github.com/user-attachments/assets/4146ec38-4d7c-4b47-8a7a-ffb2d83665dc" />
- Using one-liner force delete
     - <img width="900" height="74" alt="Screenshot 2026-05-16 at 8 58 01 AM" src="https://github.com/user-attachments/assets/41a00a6a-2309-4e29-9404-e2b6e71a34e8" />


Deleted the statefiles from s3 bucket


<img width="683" height="190" alt="Screenshot 2026-05-16 at 8 59 26 AM" src="https://github.com/user-attachments/assets/6423ccd7-1e88-43db-b889-a9ee5920082d" />

Finally destroyed 


<img width="859" height="166" alt="Screenshot 2026-05-16 at 9 01 59 AM" src="https://github.com/user-attachments/assets/fbff4013-0af3-4bb3-b572-5c7e4337bacb" />



***Note for self : The S3 bucket and the dynamodb table to create statefile source and statefile lock should be created before writing backend.tf code


Locking mechanism to save concurrent access to infrastructure using dynamoDB table


using terraform registry to find dynamodb table code


<img width="1069" height="510" alt="Screenshot 2026-05-16 at 8 41 10 AM" src="https://github.com/user-attachments/assets/6c0c7fca-3372-4cb0-815a-f3674a5fb61f" />



updated main.tf to implement statefile locking mechanism & Commented the updated backend file to create s3 bucket and dynamodb table first


<img width="1395" height="433" alt="Screenshot 2026-05-16 at 9 46 35 AM" src="https://github.com/user-attachments/assets/d5d4921e-295b-4848-bc1f-15ce389297cc" />


Initialised terraform :


<img width="612" height="318" alt="Screenshot 2026-05-16 at 9 47 41 AM" src="https://github.com/user-attachments/assets/4d7c3630-6f83-4892-8abc-7efc7000719a" />

terraform plan :


<img width="1061" height="104" alt="Screenshot 2026-05-16 at 9 48 42 AM" src="https://github.com/user-attachments/assets/6c848e12-29a0-4dda-8204-5665b7061c7b" />

terraform apply :


<img width="603" height="167" alt="Screenshot 2026-05-16 at 9 51 41 AM" src="https://github.com/user-attachments/assets/40658088-ffa3-4c47-a1f8-743b8376641b" />


<img width="730" height="247" alt="Screenshot 2026-05-16 at 9 50 41 AM" src="https://github.com/user-attachments/assets/7a8c9562-3b0f-4e6a-99b7-08b8818c3d95" />


<img width="1127" height="212" alt="Screenshot 2026-05-16 at 9 51 11 AM" src="https://github.com/user-attachments/assets/4375a345-5a82-4a2f-9b08-dcca163d18f3" />

Updated backend.tf

<img width="742" height="258" alt="Screenshot 2026-05-16 at 9 53 25 AM" src="https://github.com/user-attachments/assets/b218f87f-8a23-48bc-b202-ea9875bbd8aa" />

terraform initialise to shows we no longer need to create dynamodb table to lock state. Instead we can use parameter "use_lockfile". 

<img width="619" height="585" alt="Screenshot 2026-05-16 at 9 54 42 AM" src="https://github.com/user-attachments/assets/158f5526-da24-416c-9201-62749257e40a" />


Updated both tf files:

<img width="1137" height="273" alt="Screenshot 2026-05-16 at 12 25 05 PM" src="https://github.com/user-attachments/assets/e06e70bf-b5ca-42dd-b344-25ad0d892098" />

*** INIT-
<img width="614" height="469" alt="Screenshot 2026-05-16 at 12 28 15 PM" src="https://github.com/user-attachments/assets/c80e98e1-578d-48ac-a803-766f9cb873ae" />


*** PLAN-
Terraform plan clearly shows that dynamodb table that was previously created is going to get destroyed as main.tf and backend.tf files were updated


<img width="1082" height="705" alt="Screenshot 2026-05-16 at 12 28 53 PM" src="https://github.com/user-attachments/assets/c48ed5a9-9b5a-44f6-b839-b293c5a2ab75" />

*** APPLY-


<img width="993" height="809" alt="Screenshot 2026-05-16 at 12 30 53 PM" src="https://github.com/user-attachments/assets/f6e79917-44e8-4b6b-acac-2e580ab4a3e0" />


Verification on console- 


Dynamodb table is deleted


<img width="1423" height="519" alt="Screenshot 2026-05-16 at 12 31 53 PM" src="https://github.com/user-attachments/assets/ab8696c4-1050-4c31-b0b7-9741a2d3a41c" />

We can see terraform.tfstate.tflock created 


<img width="1416" height="483" alt="Screenshot 2026-05-16 at 12 40 56 PM" src="https://github.com/user-attachments/assets/54f851ae-4d32-411c-ac78-d947a31b8de8" />


#### use_lockfile = true

terraform will create a temporary lock file in the statefiles in S3 bucket and use S3’s own mechanisms to ensure only one run can hold the lock

This time deleting the resource manually using the following command and not using destroy command :


aws s3 rb s3://richa-s3-bucket-state-file --force --region ap-south-1

##
##

## Provisioners : 


Used to execute scripts or shell commands on local or remote machines. one can perform bootstrap actions—such as installing software, patching kernels, or running configuration management that cannot be directly represented in Terraform's declarative infrastructure model.

 
 3 types-
      
   1. local-exec
   2. remote-exec
   3. file

Understood the concept of provisioners using the demonstration of deploying a python app on cloud using terraform.


## aws-ec2-terraform-nginx-deploy : https://github.com/richapofficial22/AWS-EC2-Terraform-Nginx-Deploy 
Automated EC2 provisioning and Nginx web server deployment on AWS using Terraform. Covers VPC, subnets, security groups, IGW, and file provisioning via SSH.

##
##

### Concept of workspaces

Showing the directory Day6 and module ec2_instance having main.tf files


- <img width="1392" height="349" alt="Screenshot 2026-05-18 at 11 26 49 AM" src="https://github.com/user-attachments/assets/4b8fdbb6-7135-42ec-bbac-7fb5af16d202" />

stage.tfvars & terraform.tfvars


- <img width="1390" height="89" alt="Screenshot 2026-05-18 at 11 29 01 AM" src="https://github.com/user-attachments/assets/deef4cdd-252e-4385-8018-c11c13f0a6b2" />


executed terraform init and then terraform apply. It executed and formed EC2 instance with terraform.tfvars file having instance type t2.micro

- <img width="722" height="229" alt="Screenshot 2026-05-18 at 11 31 20 AM" src="https://github.com/user-attachments/assets/ddd7e60b-2e56-4aef-aae7-8a76ea482b04" />

- <img width="1174" height="302" alt="Screenshot 2026-05-18 at 11 34 41 AM" src="https://github.com/user-attachments/assets/0556c65c-2592-4b5f-9969-b33018f46aa2" />


Executing terraform apply with stage.tfvars to see what will happen

- <img width="992" height="398" alt="Screenshot 2026-05-18 at 11 37 27 AM" src="https://github.com/user-attachments/assets/9e14c6b5-6e29-4735-9589-dd449744061a" />


the instance having type t2.micro changed to t2.medium
- <img width="1176" height="297" alt="Screenshot 2026-05-18 at 11 56 25 AM" src="https://github.com/user-attachments/assets/9a1ad508-b859-44c6-b467-ff7322d1a3fb" />

## Creating workspaces - dev, stage, prod 
 command : terraform workspace new "name of the workspace"

 - <img width="634" height="609" alt="Screenshot 2026-05-18 at 12 18 24 PM" src="https://github.com/user-attachments/assets/815cdad3-ec6c-4dda-802f-1d19f6c2b666" />

initialised terraform, then checked if any workspace was selected or not, then chose 'dev' as workspace.
- <img width="605" height="191" alt="Screenshot 2026-05-18 at 12 23 00 PM" src="https://github.com/user-attachments/assets/2337c6a1-f55e-4a12-b2ce-38c786372be2" />



executed terraform apply and now I can see that statefile has been created in the 'dev' workspace under terraform.tfstate.d . This statefile will show the work being done in 'dev' workspace irrespective of the other environments.
- <img width="458" height="237" alt="Screenshot 2026-05-18 at 12 25 03 PM" src="https://github.com/user-attachments/assets/fffadf48-50a9-4fcf-9919-655d61d54980" />



****We can work with workspaces in 2 ways (pertaining to the above demo) -
creating diffrent tfvars for different environments and then running terraform apply command with -var-file of the particular workspace OR automating this thing also into the main.tf file



main.tf :
 - <img width="701" height="382" alt="Screenshot 2026-05-18 at 1 02 21 PM" src="https://github.com/user-attachments/assets/df8a1766-e19d-43c2-aef7-d665d3419e66" />


terraform.tfvars :
 - <img width="327" height="101" alt="Screenshot 2026-05-18 at 1 04 11 PM" src="https://github.com/user-attachments/assets/ead00b81-9fb9-401a-b2ab-19c601764a6d" />


Since value for instance_type will be selected by the user when he chooses the workspace there is no need of terraform.tfvars to have instance_type variable. Selected 'prod' as workspace and ran terraform apply. 


Our EC2 instance has been created for 'prod' workspace having instance_type as 't2.xlarge'
- <img width="677" height="261" alt="Screenshot 2026-05-18 at 1 05 24 PM" src="https://github.com/user-attachments/assets/9f76c636-7cee-48e6-9010-63e536cb33ef" />
- <img width="1165" height="238" alt="Screenshot 2026-05-18 at 1 08 38 PM" src="https://github.com/user-attachments/assets/e1f752d9-09ef-47fe-8dae-0cdee413512c" />

We can see that a separate statefile has also been created for 'prod' workspace
- <img width="348" height="254" alt="Screenshot 2026-05-18 at 1 06 13 PM" src="https://github.com/user-attachments/assets/0d0c73ac-20b8-4224-9743-aa7e04d75512" />

##
##

### Secret management in terraform

Vault solves the problem of hardcoded credentials in Terraform code. Instead of writing AWS keys or passwords directly in .tf files, Vault stores secrets centrally and Terraform fetches them at runtime using the vault provider. This keeps sensitive values out of state files and version control. 
(Conceptual understanding — hands-on implementation planned)

##

terraform fmt : Automatically formats your .tf files to follow HashiCorp's standard style — indentation, spacing, alignment.
terraform fmt -check   # just checks, doesn't rewrite. used in CI pipelines
terraform fmt -recursive  # formats all subdirectories too

terraform validate : Checks configuration for syntax errors and logical issues without connecting to AWS.
terraform validate

Correct order : fmt → validate → plan → apply

##



























