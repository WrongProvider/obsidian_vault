kasper new

<!-- 
Kasperky syslog pattern: FROM_KSC_HOST: '10.11.161.5', KES_VERSION: 'KES|11.0.0.0', TIMESTAMP: '2023-04-10T14:32:59.000Z', INFECTED_HOST: 'sup-08.aim7.local', STRUCTURED-DATA: '[event@23668 p1="275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F" p2="C:\\Users\\matheus.oliveira\\eicar.com" p5="EICAR-Test-File" p7="AIM7\\matheus.oliveira" p8="60" p9="{\"engine\":1,\"method\":3,\"blacklist\":false,\"cloud_sb\":false,\"md5\":\"44D88612FEA8A8F36DE82E1278ABB02F\"}" et="GNRL_EV_VIRUS_FOUND" tdn="File Threat Protection" etdn="Malicious object detected" hdn="SUP-08 - JESUS" hip="10.81.234.4" gn="SUPORTE" engine="1" method="3" kscfqdn="zangado"] Result description: Detected\r\nType: Virus\r\nName: EICAR-Test-File\r\nUser: AIM7\matheus.oliveira (Initiator)\r\nObject: C:\Users\matheus.oliveira\eicar.com\r\nReason: Expert analysis\r\nDatabase release date: 4/10/2023 6:33:00 AM\r\nSHA256: 275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F\r\nMD5: 44D88612FEA8A8F36DE82E1278ABB02F
-->
<decoder name="kaspersky-ksc">
  <prematch>^Kasperky syslog pattern: FROM_KSC_HOST: '\S+', KES_VERSION:</prematch>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>  
  <regex>KES_VERSION:\s'KES\|(\d+.\d.\d.\d)',\sTIMESTAMP:\s'(\d+-\d+-\d+)T(\d+:\d+:\d+).(\d+Z)',\sINFECTED_HOST:\s'(\S+)'</regex>
  <order>kes_version, date, time, milisec, infected_host</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>  
  <regex>p1="([A-Z0-9]+)"|^p1="([A-Z0-9]+)"$|p1="(\S+)"</regex>
  <order>sha256_sig</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>p2="(\S+)"|p5="(\S+)"\s+|p5="(\S+)"$</regex>
  <order>file_path</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>p5="(\S+)"|p5="(\S+)"\s+|p5="(\S+)"$</regex>
  <order>infected_file</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>p7="(\S+\\\\\S+)"|p7="(\S+\\\\\S+)"\s+|p7="(\S+\\\\\S+)"$</regex>
  <order>initiator_user</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>etdn="(\w+\s+)"|etdn="(\w+\s+)"\s+|etdn="(\w+\s+)"$</regex>
  <order>file_path</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>hip="(\d+.\d+.\d+.\d+)"\s+</regex>
  <order>infected_ip</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\\r\\nType:\s(\w+)|Type:\s(\w+)\\r\\n|Type:\s(\w+)$</regex>
  <order>malware_type</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>Database release date:\s(\w+/\w+/\w+\s\d+:\d+:\d+)\s+</regex>
  <order>database_date</order>
</decoder>