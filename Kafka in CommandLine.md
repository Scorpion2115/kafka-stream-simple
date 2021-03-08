# Hello Kafka

## Topics
Open a new terminal window and then run this command to open a shell on the broker docker container
```shell
docker-compose exec broker bash
```
Next, create the topic that the producer can write to
```shell
kafka-topics --create --topic streams-input-topic --bootstrap-server broker:9092 --replication-factor 1 --partitions 1
```

Verify the previous action by list topic
```shell
kafka-topics --list --bootstrap-server broker:9092
```

Delete unwanted topics
```shell
kafka-topics --delete --topic you-know-who --bootstrap-server broker:9092
```

## Producer
Run a console producer to publish some data to the specific topics
```shell
# StreamsMain
kafka-console-producer --broker-list broker:9092 --topic streams-input-topic --property parse.key=true --property key.separator=:

# StatelessTransformationsMain
kafka-console-producer --broker-list broker:9092 --topic stateless-transformations-input-topic --property parse.key=true --property key.separator=:

```

## Consumer
Run a console consumer that will read topics from the output topic
```shell
# StreamsMain
kafka-console-consumer --bootstrap-server broker:9092 --topic streams-output-topic --property print.key=true --from-beginning

# StatelessTransformationsMain
kafka-console-consumer --bootstrap-server broker:9092 --topic stateless-transformations-output-topic --property print.key=true --from-beginning




```