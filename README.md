<img width="493" height="213" alt="Screenshot 2026-05-07 at 7 01 49 AM" src="https://github.com/user-attachments/assets/181a0143-e63c-44d4-ba3c-c94da10178f5" />
# Learning-Terraform

Started with Terraform-Zero-to-Hero by Abhishek Veeramalla

- Source : https://www.youtube.com/watch?v=fgp-t5SqQmM&list=PLdpzxOOAlwvI0O4PeKVV1-yJoX2AqIWuf
- Github repo for instructor notes : https://github.com/iam-veeramalla/terraform-zero-to-hero/blob/main/README.md
##
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
### Project : Creation of EC2 instance 
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

  After writing the tf files we run terraform commands in the same folder where our file is stored to create the infrastructure

  terraform init

  <img width="517" height="255" alt="Screenshot 2026-05-07 at 7 02 30 AM" src="https://github.com/user-attachments/assets/6a1ce120-bfee-4165-8116-5851bd3085c3" />


  <img width="585" height="340" alt="Screenshot 2026-05-07 at 7 30 37 AM" src="https://github.com/user-attachments/assets/27403598-df4a-4a53-a586-bb9dd1b8ebbf" />

terraform plan

 <img width="1000" height="823" alt="Screenshot 2026-05-07 at 7 39 18 AM" src="https://github.com/user-attachments/assets/eb170c84-da2f-416f-8f11-d05fe6d9d9d6" />

Error on terraform apply - ec2 instance related issue
<img width="1165" height="541" alt="Screenshot 2026-05-07 at 7 45 21 AM" src="https://github.com/user-attachments/assets/bc342482-2ac8-4ac6-b4fd-2ae55dc5cebb" />

we go to our console and get the ami-id of the instance we want to create

<img width="921" height="655" alt="Screenshot 2026-05-07 at 7 49 33 AM" src="https://github.com/user-attachments/assets/d423fc79-98ad-40e8-b612-7218ee02b5b7" />

ec2 instance created suucessfully
<img width="765" height="847" alt="Screenshot 2026-05-07 at 7 57 29 AM" src="https://github.com/user-attachments/assets/7fc85464-e648-4601-810f-217c7b3675b2" />


The instance created here is having [id=i-0f1dffdbd2870e283]
we can cross-verify this in our AWS management console- 
And we can see that our instance is up and running which was made by coding- 
<img width="1174" height="334" alt="Screenshot 2026-05-07 at 8 09 01 AM" src="https://github.com/user-attachments/assets/baf0bc85-b706-4815-919c-e583282c8019" />


Lifecycle of terraform- init, plan, apply, destroy 


Ran this command to stop the instance

<img width="725" height="273" alt="Screenshot 2026-05-07 at 8 17 06 AM" src="https://github.com/user-attachments/assets/17b46bf5-69f7-4e0b-be04-774b51f7f3a7" />

now completely deleting the ec2 instance 
<img width="691" height="547" alt="Screenshot 2026-05-07 at 8 18 24 AM" src="https://github.com/user-attachments/assets/4acc6f88-4c4d-4e4f-abc2-04aaf34f108b" />
<img width="1170" height="283" alt="Screenshot 2026-05-07 at 8 19 31 AM" src="https://github.com/user-attachments/assets/2dba7e09-0bdf-4351-9d6f-8b9055091e2a" />












