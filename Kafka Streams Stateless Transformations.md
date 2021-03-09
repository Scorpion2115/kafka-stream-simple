# Kafka Streams Stateless Transformations

# Verification
1. In a separate session, starts a `kafka-console-producer` to produce data to the input topic.
```shell
kafka-console-producer --broker-list broker:9092 --topic stateless-transformations-input-topic --property parse.key=true --property key.separator=:
```

2. Publish an initial record to automatically create the topic.
```shell
a:a
```
3. In another session, start a `kafka-console-consumer` to view records being published to the output topic.
```shell
kafka-console-consumer --bootstrap-server broker:9092 --topic stateless-transformations-output-topic --property print.key=true
```
4. In the previous session, run your code.
```shell
./gradlew runStatelessTransformations
```

5. Publish some records and examine how your Streams application modifies them.
```shell
akey:avalue
akey:bvalue
bkey:bvalue
bkey:avalue

