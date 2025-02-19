# cloudboot

# Streamlined Guide: Using Claude as AI Assistant to Terraform

## Step 1: Use Claude to Generate Terraform Code

1. Create a FREE account with Claude: https://claude.ai 
2. Start a conversation with Claude.
3. Ask Claude to create Terraform code for an S3 bucket. Use a prompt like:
"Please provide Terraform code to create an S3 bucket in AWS with a unique name."
4. Claude should generate code similar to this:

   provider "aws" {
  region = "us-west-2"  # Replace with your desired region
}

resource "random_id" "bucket_suffix" {
  byte_length = 8
}

resource "aws_s3_bucket" "my_bucket" {
  bucket = "my-unique-bucket-name-${random_id.bucket_suffix.hex}"

  tags = {
    Name        = "My bucket"
    Environment = "Dev"
  }
}

resource "aws_s3_bucket_acl" "my_bucket_acl" {
  bucket = aws_s3_bucket.my_bucket.id
  acl    = "private"
}


## Step 2: Launch EC2 Instance

1. Create a FREE AWS account: https://aws.amazon.com/free/
2. Go to the EC2 dashboard in the AWS Management Console.
3. Click "Launch Instance".
4. Choose an Amazon Linux 2 AMI.
5. Select a t2.micro instance type.
6. Configure instance details:
    - Network: Default VPC
    - Subnet: Any available
    - Auto-assign Public IP: Enable
    - IAM role: Select "EC2Admin"
7. Keep default storage settings.
8. Add a tag: Key="Name", Value="workstation".
9. Create a security group allowing SSH access from EC2 Connect IP.
10. Review and launch, selecting or creating a key pair.
