# Databricks CI/CD

## Todo

- [ ] Create Databricks instance with Terraform
- [ ] Deploy Databricks Asset Bundle (DAB)
- [ ] Create GitHub Actions CD pipeline
- [ ] Deploy specific DAB based on modified files
- [ ] Create Databricks Runtime Docker CI pipeline

## Installation

### Prerequisites

- Azure CLI
- Terraform

## Usage

```bash
# Initialize Terraform
terraform init -upgrade

# Login and retrieve Azure subscription
az login
export ARM_SUBSCRIPTION_ID=$(az account show --query id --output tsv)

# Create resources
terraform plan -out main.tfplan
terraform apply main.tfplan

# Validate
resource_group_name=$(terraform output -raw resource_group_name)
az group show --name $resource_group_name

# Clean up
terraform plan -destroy -out main.destroy.tfplan
terraform apply main.destroy.tfplan
```

## Links

- https://learn.microsoft.com/en-us/azure/developer/terraform/create-resource-group
- https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/guides/azure_cli#configuring-azure-cli-authentication-in-terraform
- https://portal.azure.com
