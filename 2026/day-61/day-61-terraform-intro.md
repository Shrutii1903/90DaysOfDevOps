# Terraform Basics — Day 61

## Overview

This project demonstrates the fundamentals of Infrastructure as Code (IaC) using Terraform by provisioning and managing AWS resources through configuration files.

By the end of this exercise, an S3 bucket and an EC2 instance were created, modified, and destroyed entirely using Terraform.

---

## What is Infrastructure as Code (IaC)?

Infrastructure as Code is the practice of managing infrastructure using code instead of manual processes. It allows teams to define, provision, and manage resources in a consistent and automated way.

### Benefits:

* Reproducibility
* Version control
* Automation
* Reduced human error

---

## Tools Comparison

* **Terraform**: Declarative and cloud-agnostic
* **CloudFormation**: AWS-specific
* **Ansible**: Configuration management tool
* **Pulumi**: Uses programming languages for IaC

---

## Project Setup

### Prerequisites

* Terraform installed
* AWS CLI configured
* Valid AWS credentials

### Verification

```
terraform -version
aws sts get-caller-identity
```

---

## Resources Created

* AWS S3 Bucket
* AWS EC2 Instance (t2.micro)

---

## Terraform Workflow

### 1. Initialize

```
terraform init
```

Downloads required provider plugins.

### 2. Plan

```
terraform plan
```

Shows execution plan before applying changes.

### 3. Apply

```
terraform apply
```

Creates or updates resources.

### 4. Destroy

```
terraform destroy
```

Deletes all managed resources.

---

## State Management

Terraform uses a state file (`terraform.tfstate`) to track infrastructure.

### Stores:

* Resource definitions
* AWS resource IDs
* Current state of infrastructure

### Important:

* Do not manually edit the state file
* Do not commit it to version control

---

## Modification Example

Updated EC2 tag:

```
Name = "terra-auto-server" → "terra-auto-server-modified"
```

### Plan Output Symbols:

* `~` Modify (in-place)
* `+` Create
* `-` Destroy

Result: In-place update (no resource recreation required)

---

## Resource Replacement (Recreate)

Terraform recreates resources when immutable attributes are changed.

### Examples:

* AMI change
* Subnet change
* Availability Zone change

### Plan Indicator:

```
-/+
```

Indicates resource replacement.

---

## Key Learnings

* Infrastructure can be managed entirely through code
* Terraform state is critical for tracking resources
* `terraform plan` helps prevent unintended changes
* Not all changes require resource recreation

---


---

## Conclusion

This project demonstrates the core Terraform workflow: provisioning, updating, and destroying infrastructure using code. It establishes a foundation for more advanced topics such as modules, remote state, and automation in CI/CD pipelines.
