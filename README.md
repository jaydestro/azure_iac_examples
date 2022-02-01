**# Azure Infrastructure as Code Examples**

This is a repo with examples of IaC you can deploy from the Azure Cloud Shell.  These commands work with either the bash or PowerShell offerings of Cloud Shell.  

## Anisble

The Ansible guide will give you an example of creating an Azure Virtual Machine, Network Security Group, and a Virtual Network.  You'll need to add a public ssh key to the `ssh_public_keys:` line within the [ansible/main.yaml](ansible/main.yaml) file.  Preferred method of storing this ssh key is with Azure Key Vault.  Full documentation on this procedure can be reviewed in the Microsoft Docs article Create a Linux virtual machines in Azure using Ansible.