# PostgreSQL
1. docker image, add 
    discountdb:
        image: postgres
    into docker.compose.yml
2. add under volumes:
    postgres_data:
2. add discountdb under services in docker-compose.override.yml