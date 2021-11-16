



## Quickstart guide to Confluent Kafka for Personicle


### Introduction

Currently, we are working on integrating Kafka and timescaledb with Confluent Platform for scalable datastream utilizing JDBC sink.

### Useful documentations

#### Docker
To install the docker containers needed for the project, run following command inside this folder:
```
docker-compose up -d
```

To make sure all containers are up and running, run command:
```
docker-compose ps
```

If containers are not up, run the first command again to make sure all is up and running.

To bring down all the containers, run:
```
docker-compose down -v
```


#### Kafka

To try reading Kafka stream or producing Kafka stream manually (for testing or demo purpose), we can use the kafka console consumer and producer tool.

To use the kafka producer tool, first SSH into the broker docker container:
```
docker exec -it broker /bin/sh
```

Then, run the producer on a random topic name:
```
/bin/kafka-console-producer --topic test_topic --bootstrap-server localhost:9092
```

Feel free to type something into the prompts to send messages to the topic.

In order to read the topic, open a new terminal/bash console, SSH into the broker container again, then run:
```
/bin/kafka-console-consumer --topic test_topic --from-beginning --bootstrap-server localhost:9092
```

The messages sent from the producer should show up here after pressing enter to send it.



#### TimescaleDB

TimescaleDB should be created with username postgres and password specified in the docker-compose.yml file. To log in to timescaleDB database, first SSH  into the timescaleDB container:
```
docker exec -it timescaledb /bin/sh
```

Then, run psql (no need to specify password unless connecting remotely):
```
psql -U postgresql
```
