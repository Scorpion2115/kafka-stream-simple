# Initialize the project

## Get started
To get started, make a new directory anywhere you’d like for this project:
```shell
mkdir kafka-on-the-shore && cd kafka-on-the-shore
```
## Get Confluent Platform
Next, create the following `docker-compose.yml` file to obtain Confluent Platform and launch it by running:
```shell
docker-compose up -d
```

## Clean up
After you finish, kill all running containers with 
```shell
docker kill $(docker ps -q)
```

Delete all containers that are not running.
```shell
docker container rm $(docker ps -a -q)
```