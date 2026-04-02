rule kasper

<group name="kasperky_rule_active,"><rule id="666001" level="2"><decoded_as>kaspersky-ksc</decoded_as> <description>Kaspersky Security Center Alert</description></rule>

```
<rule id="666002" level="12">
    <if_sid>666001</if_sid>
    <field name="event_alert">KSN servers unavailable</field>
    <description>KSN servers unavailable on host: "$(infected_ip)" triggered by user: "$(initiator_user)"</description>
</rule>

<rule id="666003" level="12">
    <if_sid>666001</if_sid>
    <field name="detection_type">GNRL_EV_WEB_URL_BLOCKED</field>
    <description>Firewall blocked on host "$(infected_ip)" triggered by user: "$(initiator_user)"</description>
</rule>

<rule id="666004" level="12">
    <if_sid>666001</if_sid>
    <field name="event_alert">Database update</field>
    <description>Database update on host: "$(infected_ip)" triggered by user: "$(initiator_user)"</description>
</rule>

<rule id="666005" level="12">
    <if_sid>666001</if_sid>
    <field name="event_alert">Malicious object detected</field>
    <description>Malware "$(malware_type)" found on host: "$(infected_ip)" triggered by user: "$(initiator_user)" on path: "$(file_path)"
    sha256 signature: "$(sha256_sig)"</description>
</rule>

<rule id="666006" level="12">
    <if_sid>666001</if_sid>
    <field name="detection_type">GNRL_EV_VIRUS_FOUND_BY_KSN</field>
    <description>(KSN) Malware "$(malware_type)" found on host: "$(infected_ip)" triggered by user: "$(initiator_user)" on path: "$(file_path)"
    sha256 signature: "$(sha256_sig)"</description>
</rule>

<rule id="666007" level="14">
    <if_sid>666001</if_sid>
    <field name="detection_type">Cannot be deleted</field>
    <description>Malware $(malware_type) can not be deleted on host: "$(infected_ip)" triggered by user: "$(initiator_user)" on path: "$(file_path)"
    sha256 signature: "$(sha256_sig)"</description>
</rule>

<rule id="666008" level="12">
    <if_sid>666001</if_sid>
    <field name="detection_type">GNRL_EV_WEB_URL_BLOCKED_KSN</field>
    <description>(KSN) Firewall blocked on host "$(infected_ip)" triggered by user: "$(initiator_user)"</description>
</rule> 
```</group> <group name="kasperky_rule_active,"><rule id="666001" level="0"><decoded_as>kaspersky-antivirus</decoded_as> <description>Kaspersky Security Center Alert</description></rule> &lt;rule id="666003" level="12"&gt; &lt;if\_sid&gt;666001&lt;/if\_sid&gt; &lt;field name="detection\_type"&gt;GNRL\_EV\_WEB\_URL\_BLOCKED&lt;/field&gt; &lt;description&gt;Firewall blocked on host "$(infected\_ip)" triggered by user: "$(initiator\_user)"&lt;/description&gt; &lt;/rule&gt; &lt;rule id="666004" level="12"&gt; &lt;if\_sid&gt;666001&lt;/if\_sid&gt; &lt;field name="event\_alert"&gt;Malicious object detected&lt;/field&gt; &lt;description&gt;Malware "$(malware\_type)" found on host: "$(infected\_ip)" triggered by user: "$(initiator\_user)" on path: "$(file\_path)" sha256 signature: "$(sha256\_sig)"&lt;/description&gt; &lt;/rule&gt; &lt;rule id="666005" level="12"&gt; &lt;if\_sid&gt;666001&lt;/if\_sid&gt; &lt;field name="detection\_type"&gt;GNRL\_EV\_VIRUS\_FOUND\_BY\_KSN&lt;/field&gt; &lt;description&gt;(KSN) Malware "$(malware\_type)" found on host: "$(infected\_ip)" triggered by user: "$(initiator\_user)" on path: "$(file\_path)" sha256 signature: "$(sha256\_sig)"&lt;/description&gt; &lt;/rule&gt; &lt;rule id="666006" level="14"&gt; &lt;if\_sid&gt;666001&lt;/if\_sid&gt; &lt;field name="detection\_type"&gt;Cannot be deleted&lt;/field&gt; &lt;description&gt;Malware $(malware\_type) can not be deleted on host: "$(infected\_ip)" triggered by user: "$(initiator\_user)" on path: "$(file\_path)" sha256 signature: "$(sha256\_sig)"&lt;/description&gt; &lt;/rule&gt; &lt;rule id="666007" level="14"&gt; &lt;if\_sid&gt;666001&lt;/if\_sid&gt; &lt;field name="detection\_type"&gt;Disinfection impossible&lt;/field&gt; &lt;description&gt;Malware $(malware\_type) can not be disinfected on host: "$(infected\_ip)" triggered by user: "$(initiator\_user)" on path: "$(file\_path)" sha256 signature: "$(sha256\_sig)"&lt;/description&gt; &lt;/rule&gt; &lt;rule id="666008" level="12"&gt; &lt;if\_sid&gt;666001&lt;/if\_sid&gt; &lt;field name="detection\_type"&gt;GNRL\_EV\_WEB\_URL\_BLOCKED\_KSN&lt;/field&gt; &lt;description&gt;(KSN) Firewall blocked on host "$(infected\_ip)" triggered by user: "$(initiator\_user)"&lt;/description&gt; &lt;/rule&gt;
</group>

```
name: 'kaspersky-teste-teste'  et: 'GNRL_EV_ATTACK_DETECTED'  etdn: 'Network attack detected'  hip: '10.7.14.13'  ksc_code: 'KES|11.0.0.0'  ksc_trigger: 'User: NT AUTHORITY\SYSTEM (System user)\r\nComponent: Network Threat Protection\r\nResult description: Blocked\r\nName: Bruteforce.Generic.Rdp.a\r\nObject: TCP from 10.7.14.110 at 10.7.14.13:3389\r\nObject type: Network packet\r\nObject name: TCP from 10.7.14.110 at 10.7.14.13:3389\r\nAdditional: 10.7.14.13\r\nDatabase release date: 8/1/2023 10:38:00 AM[event@23668 p1="Bruteforce.Generic.Rdp.a" p2="TCP" p3="168234606" p4="3389" p6="168234509" et="GNRL_EV_ATTACK_DETECTED" tdn="Network Threat Protection" etdn="Network attack detected" hdn="SUP-VM-12" hip="10.7.14.13" gn="Managed devices" kscfqdn="srv-vm-12.lab-antimalware.local'  p1: 'Bruteforce.Generic.Rdp.a'  p2: 'TCP'  p3: '168234606'  p4: '3389'  p6: '168234509'  tdn: 'Network Threat Protection'
```