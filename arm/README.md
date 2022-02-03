# Azure Resource Manager Template

The Azure Resource Manager template guide will show you how to create an Azure Resource Group and an Azure Storage Account.  You'll use the `az` command in a bash or PowerShell Cloud Shell session.  Once you've completed this deployment you will delete the resource group to clean up any used resources. Full documentation on this procedure can be reviewed in the Microsoft Docs article [How to use Azure Resource Manager (ARM) deployment templates with Azure CLI.](https://cda.ms/3N0)

To deploy a Bicep file or ARM template, you need write access on the resources you're deploying and access to all operations on the Microsoft.Resources/deployments resource type. For example, to deploy a virtual machine, you need `Microsoft.Compute/virtualMachines/write` and `Microsoft.Resources/deployments/*` permissions.

**## Deploy**

**\*Clone this repo in Azure Cloud Shell and enter the** **`arm`** **directory\****

```bash
git clone git@github.com:jaydestro/azure_iac_examples.git
cd azure_iac_examples/arm
```

The [azuredeploy.json](./azuredeploy.json) contains instructions to create a storage account.  There are no modifications required to this template as our parameters are specified in the `az deployment` command.

```bash
az group create --name ExampleGroup --location eastus
az deployment group create \
  --name ExampleDeployment \
  --resource-group ExampleGroup \
  --template-file azuredeploy.json \
  --parameters storageAccountType=Standard_GRS
```

Azure Resource Manager will deploy the template with the Standard_GRS SKU in a few minutes.  You can review the created deployment by listing the storage account with the `az` command:

```bash
az storage account list --resource-group ExampleGroup
```

You'll be provided with a JSON output with a description and details of your deployed storage account, example snippet:

```json
  allowBlobPublicAccess: true
  allowCrossTenantReplication: null
  allowSharedKeyAccess: null
  azureFilesIdentityBasedAuthentication: null
  blobRestoreStatus: null
  creationTime: '2022-02-03T17:04:20.766891+00:00'
  customDomain: null
  defaultToOAuthAuthentication: null
  enableHttpsTrafficOnly: true
  enableNfsV3: null
  encryption:
    encryptionIdentity: null
    keySource: Microsoft.Storage
    keyVaultProperties: null
    requireInfrastructureEncryption: null
```

**## Deleting Azure Resources**

Run the `az destroy` command to delete all resources int he ExampleGroup resource group:

```bash
az group delete --resource-group ExampleGroup -y
```