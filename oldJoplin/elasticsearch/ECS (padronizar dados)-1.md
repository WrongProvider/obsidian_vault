o ECS vai ser usado para padronizar os dados:
https://www.elastic.co/guide/en/ecs/8.0/index.html

como o CEF ta padronizado no ECS:

cef.device\_custom\_string_1.value == nome do arquivo

cef.device\_custom\_string_10.value == tipo de proteção

cef.device\_custom\_string_9.value == nome da politica kaspersky

cef.name == nome da detecção

destination.user.name == nome do usuario ou dominio

https://github.com/elastic/ecs-mapper

https://www.elastic.co/guide/en/ecs/current/ecs-converting.html

https://www.elastic.co/guide/en/ecs/current/ecs-converting.html#ecs-map-custom-data-to-ecs-es-pipeline

https://docs.google.com/spreadsheets/d/1m5JiOTeZtUueW3VOVqS8bFYqNGEEyp0jAsgO12NFkNM/edit#gid=0

ECS a serem usados com o grok:

[hash.sha256](https://www.elastic.co/guide/en/ecs/current/ecs-hash.html#field-hash-sha256)