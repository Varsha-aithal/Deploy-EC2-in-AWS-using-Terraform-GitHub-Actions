# Deploy EC2 in AWS using Terraform + GitHub Actions

## Project overview
This project provisions an **AWS EC2 instance** using Terraform (Infrastructure as Code) and triggers the deployment through a **manual GitHub Actions workflow** where you enter the EC2 name and run the pipeline.

## Repository structure
```text
.
├── .github/
│   └── workflows/
│       └── provision_ec2_instance.yml
├── Terraform-Project-1/
│   ├── main.tf
│   └── variables.tf
└── README.md
```

## What each file does
**.github/workflows/provision_ec2_instance.yml** - Defines a GitHub Actions workflow that you can trigger manually using workflow_dispatch (you’ll see a Run workflow button in the Actions tab, and it will show input fields).

**Terraform-Project-1/main.tf** - Main Terraform configuration that defines the AWS resources (EC2 provisioning logic).

**Terraform-Project-1/variables.tf** - Defines Terraform input variables.

## GitHub Secrets
Before running the workflow, create an IAM user/credentials and add them to GitHub Secrets, then reference them in the workflow as environment variables like AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY.

## How to run (GitHub Actions)
1. Open your GitHub repository and go to the Actions tab.
2. Select provision_ec2_instance.yml (the workflow) from the list.
3. Click Run workflow.
4. Enter the EC2 name (input field shown by workflow_dispatch inputs).
5. Click Run workflow again to start the job.
6. After it finishes, log in to the AWS Console → EC2 and verify that the instance has been created.

## (Optional) Run locally
If you want to run Terraform from your machine:
1. cd Terraform-Project-1
2. terraform init
3. terraform plan
4. terraform apply
