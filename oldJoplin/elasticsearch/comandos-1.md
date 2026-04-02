comandos

https://stackoverflow.com/questions/29417830/elasticsearch-find-disk-space-usage

https://stackoverflow.com/questions/33430055/removing-old-indices-in-elasticsearch

curl -XGET "http://192.168.0.17:9200/_cat/shards?v" -u elastic:passwd

mostra as shards que existem na database

curl -XGET 'http://localhost:9200/_cat/allocation?v'

mostra somente as estatisticas

https://stackoverflow.com/questions/21011916/how-to-delete-a-specific-shard-of-an-elasticsearch-index

mostra todos os indices:
curl -XGET "http://192.168.0.17:9200/_cat/indices?v"

DELETA OS INDICES:
 curl -XDELETE "http://192.168.0.17:9200/nome-indice"
 
 para mais referencias:
 https://www.bmc.com/blogs/elasticsearch-commands/
 https://www.ibm.com/support/pages/using-restful-api-clean-all-indices-and-shards-elasticsearch