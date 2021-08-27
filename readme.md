https://stackoverflow.com/questions/41330514/docker-rabbitmq-persistency
https://www.futurefundamentals.com/set-rabbitmq-with-data-persistent-with-docker-compose/

#run publisher
docker run -it --rm --net rabbitmq_rabbits -e RABBIT_HOST=rabbitmq_rabbit-1_1 -e RABBIT_PORT=5672 -e RABBIT_USERNAME=guest -e RABBIT_PASSWORD=guest -p 8080:8080 --name publisher-1 aimvector/rabbitmq-publisher:v1.0.0

#run rabbitmq
docker network create rabbits
docker run -v rabbitmq-data:/var/lib/rabbitmq/mnesia/ -d --rm --net rabbits --hostname rabbit-1 --name rabbit-1 -p 8088:15672 rabbitmq:3.8-management
docker run  -d --rm --net rabbits --hostname rabbit-1 --name rabbit-1 -p 8088:15672 rabbitmq:3.8-management
