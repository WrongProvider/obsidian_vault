Policies

microsoft cloud framework

&nbsp;

![c8e64933bf6c2c8c1bc8f8e6dcbdc9bc.png](../_resources/c8e64933bf6c2c8c1bc8f8e6dcbdc9bc.png)

&nbsp;

passo a passo da governanca

![67133dc35ce6bd3ad097b3d924aea15d.png](../_resources/67133dc35ce6bd3ad097b3d924aea15d.png)

&nbsp;

Considerações da governanca

![ba897e622f6fa942baa1431a4e22804d.png](../_resources/ba897e622f6fa942baa1431a4e22804d.png)

&nbsp;

a ferramenta para isso

https://learn.microsoft.com/en-us/azure/governance/policy/overview

tem um dashboad de compliance

&nbsp;

Design

control plane

![e83501fc42661ff5974c3e52e70e8971.png](../_resources/e83501fc42661ff5974c3e52e70e8971.png)

&nbsp;

data:

geralmente é controlada por RBAC e ACL, porém alguns serviços estão inclusos na Azure Policy para controle como:

- **Microsoft.Kubernetes.Data** - Used for managing Kubernetes clusters and components such as pods, containers, and ingresses.
- **Microsoft.KeyVault.Data** - Used for managing vaults and certificates in Azure Key Vault.
- **Microsoft.Network.Data** - Used for managing Microsoft Azure Virtual Network Manager custom membership policies by using Azure Policy.
- **Microsoft.ManagedHSM.Data** - Used for managing Azure Key Vault Managed HSM keys by using Azure Policy.
- **Microsoft.DataFactory.Data** - Used for using Azure Policy to deny Microsoft Azure Data Factory outbound traffic domain names.
- **Microsoft.MachineLearningServices.v2.Data** - Used for managing Microsoft Azure Machine Learning model deployments. This Resource Provider mode reports compliance for newly created and updated components.

&nbsp;

modos de operação

![372823abd207f170806636ccf0ea99db.png](../_resources/372823abd207f170806636ccf0ea99db.png)

&nbsp;

&nbsp;

&nbsp;

![3a1943add3081d7fa695a7cd5a6f3c17.png](../_resources/3a1943add3081d7fa695a7cd5a6f3c17.png)

&nbsp;

da pra fazer por json

&nbsp;

![62534d7a8633234c54d4741cc9bf1729.png](../_resources/62534d7a8633234c54d4741cc9bf1729.png)