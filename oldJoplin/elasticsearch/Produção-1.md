Produção

Artigos sobre isso:

https://medium.com/@abhidrona/elasticsearch-deployment-best-practices-d6c1323b25d7

https://www.elastic.co/pt/blog/hot-warm-architecture-in-elasticsearch-5-x

https://www.elastic.co/guide/en/cloud/current/ec-planning.html#ec-ha

https://www.elastic.co/guide/en/cloud/current/ec-configure.html

https://medium.com/@mzhaase/in-depth-guide-to-running-elasticsearch-in-production-b2ea7c8fa082
TIPOS DE NODES:
Master eligible node
o cara que vai controlar o cluster

Data node
quem possui os dados, procura e agrega operações relacionadas à CRUD (create, read, update e delete)

Injest node
vai transformar os dados, injest pipeline, logstash vai entrar aqui.

remote-eligible node
bom para casos remotos, é ativado por default

machine learning
não precisaremos

“Hot-Warm” Architecture:
Hot node
é o cara que vai ficar constantemente recebendo dados e indexando eles, requerem bastante CPU e I/O por isso somente com SSDs é recomendado ter 3 hot nodes para melhor disponibilidade, e ser a prova de failovers.

Warm node
faz read-only de dados que ja não são tão utilizados, requer 3 nodes e podem ser usados com HDDs

outra estratégia a se seguir seria colocar os dados menos utilizados em S3: https://www.elastic.co/guide/en/elasticsearch/plugins/2.2/cloud-aws-repository.html

transform node
faz transformações nos dados, acho que n será necessario aqui.

Requerimentos:

Quantidade de nodes master:
N/2+1 sendo que N = numero de maquinas elegíveis para master node.

Tentativa e erro

caso vc atribua 8 Gb de memoria pra maquina, é preciso dar 50% pro elastic heap e deixar 50% livre. A Lucene usa bastante memoria para coisas críticas e sem ela o elastic n funfa.

Por algum motivo de JVM não aloque mais que 32 Gb para um node.

Discos
SSD para termos querys mais rápidas, será interessante termos um HD para alocarmos shards frias.

CPU
não é tão utilizado assim, mas é bom ter multithreading 

Kibana
se vc utiliza bastante o kibana será necessario ter um "coordinator node"

arquitetura:
![1bd1d288f3c63261ddd153707a93ad7e.png](../_resources/1bd1d288f3c63261ddd153707a93ad7e-1.png)

![104fcdb192371a7e41f03e57e6ba7ec8.png](../_resources/104fcdb192371a7e41f03e57e6ba7ec8-1.png)

![c50c55305cc63cafb4b550dcd7985dff.png](../_resources/c50c55305cc63cafb4b550dcd7985dff-1.png)

![457a06fcd3f88360568f691b93b73b85.png](../_resources/457a06fcd3f88360568f691b93b73b85-1.png)

![8da80b44b7d0a8ba3211f64903b1d166.png](../_resources/8da80b44b7d0a8ba3211f64903b1d166-1.png)

![4b6e2e291e9d53cbe977525494b79e41.png](../_resources/4b6e2e291e9d53cbe977525494b79e41-1.png)

![d63312193c93794e80644385c91a5a46.png](../_resources/d63312193c93794e80644385c91a5a46-1.png)

![1ed210dc1a8e7a7c5b2136ac02249d1b.png](../_resources/1ed210dc1a8e7a7c5b2136ac02249d1b-1.png)

![4e9bf79dc82647d830814b04af80958f.png](../_resources/4e9bf79dc82647d830814b04af80958f-1.png)

![6ba8130748bf47d255ba791312fb1b62.png](../_resources/6ba8130748bf47d255ba791312fb1b62-1.png)

![6d24ea7da4e67b6dc9977760393c0418.png](../_resources/6d24ea7da4e67b6dc9977760393c0418-1.png)

![9d5b7dd9ea8efa28f35e267351e50cea.png](../_resources/9d5b7dd9ea8efa28f35e267351e50cea-1.png)

