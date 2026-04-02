como criar um AppService Plan:

az appservice plan create --help

az appservice plan create --name $AZURE\_APP\_PLAN --resource-group $RESOURCE\_GROUP --location $AZURE\_REGION --sku FREE

mostra uma lista de todos os appservices:

az appservice plan list --output table

criando um webapp:

az webapp create --name $AZURE\_WEB\_APP --resource-group $RESOURCE\_GROUP --plan $AZURE\_APP_PLAN

lista os webapp:

az webapp list --output table

da pra dar deploy direto do github:

az webapp deployment source config --name $AZURE\_WEB\_APP --resource-group $RESOURCE_GROUP --repo-url "https://github.com/Azure-Samples/php-docs-hello-world" --branch master --manual-integration

**também é possível fazer o deploy no diretorio:**

cd html-docs-hello-world

az webapp up -g $resourceGroup -n $appName --html