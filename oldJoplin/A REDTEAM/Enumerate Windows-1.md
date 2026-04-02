Enumerate

&nbsp;enumeracao de aplicativos

```shell-session
wmic product get name,version,vendor
```

&nbsp;

enumeracao de diretorios e strings  e arquivos

```shell-session
Get-ChildItem -Hidden -Path C:\Users\kkidd\Desktop\
```

printing sharing  
https://tryhackme.com/r/room/printerhacking101

&nbsp;

listagem de serviços:

```shell-session
net start
```

usar o Wmic para saber mais do processo.

```shell-session
wmic service where "name like 'THM Demo'" get Name,PathName
```

pega informacoes tipo PID etc

```shell-session
Get-Process -Name thm-demo
```

sabendo o PID da pra verificar no netstat para saber portas

```shell-session
netstat -noa |findstr "LISTENING" |findstr "3212"
```

verifica updates instalados no windows:

```shell-session
wmic qfe get Caption,Description
```

verifica serviços startados

```shell-session
net start
```

whoami

whoami /priv

whoami /groups

net user

net group

net localgroup

net localgroup &lt;administrators&gt;

net accounts

arp -a

```shell-session
net share
```