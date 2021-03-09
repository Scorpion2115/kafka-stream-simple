# Kafka Streams Basic

# Verification


1. In a separate session, use `kafka-console-producer` to publish some data to `streams-input-topic`
```shell
kafka-console-producer --broker-list broker:9092 --topic streams-input-topic --property parse.key=true --property key.separator=:
```

2. In another session, use `kafka-console-producer` to view the data being sent to streams-output-topic by your Java application.
```shell
kafka-console-consumer --bootstrap-server broker:9092 --topic streams-output-topic --property print.key=true
```
3. Run your Streams application.
```shell
./gradlew runStreams
```

4. Publish an some records to the `streams-input-topic` and see the same message from the `streams-output-topic`
```shell
b: hello
b: world
c: hello
c: ev
```