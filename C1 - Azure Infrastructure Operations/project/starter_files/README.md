# Azure Infrastructure Operations Project: Deploying a scalable IaaS web server in Azure

This repository contains the project, which demonstrates the deployment of a policy and an image created from a Packer template. The resulting image is then used by Terraform for infrastructure deployment.

---

## **Project Overview**

This project involves:

1. Creating a policy and assigning it to a resource group.
2. Building a virtual machine image using  **Packer** .
3. Deploying infrastructure using  **Terraform** .

---

## **Dependencies**

Ensure you have the following installed and set up before proceeding:

1. Create an [Azure Account](https://portal.azure.com/)
2. Install the [Azure command line interface](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest)
3. Install [Packer](https://www.packer.io/downloads)
4. Install [Terraform](https://www.terraform.io/downloads.html)

---

## **Setup and Deployment**

### **1. Export Environment Variables**

Before running Packer or Terraform, export the following environment variables with your Azure credentials. Add them to your `.bashrc`, `.zshrc`, or equivalent shell configuration file for easier reuse:

```bash
export AZ_CLIENT_ID=00000000-0000-0000-0000-000000000000
export AZ_CLIENT_SECRET=00000000000000000000000000000000
export AZ_TENANT_ID=00000000-0000-0000-0000-000000000000
export AZ_SUBSCRIPTION_ID=00000000-0000-0000-0000-000000000000
```

**Note:** Replace the placeholder values with your actual Azure credentials.

---

### **2. Create a Resource Group**

Create a resource group for this project using either the Azure Portal or Azure CLI:

**Using Azure CLI:**

```bash
az group create --name udacity-assignment1-rg --location <location>
```

---

### **3. Deploy the Policy**

Deploy the policy and assign it to your resource group. You can do this via the Azure Portal or Azure CLI.

---

### **4. Build the Packer Image**

Run the following command to build the Packer image:

```bash
packer build packer/server.json
```

---

### **5. Prepare Terraform**

Navigate to the Terraform directory and initialize the Terraform configuration:

```bash
terraform init
```

Generate an execution plan:

```bash
terraform plan -out solution.plan
```

---

### **6. Deploy Infrastructure with Terraform**

Apply the Terraform plan to deploy your infrastructure:

```bash
terraform apply "solution.plan"
```

---

### **7. Clean Up**

To destroy the infrastructure after testing, run:

```bash
terraform destroy
```

---

## **Configuration**

The file `terraform/vars.tf` contains all the variables used in `terraform/main.tf`. If you need to customize the deployment (e.g., resource names, regions, or VM configurations), modify the variables in `vars.tf`.

---

## **Acknowledgements**

* **rfoltz** : A well-structured project that provided valuable insights, particularly for the Terraform section.
* **Udacity Community** : Special thanks to the students and mentors for their guidance, especially on the Policy and Packer sections.

---

By following this guide, you'll be able to replicate the project and deploy infrastructure on Azure using DevOps tools. If you encounter any issues, feel free to explore the resources or reach out for support.

---

This revised version adds structure, improves readability, and ensures clarity for anyone attempting to follow the instructions. Let me know if you need further modifications! 😊
