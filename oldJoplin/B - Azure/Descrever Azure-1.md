Descrever Azure

Azure Accounts

![000d050da2308746efb612e60641531f.png](../_resources/000d050da2308746efb612e60641531f-1.png)

Zonas

![ae183003fb838fcd3d59435094019d69.png](../_resources/ae183003fb838fcd3d59435094019d69-1.png)

para garantir resiliencia, usar 3 zonas diferentes

Availability zones:

    Zonal services: You pin the resource to a specific zone (for example, VMs, managed disks, IP addresses).
    Zone-redundant services: The platform replicates automatically across zones (for example, zone-redundant storage, SQL Database).
    Non-regional services: Services are always available from Azure geographies and are resilient to zone-wide outages as well as region-wide outages.

Region pairs

somente a 300m
![f83a92bd3ef301c831ac5f2c46faea3b.png](../_resources/f83a92bd3ef301c831ac5f2c46faea3b-1.png)

se uma região sofrer um desastre existe outro datacenter disponivel para tomar ação.

Data continues to reside within the same geography as its pair (except for Brazil South) for tax- and law-enforcement jurisdiction purposes.

Sovereign Regions

são regiões isoladas da azure, são mais usadas por governo.

Resource group

![1619d82fe2330586ab4ef86b5d273384.png](../_resources/1619d82fe2330586ab4ef86b5d273384-1.png)

Azure subscription
![865c69f384b6191aa1f00e0e6b18328c.png](../_resources/865c69f384b6191aa1f00e0e6b18328c-1.png)


Management group
RBAC
![769469a3b1c7c2913e578fe66c5e730b.png](../_resources/769469a3b1c7c2913e578fe66c5e730b-1.png)

10000 management groups
só pode ter 6 leveis de profundidade
cada grupo e subscrição só pode ter um parente
