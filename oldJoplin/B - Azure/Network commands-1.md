Network commands

RGROUP=$(az group create --name vmbackups --location westus2 --output tsv --query name)


az network vnet create --resource-group $RGROUP --name NorthwindInternal --address-prefixes 10.0.0.0/16 --subnet-name NorthwindInternal1 --subnet-prefixes 10.0.0.0/24