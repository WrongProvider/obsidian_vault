esse

<!-- Modify it at your will. 

2023-03-23T20:06:52.000Z sup-08.aim7.local KES|11.0.0.0 - GNRL_EV_OBJECT_DELETED [event@23668 p1="275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F" p2="C:\\Users\\matheus.oliveira\\eicar.com" p5="EICAR-Test-File" p7="AIM7\\matheus.oliveira" p8="60" p9="{\"engine\":1,\"method\":0,\"blacklist\":false,\"cloud_sb\":false,\"md5\":\"44D88612FEA8A8F36DE82E1278ABB02F\"}" et="GNRL_EV_OBJECT_DELETED" tdn="File Threat Protection" etdn="Object deleted" hdn="SUP-08 - JESUS" hip="10.81.234.3" gn="BITLOCKER - SEM CRIPTO" kscfqdn="zangado"] Result description: Deleted\r\nType: Virus\r\nName: EICAR-Test-File\r\nUser: AIM7\matheus.oliveira (Initiator)\r\nObject: C:\Users\matheus.oliveira\eicar.com\r\nSHA256: 275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F\r\nMD5: 44D88612FEA8A8F36DE82E1278ABB02F

2023-03-24T17:06:20.000Z sup-08.aim7.local KES|11.0.0.0 - GNRL_EV_VIRUS_FOUND [event@23668 p1="275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F" p2="C:\\Users\\matheus.oliveira\\eicar.com" p5="EICAR-Test-File" p7="AIM7\\matheus.oliveira" p8="60" p9="{\"engine\":1,\"method\":3,\"blacklist\":false,\"cloud_sb\":false,\"md5\":\"44D88612FEA8A8F36DE82E1278ABB02F\"}" et="GNRL_EV_VIRUS_FOUND" tdn="File Threat Protection" etdn="Malicious object detected" hdn="SUP-08 - JESUS" hip="10.81.234.4" gn="BITLOCKER - SEM CRIPTO" engine="1" method="3" kscfqdn="zangado"] Result description: Detected\r\nType: Virus\r\nName: EICAR-Test-File\r\nUser: AIM7\matheus.oliveira (Initiator)\r\nObject: C:\Users\matheus.oliveira\eicar.com\r\nReason: Expert analysis\r\nDatabase release date: 3/24/2023 10:22:00 AM\r\nSHA256: 275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F\r\nMD5: 44D88612FEA8A8F36DE82E1278ABB02F
-->
<!--
decoder chatgpt
^(\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3}Z) (\S+) (\S+) \[(.*?)\] Result description: (.*)\\r\\nType: (.*)\\r\\nName: (.*)\\r\\nUser: (.*)\\r\\nObject: (.*)\\r\\nSHA256: (.*)\\r\\nMD5: (.*)$

decoder chatgpt2 focado nos p1,p2,etc
p1="([^"]+)"\s+p2="([^"]+)"(?:\s+p9="{[^}]*\"md5\":\"([^"]+)\"}")?

decoder3
et="([^"]+)"\s+tdn="([^"]+)"\s+etdn="([^"]+)"\s+hdn="([^"]+)"\s+hip="([^"]+)"\s+gn="([^"]+)"

decoder 4
^(\S+)\s+(\S+)\s+(\S+)\s+KES\|(\S+)\s+-\s+GNRL_EV_VIRUS_FOUND\s+\[event@\S+\s+p1="(\S+)"\s+p2="([^"]+)"\s+p5="([^"]+)"\s+p7="([^"]+)"\s+p8="(\d+)"\s+p9="{[^"]*}"\s+et="GNRL_EV_VIRUS_FOUND"\s+tdn="File Threat Protection"\s+etdn="Malicious object detected"\s+hdn="([^"]+)"\s+hip="([\d.]+)"\s+gn="([^"]+)"\s+engine="(\d+)"\s+method="(\d+)"\s+kscfqdn="([^"]+)"\]\s+Result description:\s+Detected.*MD5:\s+(\S+)
-->

<!--
decoder 5
^(?<timestamp>[^ ]+) (?<hostname>[^ ]+) (?<kes>KES\|[\d\.]+) - GNRL_EV_VIRUS_FOUND \[event@\d+ p1="(?<sha256>[^"]+)" p2="(?<object>[^"]+)" p5="(?<name>[^"]+)" p7="(?<user>[^"]+)" p8="(?<process_id>\d+)" p9="(?<metadata>[^"]+)" et="GNRL_EV_VIRUS_FOUND" tdn="(?<tdn>[^"]+)" etdn="(?<etdn>[^"]+)" hdn="(?<hdn>[^"]+)" hip="(?<hip>[\d\.]+)" gn="(?<gn>[^"]+)" engine="(?<engine>\d+)" method="(?<method>\d+)" kscfqdn="(?<kscfqdn>[^"]+)".*Database release date: (?<database_release_date>[^\\]+)\\r\\nSHA256: (?<sha256>[^\\]+)\\r\\nMD5: (?<md5>[^\\]+)\\r$

decoder 6
^\S+\s+\S+\s+(\S+)\s+KES\|\S+\s+-\s+GNRL_EV_VIRUS_FOUND\s+\[event@\d+\s+p1="(\w+)"\s+p2="([^"]+)"\s+p5="([^"]+)"\s+p7="([^"]+)"\s+p8="\d+"\s+p9="([^"]+)"\s+et="GNRL_EV_VIRUS_FOUND"\s+tdn="File Threat Protection"\s+etdn="Malicious object detected"\s+hdn="[^"]+"\s+hip="([^"]+)"\s+gn="[^"]+"\s+engine="(\d)"\s+method="(\d)"\s+kscfqdn="[^"]+"\]\s+Result description:\s+Detected\\r\\nType:\s+Virus\\r\\nName:\s+([^\\]+)\\r\\nUser:\s+([^\\]+)\\r\\nObject:\s+([^\\]+)\\r\\nReason:\s+Expert analysis\\r\\nDatabase release date:\s+[\d/]+\s+([^\\]+)\\r\\nSHA256:\s+([^\\]+)\\r\\nMD5:\s+(\w+)

-->


<decoder name="kaspersky-ksc">
  <prematch>^(\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3}Z)\s+(\S+)\s+KES\|\S+\s+-\s+GNRL_EV_VIRUS_FOUND</prematch>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3}Z\s+(\S+)\s+KES\|\S+\s+-\s+GNRL_EV_VIRUS_FOUND</regex>
  <order>timestamp,host,kesversion</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>p1="(\w+)"</regex>
  <order>p1</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\\r\\nName:\s+\w+\\r\\n</regex>
  <order>Name</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\\r\\nUser:\s+\.+\\r\\n</regex>
  <order>User</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\\r\\nObject:\s+\.+\\r\\n</regex>
  <order>Object</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\\r\\nSHA256:\s+\.+\\r\\n</regex>
  <order>SHA256</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc</parent>
  <regex>\\r\\nMD5:\s+\.+\\r\\n</regex>
  <order>MD5</order>
</decoder>
