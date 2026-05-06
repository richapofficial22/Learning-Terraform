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
      - Finally AdminRP is showing as the user in terraform
        ```
         richierich@Richies-MacBook-Pro Desktop % aws sts get-caller-identity
        {
         "UserId": "AIDAT2WDJAUMAOZUPWSBD",
         "Account": "263476282648",
         "Arn": "arn:aws:iam::263476282648:user/AdminRP"
        }
         ```

## 

