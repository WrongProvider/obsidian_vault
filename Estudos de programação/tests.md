

# sobe um postgres local igual ao do CI
docker run -d \
  --name quemvota-test \
  -e POSTGRES_USER=quemvota \
  -e POSTGRES_PASSWORD=quemvota \
  -e POSTGRES_DB=quemvota_test \
  -p 5432:5432 \
  postgres:16

# roda as migrations
DATABASE_URL=postgresql://quemvota:quemvota@localhost/quemvota_test \
  uv run alembic upgrade head

# roda os testes
DATABASE_URL=postgresql+asyncpg://quemvota:quemvota@localhost/quemvota_test \
VALKEY_URL=redis://localhost:6379 \
  uv run pytest -s