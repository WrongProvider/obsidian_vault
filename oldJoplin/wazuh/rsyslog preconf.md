rsyslog preconf

$EscapeControlCharactersOnReceive on

template(name="kasper" type="list") {
    constant(value="Kasperky syslog pattern: FROM_KSC_HOST: '")
    property(name="fromhost")
    constant(value="', KES_VERSION: '")
    property(name="app-name")
    constant(value="', TIMESTAMP: '")
    property(name="timestamp" dateFormat="rfc3339")
    constant(value="', INFECTED_HOST: '")
    property(name="hostname")
#property(name="syslogtag")
    constant(value="', STRUCTURED-DATA: '")
    property(name="structured-data")
    property(name="msg" spifno1stsp="on" )
    property(name="msg" droplastlf="on" )
#replace(0,"\r\n"," ")
    constant(value="\n")
    }
template(name="kasper_devicecontrol" type="list") {
    constant(value="Kaspersky devicecontrol: FROM_KSC_HOST: '")
    property(name="fromhost")
    constant(value="', KES_VERSION: '")
    property(name="app-name")
    constant(value="', TIMESTAMP: '")
    property(name="timestamp" dateFormat="rfc3339")
    constant(value="', INFECTED_HOST: '")
    property(name="hostname")
    constant(value="', STRUCTURED-DATA: '")
    property(name="structured-data")
    property(name="msg" spifno1stsp="on" )
    property(name="msg" droplastlf="on" )
    constant(value="\n")
    }
template(name="kasper_audit" type="list") {
    constant(value="Kaspersky syslog audit: FROM_KSC_HOST: '")
    property(name="fromhost")
    constant(value="', KES_VERSION: '")
    property(name="app-name")
    constant(value="', TIMESTAMP: '")
    property(name="timestamp" dateFormat="rfc3339")
    constant(value="', INFECTED_HOST: '")
    property(name="hostname")
    constant(value="', STRUCTURED-DATA: '")
    property(name="structured-data")
    property(name="msg" spifno1stsp="on" )
    property(name="msg" droplastlf="on" )
    constant(value="\n")
    }

template(name="kasper_webcontrol" type="list") {
    constant(value="Kaspersky webcontrol: FROM_KSC_HOST: '")
    property(name="fromhost")
    constant(value="', KES_VERSION: '")
    property(name="app-name")
    constant(value="', TIMESTAMP: '")
    property(name="timestamp" dateFormat="rfc3339")
    constant(value="', INFECTED_HOST: '")
    property(name="hostname")
    constant(value="', STRUCTURED-DATA: '")
    property(name="structured-data")
    property(name="msg" spifno1stsp="on" )
    property(name="msg" droplastlf="on" )
    constant(value="\n")
    }
template(name="kasper_antivirus" type="list") {
    constant(value="Kaspersky syslog antivirus: FROM_KSC_HOST: '")
    property(name="fromhost")
    constant(value="', KES_VERSION: '")
    property(name="app-name")
    constant(value="', TIMESTAMP: '")
    property(name="timestamp" dateFormat="rfc3339")
    constant(value="', INFECTED_HOST: '")
    property(name="hostname")
	property(name="syslogtag")
    constant(value="', STRUCTURED-DATA: '")
    property(name="structured-data")
    property(name="msg" spifno1stsp="on" )
    property(name="msg" droplastlf="on" )
    replace(0,"\r\n"," ")
    constant(value="\n")
    }

template(name="kasper_network" type="list") {
    constant(value="Kaspersky network threat: FROM_KSC_HOST: '")
    property(name="fromhost")
    constant(value="', KES_VERSION: '")
    property(name="app-name")
    constant(value="', TIMESTAMP: '")
    property(name="timestamp" dateFormat="rfc3339")
    constant(value="', INFECTED_HOST: '")
    property(name="hostname")
    constant(value="', STRUCTURED-DATA: '")
    property(name="structured-data")
    property(name="msg" spifno1stsp="on" )
    property(name="msg" droplastlf="on" )
    constant(value="\n")
    }

	

else if ($fromhost-ip == '10.11.161.5') then {
  if $structured-data contains "GNRL_EV" then{
    action(type="omfile" file="/var/log/siem/aim7/kasper.log" template="kasper")
  }
  else{
    action(type="omfile" file="/var/log/siem/aim7/teste.log")
  }
}



 if  ($structured-data contains "et=\"GNRL_EV_VIRUS" or $structured-data contains "et=\"GNRL_EV_OBJECT" or $structured-data contains "et=\"GNRL_EV_PASSWD" or $structured-data contains "et=\"GNRL_EV_SUSPICIOUS") then {
    action(type="omfile" file="/var/log/siem/aim7/kasper.log" template="kasper_antivirus")
  }

  else if  ($structured-data contains "et=\"GNRL_EV_WEB" or $structured-data contains "et\"GNRL_EV_WC") then {
    action(type="omfile" file="/var/log/siem/aim7/kasper.log" template="kasper_webcontrol")
  }
  else if  ($structured-data contains "et=\"GNRL_EV_DEVCTRL" or $structured-data contains "et=\"GNRL_EV_DC" or "et=\"GNRL_EV_USB") then {
    action(type="omfile" file="/var/log/siem/aim7/kasper.log" template="kasper_devicecontrol")
  }
  else if ($structured-data contains "et=\"GNRL_EV_ATTACK_DETECTED" or $structured-data contains "et=\"00000329") then {
    action(type="omfile" file="/var/log/siem/aim7/kasper.log" template="kasper_network")
  }
  else if ($structured-data contains "000007e7" or  $structured-data contains "KLSRV_UPD_BASES_UPDATED" or $structured-data contains "00000039" or $structured-data contains "GNRL_EV_LICENSE_EXPIRATION" or $structured-data contains "000000ce" or $structured-data contains "000000e7" or $structured-data contains "000000f0") then {
    action(type="omfile" file="/var/log/siem/aim7/kasper.log" template="kasper_audit")
  }
  else{
    action(type="omfile" file="/var/log/siem/aim7/teste.log" template="kasper")
  }
