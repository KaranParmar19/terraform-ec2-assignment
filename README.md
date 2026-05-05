# Terraform EC2 Instance Assignment

## Objective
Learn Terraform basics including init, plan, apply, and creating AWS resources using Infrastructure as Code.

## Prerequisites
- Terraform installed
- AWS account with access keys
- AWS credentials configured

## Project Structure
terraform-ec2-assignment/
├── main.tf
├── variables.tf
└── README.md

## Terraform Files

### main.tf
```hcl
provider "aws" {
  region = "ap-south-1"
}

resource "aws_instance" "my_instance" {
  ami           = "ami-0f58b397bc5c1f2e8"
  instance_type = "t3.micro"

  tags = {
    Name = "Terraform-Student-Instance"
  }
}

output "instance_public_ip" {
  value = aws_instance.my_instance.public_ip
}
```

## Steps to Run

### Step 1: Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/terraform-ec2-assignment.git
cd terraform-ec2-assignment
```

### Step 2: Configure AWS Credentials
```bash
mkdir -p ~/.aws
nano ~/.aws/credentials
```
Add the following:
[default]
AWS_ACCESS_KEY_ID=AKIAR2NQCISDNNLKO6MP
 AWS_SECRET_ACCESS_KEY=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
AWS_DEFAULT_REGION="ap-south-1"

### Step 3: Initialize Terraform
```bash
terraform init
```
This command downloads the AWS provider plugin.

### Step 4: Plan the infrastructure
```bash
terraform plan
```
This command shows what resources will be created.

### Step 5: Apply and create resources
```bash
terraform apply
```
Type `yes` when prompted. This creates the EC2 instance on AWS.

### Step 6: Verify
- Go to AWS Console
- Search EC2
- Click Instances
- You should see "Terraform-Student-Instance" running

### Step 7: Destroy resources (cleanup)
```bash
terraform destroy
```
Type `yes` to delete the EC2 instance after submission.

## Resources Created
| Resource | Value |
|----------|-------|
| Provider | AWS |
| Region | ap-south-1 (Mumbai) |
| Instance Type | t3.micro |
| AMI | ami-0f58b397bc5c1f2e8 (Amazon Linux) |
| Tag Name | Terraform-Student-Instance |

## Output
After running terraform apply, you will see:
Apply complete! Resources: 1 added, 0 changed, 0 destroyed.
Outputs:
instance_public_ip =  "13.233.196.61"

## Commands Summary
| Command | Description |
|---------|-------------|
| terraform init | Initialize Terraform and download providers |
| terraform plan | Preview changes before applying |
| terraform apply | Create the actual AWS resources |
| terraform destroy | Delete all created resources |
