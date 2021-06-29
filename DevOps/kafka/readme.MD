# RUNNING KAFKA IN DOCKER

## STARTING CONTAINER

- Open the folder into Powershell terminal
	- Execute command `docker-compose -f docker-compose.yml up -d` to start the containers

## NAVIGATE TO RIGHT FOLDER

- Execute `docker exec -it kafka /bin/sh`
- Execute below commands to inside the folder in order to topic creation
	- Execute `cd opt`
	- Execute `cd kafka_2.13-2.7.0`
	- Execute `cd bin` - check all .sh files exist here
	- Execute `cd ..` to come out of bin folder

## TOPICS CRETION

- Execute `./bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic mytopic` to create the topic, observe the topic created

- Execute `./bin/kafka-topics.sh --list --zookeeper zookeeper:2181` to see the list of topics, it should list _mytopic_ as result

- Execute `./bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic test` to create another topic, 

- Execute `./bin/kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic demo` to create one more topic, 

- Execute `./bin/kafka-topics.sh --list --zookeeper zookeeper:2181` to see the list of all topics created

## PRODUCER CRETION

- Execute `./bin/kafka-console-producer.sh --broker-list localhost:9092 --topic mytopic` this will show > symbol on enter, it's fine

## CONSUMER CRETION

- Open another terminal window at same level (Follow _NAVIGATE TO RIGHT FOLDER_ instructions) and execute command `./bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic mytopic --from-beginning`

## MESSAGING
- Go to producer terminal and type _hi_ and hit enter
- Go to consumer terminal and observe the message is received
- Can test this with series of messages

## STOPPING CONTAINER
- Execute command `docker-compose down` to stop the containers

## TROUBLESHOOTING

#### Error

If get the error 'Ports are not available: listen tcp 0.0.0.0:4449: bind: An attempt was made to access a socket in a way forbidden by its access permissions' then 

#### Resolution

- Reference: https://github.com/docker/for-win/issues/9272
- Execute `net stop winnat` from the terminal
- Execute `net start winnat`from the terminal
- Execute command `docker-compose -f docker-compose.yml up -d` to start the containers and it should work now

##### References

- [Youtube](https://www.youtube.com/watch?v=WnlX7w4lHvM&t=930s)
- [Github](https://github.com/docker/for-win/issues/9272)