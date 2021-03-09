# Kafka Streams Aggregations

# Verification

1. In a separate session, start a `kafka-console-producer` to produce data to the input topic.
```shell 
kafka-console-producer --broker-list broker:9092 --topic aggregations-input-topic --property parse.key=true --property key.separator=:
```


2. Publish an initial record to automatically create the topic.
```shell
a:a
```

3. Open three more sessions. In each one, start a `kafka-console-consumer` to view records being published to the three output topics, then publish some records to the input topic and examine how your Streams application modifies them.

```shell
# to verify the aggregate transformation
kafka-console-consumer --bootstrap-server broker:9092 --topic aggregations-output-charactercount-topic --property print.key=true --property value.deserializer=org.apache.kafka.common.serialization.IntegerDeserializer

# to verify the count transformation
kafka-console-consumer --bootstrap-server broker:9092 --topic aggregations-output-count-topic --property print.key=true --property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer

# to verify the reduce transformation
kafka-console-consumer --bootstrap-server broker:9092 --topic aggregations-output-reduce-topic --property print.key=true
```
4. In the previous session, run your code.
```shell
./gradlew runAggregations
```

5. Publish an some records to the original topic and verify the message in each of the consumer created above
```shell
b: hello
b: world
c: hello
c: ev
```