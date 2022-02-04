The Bicep Manager template guide will show you how to create an Azure Resource Group and an Azure Storage Account.  You'll use the `az deployment` command in a bash or PowerShell Cloud Shell session.  Once you've completed this deployment you will delete the resource group to clean up any used resources. Full documentation on this procedure can be reviewed in the Microsoft Docs article [Quickstart: Create Bicep files with Visual Studio Code](https://cda.ms/3Nr).

To deploy a Bicep file or ARM template, you need write access on the resources you're deploying and access to all operations on the Microsoft.Resources/deployments resource type. For example, to deploy a virtual machine, you need `Microsoft.Compute/virtualMachines/write` and `Microsoft.Resources/deployments/*` permissions.

## Deploy

**Clone this repo in Azure Cloud Shell and enter the bicep directory**

```bash
git clone git@github.com:jaydestro/azure_iac_examples.git
cd azure_iac_examples/bicep
```

The [main.json](./azuredeploy.json) contains instructions to create a storage account.  There are no modifications required to this template as our parameters are specified in the `az deployment` command.

```bash
az group create --name ExampleGroup --location eastus
az deployment group create --resource-group exampleRG --template-file main.bicep --parameters storageName=uniquename
```

When the deployment finishes, you should see a message indicating the deployment succeeded.

##  **Deleting Azure Resources**

Run the `az destroy` command to delete all resources int he ExampleGroup resource group:

```bash
az group delete --resource-group ExampleGroup -y
```

