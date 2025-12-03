# ansible-aws-vpc

This project automates the creation of an AWS Virtual Private Cloud (VPC) environment using Ansible.
It provisions core networking components such as:

VPC

Public Subnets

Internet Gateway

Route Tables

Bastion Host (EC2)

Tags & variable-driven configuration

All resources are created using Ansible’s amazon.aws collection.

# PROJECT STRUCTURE

```
ansible-aws-vpc/
│
├── vpc-setup.yml              # Main playbook to create VPC + subnets + networking
├── bastion-instance.yml       # Playbook to create Bastion EC2 instance
│
├── vars/
│   ├── vpc_setup              # Variables for VPC creation (CIDR blocks, region, tags)
│   ├── bastion_setup          # Variables for Bastion instance (AMI, instance type, keypair)
│   └── output_vars            # Output variables captured from provisioning
│
├── .gitignore
└── README.md
```

# What This Automation Does
1. Creates a custom AWS VPC
   VPC Name
   VPC CIDR block
   DNS support + DNS hostnames
   Tags applied (e.g., Project: vprofile)

2. Creates Public Subnets
   Zone-specific CIDR blocks
   Subnet taggingPublic route exposure

3. Attaches an Internet Gateway
   Creates IGW
   Attaches it to the VPC
   Updates Route Table

4. Provisions a Bastion Host (optional)
   EC2 instance in the public subnet
   Key pair generation
   Security group rules
   Tags & metadata

# Prerequisites

Before running the playbooks:

1. Install Ansible
sudo apt update
sudo apt install ansible

2. Install required AWS collection
ansible-galaxy collection install amazon.aws

3. Export AWS credentials
export AWS_ACCESS_KEY_ID="YOUR_KEY"
export AWS_SECRET_ACCESS_KEY="YOUR_SECRET"
export AWS_DEFAULT_REGION="us-east-1"
