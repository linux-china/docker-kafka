Docker Kafka
===============
Docker image for Kafka

### How to build

    $ docker build -t spotify/kafka:0.9.0.1 .

### How to run container
```
    $ docker run -p 2181:2181 -p 9092:9092  spotify/kafka:0.9.0.1
```

### How to use with docker-compose
Please add following code in docker-compose.yml

```
version: '2'
services:
  kafka:
    image: spotify/kafka:0.9.0.1
    ports:
      - "2181:2181"
      - "9092:9092"
    environment:
      ADVERTISED_HOST: 127.0.0.1
```

### Execute kafka script in container

```
    $ docker exec -ti kafka_container_id /opt/kafka_2.11-0.9.0.1/bin/kafka-topics.sh --create --zookeeper 127.0.0.1:2181 --replication-factor 1 --partitions 1 --topic testTopic
    $ docker exec -ti kafka_container_id /opt/kafka_2.11-0.9.0.1/bin/kafka-topics --list --zookeeper 127.0.0.1:2181
```