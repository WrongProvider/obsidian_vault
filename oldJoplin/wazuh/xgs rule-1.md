xgs rule

<group name="sophos_xgs_aim7,">
    <rule id="666778" level="12" ignore="1">`
        <if_sid frequency="10000" timeframe="30">70021</if_sid>
        <field name="log_component">DoS Attack</field>
        <description>Traffic Dropped DoS: from $(src_ip) to $(dst_ip)</description>
    </rule>
</group>