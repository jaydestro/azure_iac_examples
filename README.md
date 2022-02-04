**# Azure Infrastructure as Code Examples**

This is a repo with examples of IaC you can deploy from the Azure Cloud Shell.  These commands work with either the bash or PowerShell offerings of Cloud Shell.  

## [Anisble](ansible/)

The Ansible guide will give you an example of creating an Azure Resource Group, Azure Virtual Machine, Network Security Group, and a Virtual Network.  You'll need to add a public ssh key to the `ssh_public_keys:` line within the [ansible/vm_create.yml](ansible/vm_create.yml) file.  Preferred method of storing this ssh key is with Azure Key Vault.  Full documentation on this procedure can be reviewed in the Microsoft Docs article [Create a Linux virtual machines in Azure using Ansible.](https://cda.ms/3LB)

[Get Started: Configure Ansible using Azure Cloud Shell](https://cda.ms/3LC) will give you details on configuration methods including setting your subscription context.

## [Azure Resource Manager Template](arm/)

The Azure Resource Manager template guide will show you how to create an Azure Resource Group and an Azure Storage Account.  You'll use the `az` command in a bash or PowerShell Cloud Shell session.  Once you've completed this deployment you will delete the resource group to clean up any used resources. Full documentation on this procedure can be reviewed in the Microsoft Docs article [How to use Azure Resource Manager (ARM) deployment templates with Azure CLI.](https://cda.ms/3N0)

## [Bicep](bicep/)

The Bicep Manager template guide will show you how to create an Azure Resource Group and an Azure Storage Account.  You'll use the `bicep` command in a bash or PowerShell Cloud Shell session.  Once you've completed this deployment you will delete the resource group to clean up any used resources. Full documentation on this procedure can be reviewed in the Microsoft Docs article [Quickstart: Create Bicep files with Visual Studio Code](https://cda.ms/3Nr).