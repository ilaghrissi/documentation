# Kafka
## Introduction
- Kafka is a distributed streaming platform

## Kafka fundamentals
- Kafka include :  
  1. Producer : send multiple data streams to brokers
  2. Broker : receive data from producer
  3. Consumer : read data from broker and process it
  4. Topic : is a way to organize messages.
  5. Partition : Topics are broken down into a number of partitions

### Producer
- Applications that send data into topics
- Applications typically integrate a Kafka client library to write to Apache Kafka.

### Message
Each event message contains :
  - Key : Key is optional in the Kafka message and it can be null. A key may be a string, number, or any object and then the key is serialized into binary format.

  - Value : The value represents the content of the message and can also be null. The value format is arbitrary and is then also serialized into binary format.

  - Compression Type. Kafka messages may be compressed. The compression type can be specified as part of the message. Options are none, gzip, lz4, snappy, and zstd

  - Headers. There can be a list of optional Kafka message headers in the form of key-value pairs. It is common to add headers to specify metadata about the message, especially for tracing.

  - Partition + Offset. Once a message is sent into a Kafka topic, it receives a partition number and an offset id. The combination of topic+partition+offset uniquely identifies the message

  - Timestamp. A timestamp is added either by the user or the system in the message.

* Each event message contains an optional key and a value.
* If a key is sent **(key=null)** is not specified by the producer, messages are distributed evenly across partitions in a topic. This means messages are sent in a round-robin fashion (partition p0 then p1 then p2, etc... then back to p0 and so on...).
* If a key is sent **(key != null)**, then all messages that share the same key will always be sent and stored in the same Kafka partition. A key can be anything to identify a message - a string, numeric value, binary value, etc.
### Broker
### Consumer
- Applications that read data from Kafka topics
- Applications integrate a Kafka client library to read from Apache Kafka.
- Consumers can read from one or more partitions at a time in Apache Kafka
- data is read in order within each partition
- A consumer always reads data from a lower offset to a higher offset and cannot read data backwards
- If the consumer consumes data from more than one partition, the message order is not guaranteed across multiple partitions because they are consumed simultaneously, but the message read order is still guaranteed within each individual partition.
- pull model : This means that Kafka consumers must request data from Kafka brokers in order to get it
- Poison Pills : Messages sent to a Kafka topic that do not respect the agreed-upon serialization format are called poison pills. They are not fun to deal with

#### Consumer Groups
- Consumers can be grouped together as a Kafka consumer group
- The benefit of a Kafka consumer group is that the consumers within the group will coordinate to split the work of reading from different partitions.
- To indicate to Kafka consumers that they are part of the same specific group , we must specify the consumer-side setting **group.id**.
- Kafka Consumers automatically use a **GroupCoordinator** and a **ConsumerCoordinator** to assign consumers to a partition and ensure the load balancing is achieved across all consumers in the same group
- It is important to note that each topic partition is only assigned to one consumer within a consumer group, but a consumer from a consumer group can be assigned multiple partitions.
### Topic
- Kafka topics are immutable: once data is written to a partition, it cannot be changed
- A topic is identified by its name. For example, we may have a topic called logs that may contain log messages from our application, and another topic called purchases that may contain purchase data from our application as it happens.
### Partition
- A single topic may have more than one partition
- The number of partitions of a topic is specified at the time of topic creation. 
- Partitions are numbered starting from 0 to N-1, where N is the number of partitions.
- The offset is an integer value that Kafka adds to each message as it is written into a partition. Each message in a given partition has a unique offset.

Example :
A traffic company wants to track its fleet of trucks. Each truck is fitted with a GPS locator that reports its position to Kafka. We can create a topic named - trucks_gps to which the trucks publish their positions. Each truck may send a message to Kafka every 20 seconds, each message will contain the truck ID and the truck position (latitude and longitude). The topic may be split into a suitable number of partitions, say 10. There may be different consumers of the topic. For example, an application that displays truck locations on a dashboard or another application that sends notifications if an event of interest occurs.

### Offsets
- offsets represent the position of a message within a Kafka Partition. Offset numbering for every partition starts at 0 and is incremented for each message sent to a specific Kafka partition. This means that Kafka offsets only have a meaning for a specific partition, e.g., offset 3 in partition 0 doesn’t represent the same data as offset 3 in partition 1.

## Kafka delivery semantics
Kafka has 3 ways that it can deliver messages 
  1. At least once
  2. At most once
  3. Exactly once