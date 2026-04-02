decoder

adicionar os seguintes campos no decoder do 0510-sophos:
<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>signature_msg="(\.*)"\s+|signature_msg="(\.*)"$|signature_msg=(\.*)\s+|signature_msg=(\.*)$</regex>
  <order>signature</order>
</decoder>
<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>classification="(\.*)"\s+|classification="(\.*)"$|classification=(\.*)\s+|classification=(\.*)$</regex>
  <order>classification</order>
</decoder>


assim o IDP no log do IPS funciona:

2023-03-17T14:37:27.337928+00:00 fw.aim7.local device="SFW" date=2023-03-17 time=11:37:27 timezone="-03" device_name="SG125w" device_id=S1601E12D739F8F log_id=020804407002 log_type="IDP" log_component="Signatures" log_subtype="Drop" priority=Warning idp_policy_id=17 fw_rule_id=112 fw_rule_name="DNAT to SRV_RADIUS_1677530597696" fw_rule_section="Local rule" user_name="" signature_id=2305362 signature_msg="SCAN NMAP Script Scanner" classification="Unknown" rule_priority=3 src_ip=201.95.16.161 src_country_code=BRA dst_ip=10.7.14.104 dst_country_code=R1 protocol="TCP" src_port=40434 dst_port=80 platform="BSD,Linux,Mac,Other,Solaris,Unix,Windows" category="scan" target="Server"


