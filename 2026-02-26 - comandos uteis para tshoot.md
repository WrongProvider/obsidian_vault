**Docker — troubleshooting**

bash

```bash
# Status geral
docker compose ps

# Logs em tempo real
docker compose logs -f
docker compose logs -f api
docker compose logs -f nginx
docker compose logs -f frontend
docker compose logs -f postgres
docker compose logs -f valkey

# Consumo de recursos
docker stats

# Reiniciar um serviço
docker compose restart api

# Recriar sem cache
docker compose up -d --build --force-recreate

# Remover containers órfãos
docker compose up -d --remove-orphans
```

**Docker — updates**

bash

```bash
# Update normal após git pull
docker compose up -d --build api frontend

# Rebuild completo
docker compose down
docker compose up -d --build
```

**Banco de dados**

bash

```bash
# Dump local
pg_dump -U postgres -d seu_banco -F c --no-owner --no-acl -f backup.dump

# Enviar para VPS
scp -i sua-chave.pem backup.dump ubuntu@<ip>:/opt/quemVota/app/deploy/

# Importar na VPS
docker cp backup.dump quemvota_postgres:/tmp/
docker compose exec postgres pg_restore -U $POSTGRES_USER -d $POSTGRES_DB --no-owner -v /tmp/backup.dump

# Checar tabelas
docker compose exec postgres psql -U $POSTGRES_USER -d $POSTGRES_DB -c "\dt"

# horario
SELECT now();

#ultima modificação na tabela
SELECT MAX(created_at) FROM politico;

#transações em idle
SELECT pid, state, query
FROM pg_stat_activity
WHERE state = 'idle in transaction';
```

**Git — conflitos na VPS**

bash

```bash
# Descartar mudanças locais e atualizar
git checkout arquivo/em/conflito
git pull

# Se tiver stash pendente
git stash
git pull
git stash pop

# Nuclear — descarta tudo e sincroniza com remoto
git reset --hard HEAD
git pull

#tirar o arquivo local para nunca atualizar
sudo git update-index --assume-unchanged main.py
sudo git update-index --no-assume-unchanged path/to/folder/*

```

```
# valkey flush
sudo docker exec -it quemvota_valkey valkey-cli flushall
```

```
Postgres 

\pset pager off

UPDATE table_name
SET column1 = NULL,
    column2 = NULL,
    column3 = NULL,

ALTER DATABASE old_dbname RENAME TO new_dbname;

SELECT pg_terminate_backend(pid)
FROM pg_stat_activity
WHERE datname = 'TARGET_DB_NAME' -- The database to clear connections from
AND pid <> pg_backend_pid();    -- Excludes your current connection


postgres=# \c quemvota 
GRANT CONNECT ON DATABASE quemvota TO caneta_azul;
GRANT USAGE ON SCHEMA public TO caneta_azul;

GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO caneta_azul;
GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO caneta_azul;

ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL PRIVILEGES ON TABLES TO caneta_azul;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL PRIVILEGES ON SEQUENCES TO caneta_azul;


https://pagespeed.web.dev/analysis/https-quemvota-com-br/dhqydstfxk?form_factor=mobile

https://realfavicongenerator.net/your-favicon-is-ready

https://search.google.com/test/rich-results/result?id=UvXXj_BmNbrxqeY2Wfikfw

```
