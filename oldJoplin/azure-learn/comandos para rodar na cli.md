comandos para rodar na cli

atribuição de algumas variaveis a serem utilizadas:

export RESOURCE_GROUP=learn-4ce52682-2345-4aa7-9780-2c1b72c2cab0

export AZURE_REGION=centralus

export AZURE\_APP\_PLAN=popupappplan-$RANDOM

export AZURE\_WEB\_APP=popupwebapp-$RANDOM

mostra todos os grupos de recursos:

az group list --output table

aqui vc pode fazer uma query para filtrar grupos:

az group list --query "\[?name == '$RESOURCE_GROUP'\]"

mostra todos os outbounds IPs de recursos:

> az webapp show \
> 
> --resource-group &lt;group_name&gt; \
> 
> --name &lt;app_name&gt; \
> 
> --query possibleOutboundIpAddresses \
> 
> --output tsv