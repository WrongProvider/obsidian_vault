Active Directory Enum

&nbsp;DN -> uma coleção de chaves e valores separados por virgula para identificar records unicos no diretorio. Consistindo em DC (domain componente), OU (organizational unit), CN (Common Name)

Get-ADUser -Filter \*

da pra especificar o Common-Name CN  ou a OU. Ex OU=THM

```shell-session
Get-ADUser -Filter * -SearchBase "CN=Users,DC=THMREDTEAM,DC=COM"
```

&nbsp;

checa programas de AV no sistema:

```shell-session
wmic /namespace:\\root\securitycenter2 path antivirusproduct
```

ou usando PS

```shell-session
Get-CimInstance -Namespace root/SecurityCenter2 -ClassName AntivirusProduct
```