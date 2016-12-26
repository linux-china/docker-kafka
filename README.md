Docker Kafka
===============
Docker image for Kafka

### How to build

    docker build -t spotify/kafka:0.9.0.1 .

### How to use
Please add following code in docker-compose.yml

```
version: '2'
services:
  kafka:
    image: spotify/kafka:0.9.0.1
    ports:
      - "2181:2181"
      - "9092:9092"
```
