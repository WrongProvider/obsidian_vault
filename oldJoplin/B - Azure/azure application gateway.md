azure application gateway

https://learn.microsoft.com/en-us/training/modules/load-balance-web-traffic-with-application-gateway/3-exercise-create-web-sites

&nbsp;

update subnet via cli

az network application-gateway stop -g Main-sucuri -n appgw-sucuri

az network application-gateway update -g Main-sucuri -n appgw-sucuri --set gatewayIpConfigurations\[0\].subnet.id=PUB-SUB

&nbsp;