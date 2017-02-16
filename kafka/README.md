### Install Kafka (one time)

```bash
# brew install kafka
cd /Developer/Applications/
# wget http://packages.confluent.io/archive/3.1/confluent-oss-3.1.2-2.11.tar.gz
curl http://packages.confluent.io/archive/3.1/confluent-oss-3.1.2-2.11.tar.gz | tar xz
```

#### Starting Kafka Services

*you will be running all commends below from* **infra/kafka** *directory*

```
cd infra/kafka
export KAFKA_HOME=/Developer/Applications/confluent-3.1.2
```

#### To Start Zookeeper
```bash
$KAFKA_HOME/bin/zookeeper-server-start ./zookeeper.properties
```

#### To Start Kafka
```bash
$KAFKA_HOME/bin/kafka-server-start ./server.properties
```

#### To Start Schema Registry
```bash
$KAFKA_HOME/bin/schema-registry-start ./schema-registry.properties
```

#### Create Kafka Topic and partitioning (one time)
```bash
$KAFKA_HOME/bin/kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic maxwell
```

#### List Kafka Topics
```bash
$KAFKA_HOME/bin/kafka-topics --list --zookeeper localhost:2181
```

#### Display messages on a topic
```bash
$KAFKA_HOME/bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic maxwell --from-beginning --property print.key=true
# for kafka-maxwell-connector
$KAFKA_HOME/bin/kafka-console-consumer --bootstrap-server localhost:9092 --topic maxwell.test.shop --from-beginning --property print.key=true
# Show Avro data in JSON format in the console.
$KAFKA_HOME/bin/kafka-avro-console-consumer -bootstrap-server localhost:9092 --topic maxwell.test.shop --property print.key=true --property schema.registry.url=http://localhost:8081
```


*NOTE: stop Kafka first and then Zookeeper*
