# 🌍 Terraform Basics

## What is Terraform?

Terraform is an **Infrastructure as Code (IaC)** tool that lets you define and manage infrastructure (servers, networks, databases, storage, etc.) using configuration files instead of manually creating resources in a cloud console.

Terraform uses a declarative language called **HCL (HashiCorp Configuration Language)**.

---

# 🔄 Terraform Workflow

1. **Write** the infrastructure configuration (`.tf` files).

2. **Initialize** the working directory.

```bash
terraform init
```

3. **Preview** the changes.

```bash
terraform plan
```

4. **Create or Update** infrastructure.

```bash
terraform apply
```

5. **Destroy** infrastructure (if needed).

```bash
terraform destroy
```

---

# 📄 Basic Terraform Configuration

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "web" {
  ami           = "ami-0abcdef1234567890"
  instance_type = "t2.micro"

  tags = {
    Name = "Terraform-Server"
  }
}
```

---

# 🛠 Common Terraform Commands

| Command | Purpose |
|----------|---------|
| `terraform init` | Initialize project and download providers |
| `terraform fmt` | Format configuration files |
| `terraform validate` | Validate configuration syntax |
| `terraform plan` | Preview infrastructure changes |
| `terraform apply` | Create or update infrastructure |
| `terraform destroy` | Remove managed infrastructure |
| `terraform show` | Display the current state |

---

# 📚 Key Terraform Concepts

## Provider

A plugin that allows Terraform to interact with cloud platforms such as:

- AWS
- Azure
- Google Cloud
- Docker
- Kubernetes

---

## Resource

An infrastructure object managed by Terraform.

Examples:

- EC2 Instance
- Virtual Machine
- VPC
- S3 Bucket
- Database

---

## Variable

Variables allow you to make Terraform configurations reusable by accepting input values.

Example:

```hcl
variable "instance_type" {
  default = "t2.micro"
}
```

---

## Output

Outputs display useful information after Terraform has finished creating infrastructure.

Example:

```hcl
output "instance_id" {
  value = aws_instance.web.id
}
```

---

## State File

Terraform stores information about your infrastructure in a file named:

```
terraform.tfstate
```

The state file helps Terraform determine:

- What resources already exist
- What needs to be created
- What needs to be updated
- What needs to be destroyed

---

## Module

A **Module** is a reusable collection of Terraform configurations.

Benefits:

- Reusable code
- Easier maintenance
- Better organization
- Standardized infrastructure

---

# 📝 Example Variable

```hcl
variable "instance_type" {
  default = "t2.micro"
}

resource "aws_instance" "web" {
  ami           = "ami-0abcdef1234567890"
  instance_type = var.instance_type
}
```

---

# 📤 Example Output

```hcl
output "instance_id" {
  value = aws_instance.web.id
}
```

---

# 📂 Typical Terraform Project Structure

```
terraform-project/
│
├── main.tf
├── variables.tf
├── outputs.tf
├── providers.tf
├── versions.tf
├── terraform.tfvars
├── .gitignore
└── README.md
```

---

# 🚀 Terraform Workflow Summary

```text
Write Configuration (.tf)
          │
          ▼
terraform init
          │
          ▼
terraform plan
          │
          ▼
terraform apply
          │
          ▼
Infrastructure Created
          │
          ▼
terraform destroy (Optional)
```

---

# ✅ Advantages of Terraform

- Infrastructure as Code (IaC)
- Multi-cloud support
- Version control with Git
- Declarative syntax
- Reusable modules
- Automatic dependency management
- Execution plan before changes
- Consistent deployments

---

# 🎯 Conclusion

Terraform simplifies infrastructure management by allowing you to define cloud resources as code. It provides consistency, automation, version control, and repeatable deployments across multiple cloud platforms.
