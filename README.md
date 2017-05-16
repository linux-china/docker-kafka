Docker Kafka
===============
Docker image for Kafka

### How to build

    $ docker build -t spotify/kafka:0.10.2.1 .

### How to run container
```
    $ docker run -p 2181:2181 -p 9092:9092  spotify/kafka:0.10.2.1
```

### How to use with docker-compose
Please add following code in docker-compose.yml

```
version: '2'
services:
   kafka:
     image: spotify/kafka:0.10.2.1
     ports:
       - "2181:2181"
       - "9092:9092"
     environment:
        ADVERTISED_HOST: 127.0.0.1
   kafka-manager:
     image: sheepkiller/kafka-manager
     ports:
       - "9000:9000"
     links:
        - kafka
     environment:
       APPLICATION_SECRET: 123456
       ZK_HOSTS: kafka:2181
```

### Execute kafka script in container

```
    $ docker exec -ti kafka_container_id /opt/kafka_2.11-0.10.2.0/bin/kafka-topics.sh --create --zookeeper 127.0.0.1:2181 --replication-factor 1 --partitions 1 --topic testTopic
    $ docker exec -ti kafka_container_id /opt/kafka_2.11-0.10.2.0/bin/kafka-topics --list --zookeeper 127.0.0.1:2181
```