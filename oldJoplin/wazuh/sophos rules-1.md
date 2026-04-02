sophos rules

  <rule id="70031" level="12" ignore="30">
    <if_sid frequency="5000" timeframe="120" same_srcip="1">70021</if_sid>
    <field name="log_component">DoS Attack</field>
    <description>Traffic Dropped DoS: from "$(src_ip)" to "$(dst_ip)"</description>
  </rule>

  <rule id="70032" level="12">
    <if_sid>70020</if_sid>
    <field name="log_type">IDP</field>
    <description>Attack "$(signature)", coming from "$(src_ip)" classified as "$(classification)"</description>
  </rule>
  
  <rule id="70033" level="0">
    <if_sid>70020</if_sid>
    <field name="log_type">Sandbox</field>
    <description>Sophos Zero-day</description>
  </rule>
  
  <rule id="70034" level="12">
    <if_sid>70032</if_sid>
    <field name="log_subtype">Denied</field>
    <description>Sophos Zero-day scanned the file: "$(file_name)" from IP "$(src_ip)" "$(log_subtype)"</description>
  </rule>
</group>
