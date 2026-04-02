capacity planning

https://bigdataboutique.com/services/elasticsearch/capacity-planning

https://www.elastic.co/pt/blog/benchmarking-and-sizing-your-elasticsearch-cluster-for-logs-and-metrics

https://www.elastic.co/pt/blog/rally-1-0-0-released-benchmark-elasticsearch-like-we-do

https://www.elastic.co/pt/webinars/elasticsearch-sizing-and-capacity-planning

meios de fazer o calculo:

por volume:

por throughput:

![ff29e03733c93418a0b44a2f9fb8af50.png](../_resources/ff29e03733c93418a0b44a2f9fb8af50.png)

![3ef16b2bbfe09bb7472954d6626a1a56.png](../_resources/3ef16b2bbfe09bb7472954d6626a1a56.png)

![ee5386293d00c580f7b2c0fb8b6ab08f.png](../_resources/ee5386293d00c580f7b2c0fb8b6ab08f.png)

![c600e9057618a4e714f652d1aa369ed0.png](../_resources/c600e9057618a4e714f652d1aa369ed0.png)

![592709968c230cf876cb7a3108b291cf.png](../_resources/592709968c230cf876cb7a3108b291cf.png)

master node (eligible) sempre no minimo 3
3 data nodes, pq vc sempre vai ter 1 replica, com um failover de 1, nunca vai ficar underreplicated

pro sophos:

ls -lah /log/logfilename.log veja o tamanho assim que der 9h e fazer uma subtração as 18h

The tiebreaker nodes are simply 1GB (by default) ES instances with data disabled and master-eligible enabled, added to a 3rd zone, It is intended for HA vs management-only nodes