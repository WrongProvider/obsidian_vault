VM Backup

Business continuity disaster recovery (BCDR)

Azure Backup vs Azure Site Recovery
backup é stateful, site recovery copia os dados em tempo real, permitindo failover.

Quando der problema de rede, ou em energia da para usar as zonas de disponibilidade para sair de desastres. (site recover)

quando acontecer um incidente como ransomware ou data corruption (backup)

RPO -> recovery point objective
RTO -> recovery time objective

Primeiro se cria uma politica de DR e depois configura a replicação do ambiente, tudo aqui é passado por resource group, então a rede e as maquinas podem ser replicadas


tem um vm agent para snapshot





az backup vault create --resource-group vmbackups --location westus2 --name azure-backup

az backup protection enable-for-vm --resource-group vmbackups --vault-name azure-backup --vm NW-APP01 --policy-name EnhancedPolicy

az backup job list --resource-group vmbackups --vault-name azure-backup --output table

az backup protection backup-now --resource-group vmbackups --vault-name azure-backup --container-name NW-APP01 --item-name NW-APP01 --retain-until 18-10-2030 --backup-management-type AzureIaasVM

az backup job list --resource-group vmbackups --vault-name azure-backup --output table