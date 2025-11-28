# Steps to follow
Step 1: Open VS Code → Terminal → Run:
```
git clone https://github.com/tirucloud/11ms.git
```
Step 2: Configure AWS Keys
aws configure

Step 3: Navigate into the Project
cd Microservices-E-Commerce-eks-project

Step 4: Create S3 Buckets for Terraform State
```
cd s3-buckets/
terraform init
terraform plan
terraform apply -auto-approve
```
Step 5: Create Network Infrastructure, Navigate to Terraform EC2 setup:
```
cd ../terraform_main_ec2
terraform init
terraform plan
terraform apply -auto-approve
```
