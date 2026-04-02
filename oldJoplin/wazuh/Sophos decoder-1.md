teste

<!--
  -  Sophos XG210 Firewall decoders
  -  Created by Wazuh, Inc.
  -  Copyright (C) 2015, Wazuh Inc.
  -  This program is a free software; you can redistribute it and/or modify it under the terms of GPLv2.
  copy
  0510-sophos_fw_decoders.xml
-->

<!--
device="SFW" date=2019-10-09 time=17:19:06 timezone="+08" device_name="XG210" device_id=AAAAAAAA1234567 log_id=010101010101 log_type="Firewall" log_component="Firewall Rule" log_subtype="Denied" status="Deny" priority=Information duration=0 fw_rule_id=14 policy_type=1 user_name="" user_gp="" iap=2 ips_policy_id=0 appfilter_policy_id=0 application="" application_risk=0 application_technology="" application_category="" in_interface="Port3" out_interface="Port2" src_mac=11:22:aa:bb:22:11 src_ip=11.22.33.44 src_country_code= dst_ip=44.33.22.11 dst_country_code= protocol="TCP" src_port=52667 dst_port=10051 sent_pkts=0  recv_pkts=0 sent_bytes=0 recv_bytes=0 tran_src_ip= tran_src_port=0 tran_dst_ip= tran_dst_port=0 srczonetype="" srczone="" dstzonetype="" dstzone="" dir_disp="" connid="" vconnid="" hb_health="No Heartbeat" message="" appresolvedby="Signature"th="No Heartbeat

device="SFW" date=2019-10-09 time=17:19:06 timezone="+08" device_name="XG210" device_id=AAAAAAAA1234567 log_id=010101010101 log_type="Firewall" log_component="Firewall Rule" log_subtype="Allowed" status="Allow" priority=Information duration=0 fw_rule_id=22 policy_type=1 user_name="" user_gp="" iap=0 ips_policy_id=9 appfilter_policy_id=0 application="DNS" application_risk=1 application_technology="Network Protocol" application_category="Infrastructure" in_interface="Port3" out_interface="Port2" src_mac=11:22:aa:bb:22:11 src_ip=11.22.33.44 src_country_code=R1 dst_ip=8.8.8.8 dst_country_code=USA protocol="UDP" src_port=60778 dst_port=53 sent_pkts=0  recv_pkts=0 sent_bytes=0 recv_bytes=0 tran_src_ip=11.22.33.44 tran_src_port=0 tran_dst_ip= tran_dst_port=0 srczonetype="DMZ" srczone="DMZ" dstzonetype="WAN" dstzone="WAN" dir_disp="" connevent="Start" connid="17709984" vconnid="" hb_health="No Heartbeat" message="" appresolvedby="Signature"

nova log:
May 22 20:12:58 200-195-229-23.brdigital.net.br device_name="SFW" timestamp="2023-05-22T17:16:19-0300" device_model="XG310" device_serial_id="C320ABJKRT43FB1" log_id="011902605151" log_type="Firewall" log_component="IP Spoof" log_subtype="Denied" log_version=1 severity="Information" fw_rule_id="N/A" nat_rule_id="0" fw_rule_type="NETWORK" ether_type="IPv6 (0x86DD)" src_ip="2804:7f3:5041:4726:fc74:db28:2490:b847" dst_ip="ff02::1" protocol="IPv6-ICMP" src_port=136 hb_status="No Heartbeat" app_resolved_by="Signature" app_is_cloud="FALSE" qualifier="New" log_occurrence="1"

2023-05-22T20:44:06.951328+00:00 fw.aim7.local device_name="SFW" timestamp="2023-05-22T17:44:06-0300" device_model="SG125w" device_serial_id="S1601E12D739F8F" log_id="010402403001" log_type="Firewall" log_component="DoS Attack" log_subtype="Denied" log_version=1 severity="Warning" fw_rule_id="N/A" nat_rule_id="0" fw_rule_type="NETWORK" ether_type="IPv4 (0x0800)" in_interface="eth4" src_mac="00:15:5d:0e:02:25" src_ip="10.7.14.103" src_country="R1" dst_ip="192.124.249.18" dst_country="USA" protocol="TCP" src_port=1025 dst_port=857 hb_status="No Heartbeat" app_resolved_by="Signature" app_is_cloud="FALSE" qualifier="New" in_display_interface="eth4" log_occurrence="1"

May 22 23:57:28 200-195-229-23.brdigital.net.br device_name="SFW" timestamp="2023-05-22T21:00:49-0300" device_model="XG310" device_serial_id="C320ABJKRT43FB1" log_id="011902605151" log_type="Firewall" log_component="IP Spoof" log_subtype="Denied" log_version=1 severity="Information" fw_rule_id="N/A" nat_rule_id="0" fw_rule_type="NETWORK" ether_type="IPv4 (0x0800)" src_ip="169.254.1.1" src_country="R1" dst_ip="64.233.162.100" dst_country="USA" protocol="TCP" src_port=44100 dst_port=443 hb_status="No Heartbeat" app_resolved_by="Signature" app_is_cloud="FALSE" qualifier="New" log_occurrence="1"


^(\w{3} \d{2} \d{2}:\d{2}:\d{2}) (\S+) (\S+) device_name="(\w+)" timestamp="([^"]+)" device_model="(\w+)" device_serial_id="([^"]+)" log_id="([^"]+)" log_type="([^"]+)" log_component="([^"]+)" log_subtype="([^"]+)" log_version=(\d+) severity="([^"]+)" fw_rule_id="([^"]+)" nat_rule_id="([^"]+)" fw_rule_type="([^"]+)" ether_type="([^"]+)" src_ip="([^"]+)" src_country="([^"]+)" dst_ip="([^"]+)" dst_country="([^"]+)" protocol="([^"]+)" src_port=(\d+) dst_port=(\d+) hb_status="([^"]+)" app_resolved_by="([^"]+)" app_is_cloud="([^"]+)" qualifier="([^"]+)" log_occurrence="(\d+)"$

device_name="\w*"\s+timestamp="\d+-\d+-\d+T\d+:\d+:\d+-\d+"\s+device_model="\s+\d+"
-->

<decoder name="sophos-fw">
  <!-- <prematch>^device="\w*"\s+date=\d+-\d+-\d+\s+time=</prematch> -->
  <!--<prematch>^\w{3} \d{2} \d{2}:\d{2}:\d{2} \S+ \S+ device_name="\w+\s"timestamp="\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}-\d*"</prematch> -->
  <prematch>device_name="SFW" timestamp="\d{4}-\d{2}-\d{2}T\d{2}:\d{2}:\d{2}-\d*" device_model="([0-9A-Z]+)"</prematch>
</decoder>

<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>device_name="SFW"\s+timestamp="(\.)"\s+device_model="([0-9A-Z]+)"</regex>
  <order>timestamp,model</order>
</decoder>

<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>log_component="(\.*)"</regex>
  <order>log_component</order>
</decoder>
<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>log_id="(\d+)"</regex>
  <order>log_id</order>
</decoder>
<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>log_subtype="(\w+)"</regex>
  <order>log_subtype</order>
</decoder>
<decoder name="sophos-fw">
  <parent>sophos-fw</parent>
  <regex>ether_type="(\w+\d) \(\d+\)"</regex>
  <order>ether_type</order>
</decoder>