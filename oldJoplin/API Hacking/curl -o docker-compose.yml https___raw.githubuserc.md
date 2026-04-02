curl -o docker-compose.yml https://raw.githubusercontent.com/OWASP/crAPI/main/deploy/docker/docker-compose.yml

docker-compose pull

docker-compose -f docker-compose.yml --compatibility up -d