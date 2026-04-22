find . -type f -name "*.py" -exec sed -i 's/from backend\./from /g' {} +

# crontab -e
0 3 * * * cd /opt/quemVota/deploy && docker compose --profile ingest run --rm ingest >> /var/log/quemvota-ingest.log 2>&1