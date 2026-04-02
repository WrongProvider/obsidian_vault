JSON ARM TEMPLATE

az login

```
az group create --name {name of your resource group} --location "{location}"
```

```
templateFile="{provide-the-path-to-the-template-file}"
az deployment group create --name blanktemplate --resource-group myResourceGroup --template-file $templateFile
```


Adicione a extenção de ARM template no VScode

az account set --subscription "Concierge Subscription"

az account list --refresh --query "[?contains(name, 'Concierge Subscription')].id" --output table

az account set --subscription {your subscription ID}

az configure --defaults group="learn-38f2d22c-7424-4b3b-8d8e-5927123fcfe3"

templateFile="azuredeploy.json"
today=$(date +"%d-%b-%Y")
DeploymentName="addstorage-"$today

az deployment group create \
  --name $DeploymentName \
  --template-file $templateFile

ARM!
arm-storage

```
{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {},
    "functions": [],
    "variables": {},
    "resources": [{
        "name": "receba123123213asdsadsa",
        "type": "Microsoft.Storage/storageAccounts",
        "apiVersion": "2023-05-01",
        "tags": {
            "displayName": "receba123123213asdsadsa"
        },
        "location": "[resourceGroup().location]",
        "kind": "StorageV2",
        "sku": {
            "name": "Standard_LRS",
            "tier": "Premium"
        }
    }],
    "outputs": {}
}

```

os campos Name e display devem ser unicos

