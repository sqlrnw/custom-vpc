# 🏗️ Custom VPC on AWS using Terraform

This project provisions a complete custom Virtual Private Cloud (VPC) infrastructure on AWS using **Terraform**.

It is designed as a production-grade networking setup that includes public and private subnets, internet and NAT gateways, and routing configuration — all from scratch.

---

## 📦 What’s Created

| Component             | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **VPC**               | Main VPC with CIDR `10.0.0.0/16`                                            |
| **Public Subnets**    | Two public subnets in `us-east-1a` and `us-east-1b`                         |
| **Private Subnets**   | Two private subnets in `us-east-1a` and `us-east-1b`                        |
| **Internet Gateway**  | Enables internet access for public subnets                                  |
| **NAT Gateway**       | Allows private subnets to access the internet securely                      |
| **Elastic IP**        | Static IP address attached to NAT Gateway                                   |
| **Route Tables**      | Routing rules for public and private traffic                                |
| **Subnet Associations** | Properly links subnets to their respective route tables                  |

---

## 📐 Architecture Diagram

vbnet
Copy
Edit
      ┌────────────┐
      │  Internet  │
      └─────┬──────┘
            │
     ┌──────▼───────┐
     │   IGW        │
     └──────┬───────┘
            │
    ┌───────▼────────┐
    │   custom-vpc   │ (10.0.0.0/16)
    └───────┬────────┘
 ┌────────┐ └────────────┐
 │ public │              │ private
 │ subnets│              │ subnets
 └────────┘              └────────────
    │                       │
┌────▼────┐ ┌────▼────┐
│ EC2 │ │ EC2 │
│Public IP│ │No Pub IP│
└─────────┘ └─────────┘
│ │
┌──▼──┐ ┌────▼────┐
│ RT │ │ NAT │
└─────┘ └─────────┘

yaml
Copy
Edit

---

## 🛠️ How to Use

### 1. Clone this repo

```bash
git clone https://github.com/your-username/custom-vpc.git
cd custom-vpc
2. Initialize Terraform
bash
Copy
Edit
terraform init
3. Apply the Configuration
bash
Copy
Edit
terraform apply
✅ Confirm the plan with yes when prompted.

📁 File Structure
bash
Copy
Edit
custom-vpc/
├── main.tf          # Terraform configuration file
├── .gitignore       # Git ignore file for Terraform
└── README.md        # Project documentation
🔐 Security Note
This project does not include:

Any EC2 instances

SSH Keys or sensitive credentials

It is purely focused on network infrastructure only.

