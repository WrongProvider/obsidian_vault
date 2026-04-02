DNS Zone Transfer

nslookup

server &lt;DNS Server Name OR ip address of DNS server&gt;

set type=any

ls -d &lt;DNS Zone Name&gt; > dnstest.txt

exit

&nbsp;

`dig -t AXFR DOMAIN_NAME @DNS_SERVER`