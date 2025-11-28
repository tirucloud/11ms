# Steps to follow
Step 1: Open VS Code → Terminal → Run:
```
git clone https://github.com/tirucloud/11ms.git
```
Step 2: Configure AWS Keys
```
aws configure
```
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
Step 6: Connect to EC2 and Access Jenkins
From AWS Console → EC2 → Connect → Switch to root:
```
sudo -i
```
Verify installed DevOps tools:
```
git --version
java -version
jenkins --version
terraform -version
mvn -v
kubectl version --client --short
eksctl version
helm version --short
docker --version
trivy --version
```
Get Jenkins admin password:
```
cat /var/lib/jenkins/secrets/initialAdminPassword

example output :
0c39f23132004d508132ae3e0a7c70e4
```
Step 7: Jenkins Setup in Browser
```
Open: http://<EC2 Public IP>:8080
Paste admin password
```

- Install suggested plugins

- Create first user (user1)

- Click through: Save and Continue → Save and Finish → Start using Jenkins

Step 9: Install Jenkins Plugins
- Go to Jenkins Dashboard → Manage Jenkins → Plugins.
- Click the Available tab.
- Search and install the following:

- ✅ Pipeline: stage view

Step 10: Create a Jenkins Pipeline Job (Create EKS Cluster)
- Go to Jenkins Dashboard
- Click New Item
- Name it: eks-terraform
- Select: Pipeline
- Click OK

Pipeline:
- Definition : Pipeline script from SCM
- SCM : Git
- Repositories : https://github.com/tirucloud/11ms.git
- Branches to build : */main
- Script Path : eks-terraform/eks-jenkinsfile
- Apply
- Save
