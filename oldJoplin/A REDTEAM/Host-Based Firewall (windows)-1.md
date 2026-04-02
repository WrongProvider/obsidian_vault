Host-Based Firewall (windows)

checa como está o firewall do windows.

```shell-session
Get-NetFirewallProfile | Format-Table Name, Enabled
```

&nbsp;

caso tenha admin, da para configurar o firewall:

```shell-session
Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled False
```

&nbsp;

aprendendo as regras ja impostas no sistema 

```shell-session
Get-NetFirewallRule | select DisplayName, Enabled, Description
```

&nbsp;

teste de conexão

```shell-session
Test-NetConnection -ComputerName 127.0.0.1 -Port 80
```