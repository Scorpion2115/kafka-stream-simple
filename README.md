# README

1. Initialize the project
2. Kafka in Java
3. Kafka in CommandLine


# Kafka Streams Stateless Transformation
branch: take a stream and split it to multiple streams
filter: remove records from the stream
FlatMap: it takes a record and transforms it into a different set of records.
Map: Takes one record and produces one record, while retaining the key 
Merge: Merges records of two streams into one larger stream
Peek: Performs a stateless action on each record, and returns an unchanged stream
Foreach: Performs a stateless action on each record.

## Stateless: do not require any additional storage to manage the state
## Stateful: require a state store to manage the state