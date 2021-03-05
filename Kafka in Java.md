# Kafka in Java

## Configure the project
Create the following Gradle build file for the project, named `build.gradle`:
Run the following command to obtain the Gradle wrapper:
```shell
gradle wrapper
```

## Create the KafkaProducer application
Create a directory for the Java files in this project:
```shell
mkdir -p src/main/java/ace/kafka/stream
```
![img](./img/project.png?raw=true "project structure")

### StreamsMain.java
* Function: read from an input stream and write to an output stream
```shell
./gradlew runStreams
```
![img](./img/runStreams.png?raw=true "./gradlew runStreams")

* Verification: 
    1. open a new terminal to publish `streams-input-topic`
    ```shell
    kafka-topics --create --topic streams-input-topic --bootstrap-server broker:9092 --replication-factor 1 --partitions 1
        
    kafka-console-producer --broker-list broker:9092 --topic streams-input-topic --property parse.key=true --property key.separator=:
    ```
    2. Since the function of StreamsMain is to copy `streams-input-topic` and paste as `streams-output-topic`. We now need open another terminal to run a console consumer to read `streams-output-topic`
    ```shell
    kafka-console-consumer --bootstrap-server broker:9092 --topic streams-output-topic --property print.key=true
    ```
    ![img](./img/runStreams-verify.png?raw=true "./gradlew runStreams")