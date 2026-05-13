
# Learning-Terraform

- Source : https://www.youtube.com/watch?v=fgp-t5SqQmM&list=PLdpzxOOAlwvI0O4PeKVV1-yJoX2AqIWuf
- Github repo for instructor notes : https://github.com/iam-veeramalla/terraform-zero-to-hero/blob/main/README.md

## Started with Terraform-Zero-to-Hero by Abhishek Veeramalla
**Setup:**

1.  Installed Terraform on my macbook-pro

    <img width="436" height="88" alt="Screenshot 2026-05-06 at 8 59 47 AM" src="https://github.com/user-attachments/assets/34b94d90-8a53-47ea-9215-83b85a7a2d1b" />
3.  Using VSCode to run terraform 
    <img width="1440" height="900" alt="Screenshot 2026-05-06 at 9 26 41 AM" src="https://github.com/user-attachments/assets/31efc2bd-a65d-4aec-b9ab-c5910d5bc7f7" />
4.  Installed AWS CLI using-
    ``` brew install awscli ```
    <img width="1440" height="281" alt="Screenshot 2026-05-06 at 5 53 32 PM" src="https://github.com/user-attachments/assets/483b8b80-ac52-453e-aa2f-701e9d5256a0" />
5.  Adding programmatic access to already created IAM User- AdminRP 
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

#### ec2 instance created suucessfully
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
terraform.tfvars
when using terraform apply (terraform.tfvars values are taken automatically)
But if default/initial values are in some other files (eg. dev.tfvars) then we use command terraform apply --dev.tfvars


Created 3 terraform files-

<img width="310" height="367" alt="Screenshot 2026-05-07 at 5 44 38 PM" src="https://github.com/user-attachments/assets/df040c41-05e2-4df2-ba24-597e988e7be2" />

### main.tf

   ```
       provider "aws" {
       region = "ap-south-1"
        }

       resource "aws_instance" "e1" {
       ami = var.ami_value
       instance_type = var.instance_type_value
        }

   ```
### variables.tf


   ```
       variable "ami_value" {
       description = "value for ami_value"
        }

       variable "instance_type_value" {
       description = "value for instance_type"
        }
   ```

### terraform.tfvars

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

### Modules
Modules are a set of files grouped in a single directory and they can be accessed by multiple users any no. of times if only the path of module is known to the user. 


Creating module

Created a folder modules/M1 and put the files main.tf , variables.tf and output.tf in it.

<img width="311" height="359" alt="Screenshot 2026-05-07 at 9 32 46 PM" src="https://github.com/user-attachments/assets/2e118f2e-901c-406e-a435-677d75e47a4c" />

Outside modules folder created the follwing main.tf file inside project2 folder

<img width="765" height="812" alt="Screenshot 2026-05-07 at 9 33 17 PM" src="https://github.com/user-attachments/assets/aa907987-addb-4e53-acde-e7117be6e0cf" />

Ran the terraform commands to get our EC2 instance created again. 

<img width="1178" height="339" alt="Screenshot 2026-05-07 at 9 33 44 PM" src="https://github.com/user-attachments/assets/54a604df-b1c0-414a-8435-008fb03e56ab" />

##
##


Importance of statefiles

apply and destroy use statefiles to check what actions they need to perform 

drawbacks: it records everything including passwords and other sensitive information

<img width="679" height="432" alt="Screenshot 2026-05-09 at 1 46 08 PM" src="https://github.com/user-attachments/assets/ecd23559-2622-4840-8ec4-f8fdd934770e" />

 terraform show gives statefile

 S3 bucket me terraform state file save kiya to fir usko sirf wahi access kr paega jiske pas s3w bucket ka access h. 
 locking mechanism dynamodb table
 



























