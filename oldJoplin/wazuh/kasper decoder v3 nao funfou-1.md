kasper decoder v3 nao funfou

<decoder name="kaspersky-ksc-syslog">
  <prematch>^\w{3}\s+\d{1,2}\s+\d{2}:\d{2}:\d{2}\.\d+\s+\w+\s+\d+\.\d+\.\d+\.\d+\.\d+\s+>\s+\w+\.\w+\.\w+\.\w+:\s+SYSLOG\s+user\.critical|warning|notice|info|debug,\s+length:\s+\d+</prematch>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <prematch>^(*?)</prematch>
  <regex>\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}\.\d{3}Z\s\S+\sKES\|S+\s-\sGNRL_EV_VIRUS_FOUND|GNRL_EV_OBJECT_DELETED|GNRL_EV_OBJECT_NOTCURED</regex>
  <order>time,host,kesversion</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>p1="(\w+)"|p1="(\w+)"\s+|p1="(\w+)"$</regex>
  <order>sha265_infected</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>p2="(\.+)"|p2="(\.+)"\s+|p2="(\.+)"$</regex>
  <order>caminho</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>p5="(\.+)"|p5="(\.+)"\s+|p5="(\.+)"$</regex>
  <order>arquivo_infectado</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>p7="(\.+)"|p7="(\.+)"\s+|p7="(\.+)"$</regex>
  <order>usuario</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>tdn="(\.+)"|tdn="(\.+)"\s+|tdn="(\.+)"$</regex>
  <order>protecao</order>
</decoder>
<!-- ^(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?)\.(25[0-5]|2[0-4][0-9]|[01]?[0-9][0-9]?) -->
<!--
name: 'kaspersky-ksc'
	arquivo_infectado: 'EICAR-Test-File'
	caminho: 'C:\\Users\\matheus.oliveira\\eicar.com'
	regra: 'BITLOCKER - SEM CRIPTO'
	sha265_infected: '275A021BBFB6489E54D471899F7DB9D1663FC695EC2FE2A2C4538AABF651FD0F'
	usuario: 'AIM7\\matheus.oliveira'
-->

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>hip="(\.+)"|hip="(\.+)"\s+|hip="(\.+)"$</regex>
  <order>ip</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>gn="(\.+)"|gn="(\.+)"\s+|gn="(\.+)"$</regex>
  <order>regra</order>
</decoder>

<decoder name="kaspersky-ksc">
  <parent>kaspersky-ksc-syslog</parent>
  <regex>Type:\s(\w+)|Type:\s(\w+)\s+|Type:\s(\w+)$</regex>
  <order>tipo_malware</order>
</decoder>
