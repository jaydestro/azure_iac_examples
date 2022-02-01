**# Azure Infrastructure as Code Examples**

This is a repo with examples of IaC you can deploy from the Azure Cloud Shell.  These commands work with either the bash or PowerShell offerings of Cloud Shell.  

## [Anisble](ansible/)

The Ansible guide will give you an example of creating an Azure Resource Group, Azure Virtual Machine, Network Security Group, and a Virtual Network.  You'll need to add a public ssh key to the `ssh_public_keys:` line within the [ansible/vm_create.yml](ansible/vm_create.yml) file.  Preferred method of storing this ssh key is with Azure Key Vault.  Full documentation on this procedure can be reviewed in the Microsoft Docs article [Create a Linux virtual machines in Azure using Ansible.](https://cda.ms/3LB)

[Get Started: Configure Ansible using Azure Cloud Shell](https://cda.ms/3LC) will give you details on configuration methods including setting your subscription context.