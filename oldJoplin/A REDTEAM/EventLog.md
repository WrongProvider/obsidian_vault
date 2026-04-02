EventLog

&nbsp;

```shell-session
Get-EventLog -List
```

verifica se o Sysmon está presente: 

```shell-session
Get-Process | Where-Object { $_.ProcessName -eq "Sysmon" }
```

&nbsp;

```shell-session
Get-CimInstance win32_service -Filter "Description = 'System Monitor service'"
```

```shell-session
Get-Service | where-object {$_.DisplayName -like "*sysm*"}
```

&nbsp;

verificar no registro

```shell-session
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WINEVT\Channels\Microsoft-Windows-Sysmon/Operational
```

&nbsp;

dai verificamos se temos acesso a escrita das configurações 

```shell-session
findstr /si '<ProcessCreate onmatch="exclude">' C:\tools\*
```