Windows Defender

&nbsp;

o Windows tem o modo Active (proteção e remediação), Passivo (quando tem instalação de AV e fica como um secundario sem remediação), e Disable

checa se o serviço do windows está up

```shell-session
Get-Service WinDefend
```

```shell-session
Get-MpComputerStatus | select RealTimeProtectionEnabled
```

&nbsp;

verifica as ameaças do windows defender

<span style="color: #eb5757;">Get-MpThreat</span>