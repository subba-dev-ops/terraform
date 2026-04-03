# Terraform  Setup

## 📌 Environment Setup

### 🔧 Software Required
- [Visual Studio Code](https://code.visualstudio.com/) – for editing Terraform files  
- [Terraform](https://developer.hashicorp.com/terraform/downloads) – Infrastructure as Code tool  
- [AWS CLI v2](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) – to configure AWS credentials  

### 🛠️ Steps
1. **Create IAM Administrator User**  
   - In AWS Console → IAM → Users → Create user with AdministratorAccess policy.  
   - Copy the **Access Key** and **Secret Key**.  
   ⚠️ **Never push these credentials to GitHub or share online.**

2. **Configure AWS CLI on your laptop**  
   ```bash
   aws configure
   Provide your access key, secret key, region, and output format.
- Add Terraform path to system variables
- On Windows: Add Terraform installation folder to PATH in Environment Variables.
- On Linux/Mac: Update .bashrc or .zshrc with Terraform path.

### 🌍 Why Terraform?
- Version Control
Infrastructure is code. Store it in GitHub for history, collaboration, and rollback.
- Consistent Infrastructure
Avoid mismatched configs across DEV, QA, PROD. Terraform ensures identical infra across environments.
- Automated Infra CRUD
Create, update, and delete infrastructure in minutes with minimal human error.
- Inventory Management
Terraform state files show all resources across regions, unlike manual setups.
- Cost Optimization
Spin up infra when needed, destroy when not — saving costs.
- Automatic Dependency Management
Terraform understands resource dependencies and provisions in the correct order.
- Modular Infrastructure
Reuse code with modules (your own or open-source). Speeds up infra creation.


## ⚙️ Terraform Commands
Initialize
Downloads provider plugins into .terraform folder.
```bash
terraform init
```


## Plan
Compares declared vs existing infra. No changes yet.
```bash
terraform plan
```

## Apply
Creates infra with approval.
```bash
terraform apply
```

## Destroy
Deletes infra to save cost.
```bash
terraform destroy
```

## 📝 Clarification on Arguments & Variables 

In Terraform, **arguments** are defined by the provider documentation.

Example:
```bash
resource "aws_instance" "terraform" {
  ami = "ami-09c813fb71547fc4f"
}
```

- ami → argument name (from AWS provider docs)
- "ami-09c813fb71547fc4f" → value
You can also use variables:
```bash
resource "aws_instance" "terraform" {
  ami = var.ami_id
}

variable "ami_id" {
  default = "ami-09c813fb71547fc4f"
}
```

Or with a different variable name:
```bash
resource "aws_instance" "terraform" {
  ami = var.ami
}

variable "ami" {
  default = "ami-09c813fb71547fc4f"
}
```


📂 Suggested Project Structure
```bash
terraform-ec2/
├── main.tf          # EC2 resource definition
├── variables.tf     # Input variables
├── outputs.tf       # Output values (e.g., public IP)
├── provider.tf      # AWS provider configuration
└── README.md        # Documentation```

