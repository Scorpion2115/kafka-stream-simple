# Hello Kafka

## Topics
Open a new terminal window and then run this command to open a shell on the broker docker container
```shell
docker-compose exec broker bash
```
Next, create the topic that the producer can write to
```shell
kafka-topics --create --topic you-know-who --bootstrap-server broker:9092 --replication-factor 1 --partitions 1
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
kafka-console-producer --broker-list broker:9092 --topic you-know-who
```

## Consumer
Run a console consumer that will read topics from the output topic
```shell
kafka-console-consumer --bootstrap-server broker:9092 --topic you-know-who --property print.key=true --from-beginning
```