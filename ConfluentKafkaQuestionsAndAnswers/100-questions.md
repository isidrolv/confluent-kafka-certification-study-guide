# Confluent Kafka Developer Certification - 100 Practice Questions

## Basic Questions (1-35)

### 1. What is Apache Kafka?
   a. A relational database management system
   b. A distributed streaming platform
   c. A message queue only
   d. A file storage system

Ans: b

Explanation: Apache Kafka is a distributed streaming platform that is used for building real-time data pipelines and streaming applications. It is horizontally scalable, fault-tolerant, and provides high throughput for both publishing and subscribing to streams of records. Kafka is not just a message queue; it also provides storage capabilities with configurable retention periods and can process streams of data in real-time.

### 2. What are the main components of Kafka architecture?
   a. Producer, Consumer, Database
   b. Producer, Consumer, Broker, ZooKeeper
   c. Client, Server, Cache
   d. Publisher, Subscriber, Router

Ans: b

Explanation: The main components of Kafka architecture are: Producers (which publish messages to Kafka topics), Consumers (which subscribe to topics and process messages), Brokers (Kafka servers that store and serve data), and ZooKeeper (which manages and coordinates Kafka brokers). Note that newer versions of Kafka (KRaft mode) are removing the ZooKeeper dependency.

### 3. What is a Kafka topic?
   a. A database table
   b. A category or feed name to which records are published
   c. A consumer group
   d. A server instance

Ans: b

Explanation: A Kafka topic is a category or feed name to which records are published by producers. Topics in Kafka are always multi-subscriber, meaning a topic can have zero, one, or many consumers that subscribe to the data written to it. Topics are logical channels that organize and categorize data streams.

### 4. What is a Kafka partition?
   a. A way to divide a topic into smaller units for parallelism and scalability
   b. A backup copy of data
   c. A consumer group
   d. A compression algorithm

Ans: a

Explanation: A partition is a way to divide a Kafka topic into smaller, ordered, and immutable sequences of records. Partitions allow topics to be parallelized by splitting the data across multiple brokers. Each partition is replicated across a configurable number of servers for fault tolerance. Partitions enable Kafka to scale horizontally and provide ordering guarantees within each partition.

### 5. What is the default port for Kafka broker?
   a. 8080
   b. 2181
   c. 9092
   d. 3306

Ans: c

Explanation: The default port for Kafka broker is 9092. This is the port that producers and consumers use to connect to Kafka brokers. Port 2181 is the default port for ZooKeeper, which Kafka uses for coordination (in non-KRaft mode). Port 8080 is commonly used for web applications, and 3306 is the default MySQL port.

### 6. What is a Kafka producer?
   a. A component that reads data from topics
   b. A component that publishes messages to Kafka topics
   c. A storage system
   d. A monitoring tool

Ans: b

Explanation: A Kafka producer is a client application that publishes (writes) messages to Kafka topics. Producers are responsible for choosing which partition within a topic to send records to. This can be done in a round-robin fashion for load balancing, or it can be based on a semantic partition function (like a hash of the message key).

### 7. What is a Kafka consumer?
   a. A component that writes data to topics
   b. A component that reads messages from Kafka topics
   c. A backup service
   d. A replication mechanism

Ans: b

Explanation: A Kafka consumer is a client application that reads (consumes) messages from Kafka topics. Consumers subscribe to one or more topics and process the stream of records produced to them. Consumers are typically part of a consumer group, which allows for load balancing and fault tolerance in message consumption.

### 8. What is a consumer group?
   a. A set of producers working together
   b. A set of consumers collaborating to consume data from topics
   c. A collection of topics
   d. A set of brokers in a cluster

Ans: b

Explanation: A consumer group is a set of consumers that cooperate to consume data from some topics. Each partition of a topic is consumed by exactly one consumer within each consumer group. This allows for parallel processing of messages while maintaining ordering guarantees within partitions. Consumer groups enable both message broadcasting and load balancing patterns.

### 9. What is the role of ZooKeeper in Kafka (pre-KRaft)?
   a. To store all message data
   b. To coordinate and manage Kafka brokers and store metadata
   c. To compress messages
   d. To encrypt data

Ans: b

Explanation: In traditional Kafka deployments, ZooKeeper is used to store metadata about the Kafka cluster, including information about topics, partitions, consumer groups, and broker configurations. It also helps in leader election for partitions and maintains the health status of brokers. However, newer versions of Kafka are moving to KRaft mode, which eliminates the need for ZooKeeper.

### 10. What is a Kafka broker?
   a. A consumer application
   b. A producer application
   c. A server that stores and serves data
   d. A monitoring dashboard

Ans: c

Explanation: A Kafka broker is a server in the Kafka cluster that receives messages from producers, assigns offsets to them, and stores the messages on disk. Brokers also serve data to consumers that request to read messages. A Kafka cluster typically consists of multiple brokers to provide fault tolerance and scalability.

### 11. What is message offset in Kafka?
   a. A unique identifier for a partition
   b. A sequential ID number assigned to each message within a partition
   c. A timestamp of message creation
   d. A consumer group ID

Ans: b

Explanation: An offset is a sequential ID number assigned to each message within a partition. The offset uniquely identifies each record within that partition. Consumers use offsets to track their position in the partition, allowing them to resume from where they left off in case of failure. Offsets start at 0 for the first message in a partition.

### 12. What is the default replication factor in Kafka?
   a. 1
   b. 2
   c. 3
   d. 0

Ans: a

Explanation: The default replication factor in Kafka is 1, which means no replication. However, in production environments, it's strongly recommended to set a replication factor of at least 3 for fault tolerance. The replication factor determines how many copies of the data are maintained across different brokers in the cluster.

### 13. What is the purpose of the __consumer_offsets topic?
   a. To store producer configurations
   b. To store consumer group offsets
   c. To store broker metadata
   d. To store message keys

Ans: b

Explanation: The __consumer_offsets topic is an internal Kafka topic used to store consumer group offset information. When consumers commit their offsets, these are written to this internal topic. This allows consumers to resume from their last committed position in case of failure or restart. The topic is managed by Kafka and typically has a high replication factor for reliability.

### 14. What does ISR stand for in Kafka?
   a. Internal System Registry
   b. In-Sync Replicas
   c. Integrated Service Router
   d. Index Search Results

Ans: b

Explanation: ISR stands for In-Sync Replicas. It refers to the set of replica partitions that are fully caught up with the leader partition. Only replicas in the ISR are eligible to become the leader if the current leader fails. A replica is considered in-sync if it has fully caught up with the leader's log and has been sending fetch requests regularly.

### 15. What is the purpose of the message key in Kafka?
   a. To encrypt messages
   b. To determine message priority
   c. To determine which partition a message goes to
   d. To authenticate producers

Ans: c

Explanation: The message key in Kafka is primarily used to determine which partition a message should be sent to. By default, Kafka uses a hash of the key to select the partition, ensuring that all messages with the same key go to the same partition. This provides ordering guarantees for messages with the same key. If no key is provided, messages are distributed in a round-robin fashion.

### 16. What is the minimum number of brokers required for a Kafka cluster?
   a. 3
   b. 5
   c. 1
   d. 2

Ans: c

Explanation: Technically, a Kafka cluster can run with just 1 broker for development or testing purposes. However, for production environments, it's recommended to have at least 3 brokers to ensure fault tolerance and high availability. With multiple brokers, the cluster can continue operating even if one or more brokers fail, provided the replication factor is set appropriately.

### 17. What is the default retention period for messages in Kafka?
   a. 1 hour
   b. 24 hours
   c. 7 days
   d. 30 days

Ans: c

Explanation: The default retention period for messages in Kafka is 7 days (168 hours). This is controlled by the log.retention.hours configuration parameter. After this period, messages are eligible for deletion to free up disk space. The retention period can be configured at the broker level or per topic. Kafka also supports retention based on size (log.retention.bytes).

### 18. What protocol does Kafka use for communication?
   a. HTTP
   b. TCP
   c. UDP
   d. FTP

Ans: b

Explanation: Kafka uses TCP (Transmission Control Protocol) for communication between clients (producers and consumers) and brokers. The Kafka protocol is a binary protocol built on top of TCP that is optimized for high performance. It uses persistent connections and supports request pipelining for efficiency.

### 19. What is a Kafka Connect?
   a. A tool for monitoring Kafka clusters
   b. A framework for connecting Kafka with external systems
   c. A security protocol
   d. A compression algorithm

Ans: b

Explanation: Kafka Connect is a framework for connecting Kafka with external systems such as databases, key-value stores, search indexes, and file systems. It provides a scalable and reliable way to move data in and out of Kafka without writing custom producer or consumer code. Connect supports both source connectors (to import data into Kafka) and sink connectors (to export data from Kafka).

### 20. What is Kafka Streams?
   a. A database system
   b. A client library for building streaming applications
   c. A monitoring tool
   d. A message broker

Ans: b

Explanation: Kafka Streams is a client library for building applications and microservices where the input and output data are stored in Kafka clusters. It allows you to build real-time streaming applications that transform, aggregate, and process data stored in Kafka topics. Kafka Streams provides high-level DSL and low-level Processor API for building stream processing applications.

### 21. What is the purpose of acks configuration in producer?
   a. To set message compression
   b. To control how many acknowledgments the producer requires from brokers
   c. To set consumer group ID
   d. To enable encryption

Ans: b

Explanation: The acks configuration controls how many acknowledgments the producer requires the leader broker to have received before considering a request complete. acks=0 means the producer doesn't wait for acknowledgment, acks=1 means wait for leader acknowledgment, and acks=all means wait for acknowledgment from all in-sync replicas. This setting affects both throughput and durability guarantees.

### 22. What is the purpose of log compaction in Kafka?
   a. To compress messages using gzip
   b. To retain only the latest value for each key
   c. To delete all old messages
   d. To encrypt log files

Ans: b

Explanation: Log compaction is a mechanism in Kafka that ensures that Kafka will always retain at least the last known value for each message key within the log of data for a single topic partition. This is useful for maintaining a compacted changelog where you only care about the latest state of each key, such as in change data capture (CDC) scenarios or maintaining materialized views.

### 23. What is the default serializer for Kafka producer?
   a. JSONSerializer
   b. StringSerializer
   c. ByteArraySerializer
   d. There is no default; it must be explicitly set

Ans: d

Explanation: There is no default serializer in Kafka; you must explicitly configure the key.serializer and value.serializer properties when creating a producer. Common serializers include StringSerializer, ByteArraySerializer, and custom serializers for specific data formats like Avro or JSON. This explicit configuration ensures that developers are aware of how their data is being serialized.

### 24. What does the min.insync.replicas configuration control?
   a. Minimum number of consumers in a group
   b. Minimum number of in-sync replicas required for a write to succeed
   c. Minimum number of brokers in the cluster
   d. Minimum number of partitions per topic

Ans: b

Explanation: The min.insync.replicas configuration specifies the minimum number of replicas that must acknowledge a write for it to be considered successful when acks=all. For example, if min.insync.replicas=2 and you have 3 replicas, at least 2 replicas (including the leader) must acknowledge the write. This provides a balance between durability and availability.

### 25. What is a Kafka record?
   a. Only a message key
   b. A key-value pair with optional headers and metadata
   c. Only a message value
   d. A consumer offset

Ans: b

Explanation: A Kafka record (also called a message) consists of a key, a value, headers, and metadata such as timestamp and partition. The key and value are byte arrays that can contain any serialized data. Headers allow you to add metadata to records without modifying the key or value. The timestamp indicates when the record was created or ingested.

### 26. What is the role of the bootstrap.servers configuration?
   a. To specify all brokers in the cluster
   b. To provide initial connection points to the Kafka cluster
   c. To define consumer groups
   d. To set topic replication factor

Ans: b

Explanation: The bootstrap.servers configuration provides a list of host:port pairs to use for establishing the initial connection to the Kafka cluster. You don't need to specify all brokers; the client will discover all brokers in the cluster once connected. However, it's recommended to provide multiple brokers for redundancy in case one is down during initial connection.

### 27. What is the purpose of consumer.poll() method?
   a. To commit offsets
   b. To fetch records from Kafka topics
   c. To create new topics
   d. To delete messages

Ans: b

Explanation: The poll() method is the primary way a consumer fetches records from Kafka topics. It returns all available records from the assigned partitions. The method takes a timeout parameter that controls how long it blocks if data is not immediately available. Calling poll() also handles consumer group coordination, partition rebalancing, and heartbeats.

### 28. What is partition leader in Kafka?
   a. The broker with the most storage
   b. The replica that handles all reads and writes for a partition
   c. The oldest broker in the cluster
   d. The broker with the highest ID

Ans: b

Explanation: The partition leader is the replica that handles all read and write requests for a particular partition. Each partition has exactly one leader and zero or more follower replicas. The leader maintains the log and coordinates with followers to ensure they stay in sync. If the leader fails, one of the in-sync replicas is elected as the new leader.

### 29. What is the purpose of enable.auto.commit configuration?
   a. To enable automatic topic creation
   b. To enable automatic offset committing by the consumer
   c. To enable automatic broker failover
   d. To enable automatic message compression

Ans: b

Explanation: The enable.auto.commit configuration determines whether the consumer automatically commits offsets in the background. When set to true, offsets are committed automatically at regular intervals defined by auto.commit.interval.ms. When false, the application must manually commit offsets using commitSync() or commitAsync(). Manual commit gives more control but requires more code.

### 30. What is a Kafka Schema Registry?
   a. A DNS server for Kafka
   b. A centralized repository for managing schemas
   c. A user authentication system
   d. A partition assignment strategy

Ans: b

Explanation: Kafka Schema Registry is a centralized repository for managing and validating schemas for topic message data. It provides a RESTful interface for storing and retrieving Avro, JSON Schema, and Protobuf schemas. Schema Registry ensures data compatibility and allows schema evolution while maintaining backward and forward compatibility. It's commonly used with Confluent Platform but can be used with Apache Kafka as well.

### 31. What is the difference between Kafka and traditional message queues?
   a. Kafka only supports publish-subscribe pattern
   b. Kafka stores messages on disk and supports replay, traditional queues delete messages after consumption
   c. Kafka is slower than traditional queues
   d. Traditional queues are more scalable

Ans: b

Explanation: Unlike traditional message queues that delete messages after they are consumed, Kafka stores messages on disk with a configurable retention period. This allows consumers to replay messages and multiple consumers to read the same messages. Kafka supports both publish-subscribe and queue patterns through consumer groups. It's designed for high throughput and horizontal scalability.

### 32. What is the purpose of session.timeout.ms configuration?
   a. To set producer timeout
   b. To detect consumer failures in a consumer group
   c. To set message retention time
   d. To define connection timeout to brokers

Ans: b

Explanation: The session.timeout.ms configuration determines how long a consumer can go without sending a heartbeat to the group coordinator before being considered dead. If no heartbeat is received within this timeout, the coordinator triggers a rebalance to redistribute partitions to other consumers in the group. The default is typically 10 seconds. This must be balanced with heartbeat.interval.ms.

### 33. What is idempotent producer in Kafka?
   a. A producer that encrypts messages
   b. A producer that ensures exactly-once delivery semantics
   c. A producer that compresses messages
   d. A producer that batches messages

Ans: b

Explanation: An idempotent producer ensures that messages are delivered exactly once to a particular partition, even if the producer retries due to network errors or timeouts. This is achieved by assigning a unique sequence number to each message. When enable.idempotence=true, Kafka can detect and discard duplicate messages, preventing issues like message duplication during retries.

### 34. What is the purpose of linger.ms configuration in producer?
   a. To set message expiration time
   b. To add artificial delay to allow batching of messages
   c. To set consumer lag threshold
   d. To define partition count

Ans: b

Explanation: The linger.ms configuration adds a small artificial delay (in milliseconds) before sending a batch of messages. This allows more messages to accumulate in the batch, improving throughput by reducing the number of requests. A value of 0 means messages are sent immediately. A higher value increases latency slightly but can significantly improve throughput for high-volume scenarios.

### 35. What happens when a consumer fails in a consumer group?
   a. All messages are lost
   b. The cluster shuts down
   c. A rebalance occurs and partitions are reassigned to remaining consumers
   d. Nothing, messages queue up indefinitely

Ans: c

Explanation: When a consumer fails in a consumer group, the group coordinator detects the failure (through missing heartbeats) and triggers a rebalance. During rebalancing, the partitions previously assigned to the failed consumer are redistributed among the remaining active consumers in the group. This ensures that message processing continues despite consumer failures, providing fault tolerance.

## Intermediate Questions (36-70)

### 36. What is the purpose of max.poll.records configuration?
   a. To set the maximum number of topics
   b. To control the maximum number of records returned in a single poll() call
   c. To set the maximum partition count
   d. To limit the number of consumer groups

Ans: b

Explanation: The max.poll.records configuration controls the maximum number of records returned in a single call to poll(). This is useful for controlling the amount of data your application needs to process in each iteration and can help prevent overwhelming the consumer application. The default value is 500. Setting this too high might cause processing timeouts, while setting it too low might reduce throughput.

### 37. What is the difference between at-most-once, at-least-once, and exactly-once delivery semantics?
   a. They all mean the same thing
   b. At-most-once: messages may be lost; at-least-once: messages may be duplicated; exactly-once: messages are delivered exactly once
   c. Only at-least-once is possible in Kafka
   d. They refer to compression algorithms

Ans: b

Explanation: These are different delivery guarantees in message processing. At-most-once means messages may be lost but never duplicated (acks=0, commit before processing). At-least-once means messages may be duplicated but never lost (acks=all, commit after processing). Exactly-once means messages are delivered exactly once without loss or duplication (achieved through idempotent producers and transactional writes).

### 38. What is a Kafka transaction?
   a. A database commit
   b. An atomic write operation across multiple partitions and topics
   c. A consumer offset commit
   d. A network protocol

Ans: b

Explanation: Kafka transactions allow producers to send data to multiple topics and partitions atomically. Either all messages in the transaction are written successfully, or none are. This is crucial for exactly-once semantics in stream processing applications. Transactions are configured using transactional.id and managed through methods like beginTransaction(), commitTransaction(), and abortTransaction().

### 39. What is the purpose of fetch.min.bytes configuration for consumers?
   a. To limit consumer memory usage
   b. To specify the minimum amount of data the server should return for a fetch request
   c. To set partition size
   d. To define message key size

Ans: b

Explanation: The fetch.min.bytes configuration specifies the minimum amount of data the broker should return for a fetch request. If insufficient data is available, the request will wait up to fetch.max.wait.ms before responding. This can improve throughput by reducing the number of fetch requests when the message rate is low. The default is 1 byte, meaning the broker responds immediately with available data.

### 40. What is partition reassignment in Kafka?
   a. Deleting all partitions
   b. Moving partitions from one set of brokers to another
   c. Changing the replication factor
   d. Renaming partitions

Ans: b

Explanation: Partition reassignment is the process of moving partitions from one set of brokers to another in the cluster. This is typically done for load balancing, decommissioning brokers, or adding new brokers to the cluster. The kafka-reassign-partitions tool is used to generate reassignment plans and execute them. During reassignment, data is replicated to new brokers while maintaining availability.

### 41. What is the purpose of compression.type configuration?
   a. To encrypt messages
   b. To specify the compression codec for messages (none, gzip, snappy, lz4, zstd)
   c. To compact logs
   d. To compress broker metadata

Ans: b

Explanation: The compression.type configuration specifies the compression codec used to compress message batches. Supported values include none, gzip, snappy, lz4, and zstd. Compression reduces network bandwidth and storage requirements but adds CPU overhead for compression and decompression. The choice depends on the trade-off between compression ratio and CPU usage. Producers compress data, and it stays compressed in the broker until consumed.

### 42. What is the purpose of max.in.flight.requests.per.connection?
   a. To limit the number of unacknowledged requests per broker connection
   b. To set the maximum partition count
   c. To limit consumer poll requests
   d. To define timeout values

Ans: a

Explanation: This configuration controls the maximum number of unacknowledged requests the producer will send on a single connection before blocking. Setting this to 1 ensures ordering even with retries, but it can reduce throughput. Higher values improve throughput through pipelining but may result in out-of-order messages if retries occur. For exactly-once semantics with retries, this should be set to 5 or less.

### 43. What is a Kafka MirrorMaker?
   a. A backup tool
   b. A tool for replicating data between Kafka clusters
   c. A monitoring dashboard
   d. A schema validation tool

Ans: b

Explanation: MirrorMaker is a tool for replicating data between Kafka clusters. It consists of a consumer that reads from a source cluster and a producer that writes to a destination cluster. MirrorMaker 2.0 (based on Kafka Connect) provides more features like automatic topic creation, offset sync, and checkpoint management. It's commonly used for disaster recovery, data migration, and aggregating data from multiple data centers.

### 44. What is the purpose of auto.offset.reset configuration?
   a. To automatically delete old offsets
   b. To determine what to do when there's no initial offset or the offset is out of range
   c. To reset all consumer offsets daily
   d. To enable offset compression

Ans: b

Explanation: The auto.offset.reset configuration controls the consumer's behavior when there is no committed offset or when the committed offset is no longer valid (e.g., data has been deleted). Values include: 'earliest' (start from the beginning of the partition), 'latest' (start from the end/newest records), and 'none' (throw an exception). This is important for new consumer groups or when recovering from data loss.

### 45. What is the difference between commitSync() and commitAsync()?
   a. They are the same
   b. commitSync() blocks until offset commit succeeds; commitAsync() doesn't block
   c. commitSync() is faster
   d. commitAsync() is deprecated

Ans: b

Explanation: commitSync() blocks the consumer until the offset commit request is acknowledged or fails, which can reduce throughput but provides strong guarantees. commitAsync() doesn't block and allows the consumer to continue processing while the commit happens in the background. commitAsync() accepts a callback for handling results. A common pattern is to use commitAsync() during normal processing and commitSync() during shutdown for final commits.

### 46. What is consumer lag?
   a. Network latency between consumer and broker
   b. The difference between the last produced message offset and the last committed consumer offset
   c. Consumer processing time
   d. Time to start a consumer

Ans: b

Explanation: Consumer lag is the difference between the latest offset in the partition (high water mark) and the current offset of the consumer. It indicates how far behind the consumer is in processing messages. High lag might indicate that consumers can't keep up with the production rate, suggesting the need for more consumer instances, optimization, or increased parallelism. Monitoring consumer lag is critical for ensuring real-time processing.

### 47. What is the purpose of isolation.level configuration for consumers?
   a. To control network isolation
   b. To control whether consumers read uncommitted or committed transactional messages
   c. To set authentication level
   d. To define partition isolation

Ans: b

Explanation: The isolation.level configuration determines whether the consumer reads uncommitted or only committed transactional messages. Values are 'read_uncommitted' (default, reads all messages) and 'read_committed' (only reads committed transactional messages and non-transactional messages). When set to read_committed, the consumer won't see messages from aborted transactions, supporting exactly-once semantics in stream processing.

### 48. What is a Kafka producer interceptor?
   a. A security filter
   b. A plugin that allows you to intercept and modify records before they are sent
   c. A network proxy
   d. A schema validator

Ans: b

Explanation: Producer interceptors are plugins that allow you to intercept (and potentially modify) records before they're sent to the broker and also receive acknowledgments. They implement the ProducerInterceptor interface with methods like onSend() and onAcknowledgement(). Common use cases include adding metadata, monitoring, auditing, or enforcing policies. Multiple interceptors can be chained together.

### 49. What is a consumer interceptor?
   a. A firewall rule
   b. A plugin that allows you to intercept and modify records after they are received
   c. A schema converter
   d. A compression algorithm

Ans: b

Explanation: Consumer interceptors allow you to intercept records after they're received from the broker but before they're returned to the application. They implement the ConsumerInterceptor interface with methods like onConsume() and onCommit(). Use cases include monitoring, enriching records with metadata, filtering, or transformation. Like producer interceptors, multiple consumer interceptors can be chained.

### 50. What is the purpose of replica.lag.time.max.ms configuration?
   a. To set consumer lag threshold
   b. To determine when a replica falls out of ISR
   c. To set producer timeout
   d. To define log retention time

Ans: b

Explanation: The replica.lag.time.max.ms configuration (default 10 seconds) determines how long a replica can fail to fetch from the leader before it's removed from the In-Sync Replica (ISR) set. If a replica hasn't sent a fetch request or hasn't caught up to the leader's log end offset within this time, it's considered out of sync. This is important for maintaining the ISR and ensuring data durability.

### 51. What is the purpose of unclean.leader.election.enable configuration?
   a. To enable automatic topic creation
   b. To allow out-of-sync replicas to become leaders
   c. To enable consumer group coordination
   d. To allow partition deletion

Ans: b

Explanation: When set to true, unclean.leader.election.enable allows replicas that are not in the ISR to become leaders when all ISR replicas are down. This sacrifices data consistency for availability—data loss may occur as the new leader might not have all committed messages. Setting it to false (recommended) prioritizes consistency and waits for an ISR replica to recover, but may result in downtime.

### 52. What is the difference between KafkaProducer and KafkaConsumer thread safety?
   a. Both are thread-safe
   b. KafkaProducer is thread-safe; KafkaConsumer is not
   c. KafkaConsumer is thread-safe; KafkaProducer is not
   d. Neither is thread-safe

Ans: b

Explanation: KafkaProducer is thread-safe and can be shared across threads, making it efficient to use a single producer instance for multiple threads. However, KafkaConsumer is NOT thread-safe, and concurrent access from multiple threads requires external synchronization. The recommended pattern is to use one consumer instance per thread. This design decision was made because consumer coordination and offset management are complex and easier to reason about in a single-threaded context.

### 53. What is partition rebalancing?
   a. Redistributing messages within a partition
   b. The process of redistributing partition ownership among consumers in a group
   c. Changing partition count
   d. Compressing partition data

Ans: b

Explanation: Partition rebalancing is the process of redistributing partition assignments among consumers in a consumer group. It's triggered when consumers join or leave the group, or when partition count changes. During rebalancing, consumers stop consuming, partitions are reassigned, and consumers resume from committed offsets. Excessive rebalancing can impact performance, so it's important to configure session.timeout.ms and max.poll.interval.ms appropriately.

### 54. What is the purpose of max.poll.interval.ms?
   a. To set the maximum time between consecutive poll() calls
   b. To set partition count
   c. To define message retention
   d. To control compression interval

Ans: a

Explanation: The max.poll.interval.ms configuration sets the maximum time between consecutive calls to poll(). If this interval is exceeded, the consumer is considered failed and will be removed from the group, triggering a rebalance. This prevents a slow or stuck consumer from holding onto partitions indefinitely. The value should be set higher than the maximum expected processing time for the records returned by a single poll().

### 55. What is a Kafka quota?
   a. A limit on topic count
   b. Limits on produce/fetch rates or request rates to prevent resource starvation
   c. A limit on consumer groups
   d. A partition count limit

Ans: b

Explanation: Kafka quotas are limits that can be applied to clients to prevent any single client from monopolizing broker resources. Quotas can be set for produce rates, fetch rates, and request rates, and can be configured per-client-id, per-user, or per-group. When a client exceeds its quota, requests are throttled by delaying responses. This ensures fair resource sharing and prevents denial-of-service scenarios in multi-tenant environments.

### 56. What is the purpose of request.timeout.ms configuration?
   a. To set how long the producer waits for a response from the broker
   b. To set consumer group timeout
   c. To define message expiration
   d. To control rebalance timeout

Ans: a

Explanation: The request.timeout.ms configuration controls how long the producer or consumer will wait for a response to a request from the broker. If the broker doesn't respond within this time, the request is marked as failed and may be retried. The default is typically 30 seconds. This should be set larger than replica.lag.time.max.ms to allow for replica synchronization delays. Setting it too low can cause unnecessary retries.

### 57. What is log segment in Kafka?
   a. A monitoring metric
   b. A portion of a partition's log stored in a single file
   c. A consumer group identifier
   d. A compression type

Ans: b

Explanation: A log segment is a portion of a partition's log that is stored in a single file on disk. Kafka divides each partition's log into segments for management purposes. The active segment receives all new writes, while older segments are immutable. Segments are rolled based on size (segment.bytes) or time (segment.ms). Log compaction, deletion, and retention operate on segments, making them easier to manage than one large file.

### 58. What is the purpose of segment.ms configuration?
   a. To set message processing time
   b. To control how long before Kafka rolls a new log segment
   c. To define consumer timeout
   d. To set replication delay

Ans: b

Explanation: The segment.ms configuration controls the time period after which Kafka will force the log to roll to a new segment, even if the segment file isn't full. The default is 7 days. This is important because retention and compaction policies operate at the segment level. More frequent segment rolling allows for finer-grained retention control but creates more files, while less frequent rolling reduces file count but makes retention less precise.

### 59. What is the Kafka Controller?
   a. A consumer application
   b. A special broker responsible for managing partition leadership and cluster metadata
   c. A monitoring tool
   d. A schema registry component

Ans: b

Explanation: The Kafka Controller is one of the brokers in the cluster that is elected to have additional responsibilities beyond normal broker duties. It manages partition leader election, handles broker failures, and communicates state changes to all brokers. There is always exactly one controller in the cluster. If the controller fails, another broker is elected. The controller stores its state in ZooKeeper (pre-KRaft) or uses the KRaft protocol.

### 60. What is the purpose of retention.bytes configuration?
   a. To limit consumer memory
   b. To set the maximum size of the log before deleting old segments
   c. To limit message size
   d. To define producer buffer size

Ans: b

Explanation: The retention.bytes configuration sets the maximum size of the log for a partition before old segments are deleted. This works alongside retention.ms (time-based retention). When either threshold is reached, segments become eligible for deletion. The default is -1, meaning infinite size-based retention. This is useful for limiting disk usage per partition, especially in scenarios where message rates vary significantly over time.

### 61. What is the purpose of buffer.memory configuration in producer?
   a. To set broker memory
   b. To control the total memory available to the producer for buffering records
   c. To limit consumer memory
   d. To define partition size

Ans: b

Explanation: The buffer.memory configuration sets the total bytes of memory the producer can use to buffer records waiting to be sent to the broker. If records are sent faster than they can be transmitted to the server, the producer will block for max.block.ms before throwing an exception. The default is 32MB. This buffer allows for batching and improves throughput but must be balanced against memory availability.

### 62. What is the purpose of delivery.timeout.ms?
   a. To set consumer timeout
   b. To set an upper bound on the time to report success or failure after calling send()
   c. To define message expiration
   d. To control rebalance timeout

Ans: b

Explanation: The delivery.timeout.ms configuration sets an upper bound on the time to report success or failure after calling send(). It covers the time spent in the buffer, serialization, transmission, and waiting for acknowledgment. The default is 120 seconds. This value should be greater than or equal to linger.ms + request.timeout.ms. If the timeout is reached before acknowledgment, the producer will throw a TimeoutException.

### 63. What is partition assignment strategy?
   a. How messages are assigned to partitions
   b. How partitions are assigned to consumers in a consumer group
   c. How brokers are assigned to partitions
   d. How topics are assigned to clusters

Ans: b

Explanation: Partition assignment strategy determines how partitions are distributed among consumers in a consumer group. Common strategies include: RangeAssignor (assigns consecutive partitions to each consumer), RoundRobinAssignor (distributes partitions evenly in a round-robin fashion), StickyAssignor (minimizes movement during rebalancing), and CooperativeStickyAssignor (allows incremental rebalancing). The strategy can be configured using partition.assignment.strategy.

### 64. What is the purpose of max.request.size configuration?
   a. To limit broker storage
   b. To set the maximum size of a request sent by the producer
   c. To define partition count
   d. To control consumer buffer size

Ans: b

Explanation: The max.request.size configuration sets the maximum size of a request sent by the producer. This effectively limits the maximum size of a single message or the size of a batch of messages. The default is 1MB. This must be coordinated with the broker's message.max.bytes and replica.fetch.max.bytes configurations. Setting it too high can cause memory issues, while setting it too low can prevent sending legitimate large messages.

### 65. What is a Kafka sink connector?
   a. A tool for exporting data from Kafka to external systems
   b. A tool for importing data into Kafka
   c. A monitoring component
   d. A compression algorithm

Ans: a

Explanation: A Kafka sink connector is a component of Kafka Connect that exports data from Kafka topics to external systems such as databases, file systems, search indexes, or other data stores. Sink connectors read from Kafka topics and write to the destination system. They handle concerns like schema conversion, error handling, and delivery guarantees. Popular sink connectors include JDBC, Elasticsearch, S3, and HDFS.

### 66. What is a Kafka source connector?
   a. A tool for exporting data from Kafka
   b. A tool for importing data from external systems into Kafka
   c. A security component
   d. A partition strategy

Ans: b

Explanation: A Kafka source connector is a component of Kafka Connect that imports data from external systems into Kafka topics. Source connectors read from databases, file systems, message queues, or other data sources and write to Kafka. They handle tasks like data polling, change data capture, schema inference, and offset management. Popular source connectors include JDBC, Debezium (for CDC), File Source, and MongoDB.

### 67. What is the purpose of fetch.max.wait.ms?
   a. To set producer timeout
   b. To set the maximum time the broker waits before responding to a fetch request
   c. To define consumer lag threshold
   d. To control rebalance time

Ans: b

Explanation: The fetch.max.wait.ms configuration sets the maximum time the broker will wait before responding to a fetch request if there isn't sufficient data to immediately satisfy fetch.min.bytes. The default is 500ms. This prevents consumers from constantly polling when there's little data available, reducing CPU usage and network overhead. It's a trade-off between latency (how quickly consumers see new data) and efficiency.

### 68. What is the log cleaner in Kafka?
   a. A tool for deleting all logs
   b. A background process that performs log compaction
   c. A consumer that reads and discards messages
   d. A monitoring tool

Ans: b

Explanation: The log cleaner is a pool of background threads that perform log compaction on partitions configured with cleanup.policy=compact. It ensures that the log contains at least the last known value for each message key, removing old values. The cleaner works on inactive segments, merging them while preserving the latest value for each key. This is essential for maintaining compacted topics used in change data capture and maintaining table-like data.

### 69. What is the purpose of group.id configuration?
   a. To set the broker ID
   b. To uniquely identify the consumer group to which a consumer belongs
   c. To set the partition ID
   d. To define the topic name

Ans: b

Explanation: The group.id configuration is a unique string that identifies the consumer group to which a consumer belongs. All consumers with the same group.id are part of the same consumer group and will coordinate to consume from the subscribed topics, with each partition assigned to exactly one consumer in the group. Different group IDs allow independent consumption of the same topics.

### 70. What is the purpose of client.id configuration?
   a. To authenticate clients
   b. A logical identifier for the client application used in logging and metrics
   c. To set the consumer group
   d. To define partition assignment

Ans: b

Explanation: The client.id configuration is a logical name for the client application used in logging, metrics, and quotas. While not required to be unique, it's helpful for identifying different applications in monitoring tools. The broker includes this ID in logs and metrics, making it easier to track down issues or identify which clients are consuming resources. It doesn't affect functionality but is valuable for operations.

## Advanced Questions (71-100)

### 71. What is KRaft mode in Kafka?
   a. A compression algorithm
   b. Kafka's new consensus protocol that removes ZooKeeper dependency
   c. A consumer group protocol
   d. A partition strategy

Ans: b

Explanation: KRaft (Kafka Raft) is Kafka's new consensus protocol that eliminates the dependency on ZooKeeper for metadata management. Instead of using ZooKeeper, Kafka brokers use the Raft consensus algorithm to manage cluster metadata and leader election. This simplifies deployment, improves scalability (supporting more partitions), reduces operational complexity, and provides faster controller failover. KRaft is production-ready as of Kafka 3.3.

### 72. What is the exactly-once semantics (EOS) in Kafka?
   a. Messages are sent once without acknowledgment
   b. A guarantee that messages are processed exactly once, without loss or duplication
   c. A compression setting
   d. A partition strategy

Ans: b

Explanation: Exactly-once semantics (EOS) ensures that messages are processed exactly once across the entire stream processing pipeline, from producer to consumer, without loss or duplication. This is achieved through idempotent producers (preventing duplicates on retry), transactions (atomic writes across partitions), and transactional consumers (reading only committed data). EOS requires enable.idempotence=true, transactional.id configuration, and isolation.level=read_committed for consumers.

### 73. What is the difference between KTable and KStream in Kafka Streams?
   a. They are the same
   b. KStream represents an event stream; KTable represents a changelog stream (table)
   c. KTable is faster
   d. KStream is deprecated

Ans: b

Explanation: In Kafka Streams, KStream represents an unbounded stream of events where each record is an independent fact. KTable represents a changelog stream that is interpreted as a table, where each record is an update to the table (upsert). KTable maintains the latest value for each key. Aggregations on KStream produce KTable. Understanding the difference is crucial for choosing the right abstraction for your stream processing logic.

### 74. What is a GlobalKTable in Kafka Streams?
   a. A distributed table
   b. A fully replicated table available on all application instances
   c. A temporary table
   d. A partitioned table

Ans: b

Explanation: A GlobalKTable is a fully replicated table where each application instance maintains a complete copy of the entire table, regardless of partitioning. Unlike KTable (which is partitioned), GlobalKTable allows joins with KStream without requiring co-partitioning. This is useful for small reference data that needs to be available everywhere, but it increases memory usage and replication overhead. Use GlobalKTable judiciously for relatively small datasets.

### 75. What is the purpose of processing.guarantee configuration in Kafka Streams?
   a. To set producer guarantees
   b. To configure the processing semantics (at_least_once or exactly_once)
   c. To define consumer timeouts
   d. To control partition replication

Ans: b

Explanation: The processing.guarantee configuration in Kafka Streams determines the processing semantics. Values are "at_least_once" (default, faster but may duplicate results) and "exactly_once" or "exactly_once_v2" (slower but guarantees no duplicates or data loss). When set to exactly_once, Kafka Streams uses transactions to ensure that processing and state updates are atomic, and output records are written exactly once.

### 76. What is the purpose of state stores in Kafka Streams?
   a. To store broker configurations
   b. To maintain local state for stream processing operations like aggregations and joins
   c. To backup topics
   d. To cache consumer offsets

Ans: b

Explanation: State stores are key-value stores maintained by Kafka Streams applications to store intermediate state for operations like aggregations, joins, and windowing. They can be persistent (backed by RocksDB and changelog topics) or in-memory. Changelog topics provide fault tolerance by replicating state changes to Kafka. State stores enable stateful stream processing while maintaining fault tolerance and scalability.

### 77. What is windowing in Kafka Streams?
   a. A UI component
   b. Grouping records into time-based or session-based windows for aggregation
   c. A partition strategy
   d. A compression technique

Ans: b

Explanation: Windowing in Kafka Streams allows grouping records by time intervals for time-based aggregations. Types include: tumbling windows (fixed, non-overlapping), hopping windows (fixed, overlapping), sliding windows (based on record timestamps), and session windows (dynamically sized based on inactivity gaps). Windows are essential for computing time-based metrics like counts, sums, or averages over specific time periods in streaming applications.

### 78. What is the purpose of num.standby.replicas in Kafka Streams?
   a. To set broker count
   b. To configure the number of standby replicas for state stores
   c. To define partition replicas
   d. To set consumer instances

Ans: b

Explanation: The num.standby.replicas configuration in Kafka Streams specifies how many standby replicas to maintain for each state store. Standby replicas are passive copies of state stores on different application instances that stay up-to-date with the active task. When a failure occurs, a standby can quickly become active without rebuilding state from scratch, reducing recovery time. The default is 0 (no standbys), but setting it to 1 or more improves availability.

### 79. What is interactive queries in Kafka Streams?
   a. SQL queries on Kafka
   b. The ability to query state stores directly from outside the Streams application
   c. A monitoring tool
   d. A REST API generator

Ans: b

Explanation: Interactive queries allow external applications to directly query the state stores maintained by Kafka Streams applications. This enables building applications that combine stream processing with real-time queries without needing an external database. The Streams application exposes state stores through its API, allowing queries like range scans and point lookups. This is powerful for building responsive applications with low-latency data access.

### 80. What is the purpose of commit.interval.ms in Kafka Streams?
   a. To set producer commit frequency
   b. To control how often to commit the position of processors
   c. To define log retention
   d. To set rebalance interval

Ans: b

Explanation: The commit.interval.ms configuration in Kafka Streams controls how frequently to save the position of the processor. Committing positions and state store flushes happen at this interval. A lower value provides stronger guarantees (less reprocessing on failure) but may impact performance. A higher value improves throughput but means more data might be reprocessed after a failure. The default is 30 seconds, balancing performance and recovery.

### 81. What is the difference between stateless and stateful operations in Kafka Streams?
   a. There is no difference
   b. Stateless operations don't require maintaining state; stateful operations require state stores
   c. Stateless operations are faster always
   d. Stateful operations don't use memory

Ans: b

Explanation: Stateless operations (like filter, map, flatMap) process each record independently without maintaining state or memory of previous records. Stateful operations (like aggregate, reduce, join, windowing) require maintaining state in state stores, which adds complexity but enables more sophisticated processing. Stateful operations need changelog topics for fault tolerance and can be resource-intensive. Choosing between them depends on your processing requirements.

### 82. What is cooperative rebalancing (incremental rebalancing)?
   a. A broker coordination protocol
   b. A rebalancing strategy that minimizes work stoppage by incrementally reassigning partitions
   c. A partition deletion strategy
   d. A compression technique

Ans: b

Explanation: Cooperative rebalancing (introduced in Kafka 2.4) is an improvement over the eager rebalancing protocol. Instead of stopping all consumers, revoking all partitions, and reassigning everything, cooperative rebalancing only revokes and reassigns the partitions that need to move. This significantly reduces the rebalancing impact on processing. It's used with CooperativeStickyAssignor and requires all consumers in the group to support it.

### 83. What is the purpose of transactional.id in producer?
   a. To identify the database transaction
   b. To enable transactional writes and ensure idempotence across producer sessions
   c. To set the consumer group ID
   d. To identify the broker

Ans: b

Explanation: The transactional.id is a unique identifier for a producer that enables transactional writes and ensures idempotence across producer sessions (even after restarts). With a transactional ID, Kafka can determine if records from failed transactions should be aborted. Each transactional.id should be unique to a logical producer. This is essential for exactly-once semantics, as it allows Kafka to fence out zombie producers and prevent duplicate writes.

### 84. What is producer fencing?
   a. A security mechanism
   b. A mechanism to prevent zombie producers from writing duplicate data
   c. A network isolation technique
   d. A partition strategy

Ans: b

Explanation: Producer fencing is a mechanism that prevents old producer instances (zombie producers) from writing data when a new instance with the same transactional.id starts. When a new producer with a transactional ID is initialized, Kafka increments the producer epoch. Any writes from producers with older epochs are rejected. This ensures that only one producer instance can write with a given transactional ID at a time, preventing duplicates in failure scenarios.

### 85. What is the purpose of max.block.ms configuration?
   a. To set consumer timeout
   b. To control how long send() and partitionsFor() will block when buffer is full
   c. To define partition count
   d. To set rebalance timeout

Ans: b

Explanation: The max.block.ms configuration controls how long the producer's send() and partitionsFor() methods will block when the buffer is full or metadata is unavailable. If the buffer fills up faster than data can be sent to brokers, send() will block for this duration before throwing an exception. The default is 60 seconds. This prevents indefinite blocking and allows applications to handle backpressure appropriately.

### 86. What is the difference between message.max.bytes and replica.fetch.max.bytes?
   a. They are identical
   b. message.max.bytes limits incoming message size; replica.fetch.max.bytes limits replica fetch size
   c. Only message.max.bytes exists
   d. They control compression types

Ans: b

Explanation: message.max.bytes (broker config) controls the maximum size of messages the broker will accept from producers. replica.fetch.max.bytes controls the maximum size of data that a replica broker can fetch in a single request from the leader. For proper replication, replica.fetch.max.bytes should be larger than message.max.bytes to ensure the largest messages can be replicated. Mismatched settings can cause replication failures.

### 87. What is the purpose of log.cleanup.policy?
   a. To delete all logs
   b. To control whether old segments are deleted or compacted (delete, compact, or both)
   c. To compress logs
   d. To backup logs

Ans: b

Explanation: The log.cleanup.policy configuration determines how old log segments are handled. Values include: "delete" (delete old segments based on time or size retention), "compact" (compact the log to retain only the latest value for each key), or "compact,delete" (compact first, then delete old compacted segments). The policy can be set at broker or topic level. Choosing the right policy depends on whether you need full event history or just latest state.

### 88. What is the purpose of log.flush.interval.messages and log.flush.interval.ms?
   a. To control producer flush
   b. To control when Kafka forces fsync to disk
   c. To set consumer offset commits
   d. To define replication lag

Ans: b

Explanation: These configurations control when Kafka forces an fsync to disk: log.flush.interval.messages (after N messages) or log.flush.interval.ms (after time interval). However, Kafka generally relies on the OS page cache and replication for durability, so it's recommended to leave these unset and let the OS handle flushing. Explicitly flushing can reduce throughput significantly. Replication provides better durability guarantees than frequent fsync.

### 89. What is the quotas API in Kafka?
   a. A REST API for topics
   b. An API for configuring and managing client quotas dynamically
   c. A monitoring API
   d. A schema registry API

Ans: b

Explanation: The Kafka quotas API allows administrators to dynamically configure and manage quotas for clients without restarting brokers. Quotas can be set for produce rates, consume rates, and request rates at various levels (user, client-id, or combinations). The API provides methods to set, describe, and delete quota configurations. This enables runtime quota management for multi-tenant environments, preventing resource starvation and ensuring fair usage.

### 90. What is the purpose of prefetch in Kafka consumers?
   a. To predict future messages
   b. To fetch records in advance to reduce latency
   c. To validate schemas
   d. To compress data

Ans: b

Explanation: Prefetching is the mechanism where consumers fetch records from brokers before the application calls poll(), keeping them in local buffers. This reduces the perceived latency of poll() calls. Configurations like fetch.min.bytes, fetch.max.wait.ms, and max.partition.fetch.bytes control prefetching behavior. While prefetching improves throughput and reduces latency, it increases memory usage and may fetch more data than needed if processing is slow.

### 91. What is the purpose of log.message.timestamp.type?
   a. To set time zone
   b. To specify whether to use CreateTime or LogAppendTime for message timestamps
   c. To format timestamps
   d. To sync broker clocks

Ans: b

Explanation: The log.message.timestamp.type configuration determines the timestamp used for messages. Values are "CreateTime" (use timestamp set by producer, default) or "LogAppendTime" (use timestamp when broker appends the message to log). CreateTime preserves producer timing but requires producer clock synchronization. LogAppendTime provides broker-synchronized timestamps but loses original producer timing. This affects time-based operations like windowing and retention.

### 92. What is the purpose of log.index.size.max.bytes?
   a. To limit message size
   b. To control the maximum size of the offset index file for each log segment
   c. To set partition count
   d. To define buffer size

Ans: b

Explanation: The log.index.size.max.bytes configuration controls the maximum size of the offset index file for each log segment. The index maps offsets to physical file positions, enabling fast lookups. The default is 10MB. When the index reaches this size, a new log segment is rolled even if segment.bytes hasn't been reached. Larger indexes allow bigger segments and reduce file count but increase startup time and memory usage.

### 93. What is tombstone record in Kafka?
   a. An encrypted message
   b. A record with null value used to delete a key in compacted topics
   c. A large message
   d. An expired message

Ans: b

Explanation: A tombstone record is a message with a non-null key but a null value. In compacted topics, tombstones mark keys for deletion. After compaction, the tombstone itself is eventually removed (after delete.retention.ms), effectively deleting all records for that key. Tombstones are essential for maintaining compacted topics as changelog streams, allowing deletions to propagate. Without tombstones, deleted keys would reappear after compaction.

### 94. What is the purpose of controlled shutdown in Kafka?
   a. Emergency broker shutdown
   b. Graceful broker shutdown that migrates leadership before stopping
   c. Consumer shutdown
   d. Network shutdown

Ans: b

Explanation: Controlled shutdown is a mechanism that allows a broker to gracefully shut down by first migrating all partition leadership to other brokers. This minimizes unavailability during planned maintenance. When controlled.shutdown.enable=true, the shutting down broker notifies the controller, which reassigns leaders before the broker stops. This is much better than abrupt shutdown, which would cause all clients to fail over simultaneously, causing a spike in load.

### 95. What is the purpose of follower.replication.throttled.rate?
   a. To limit consumer rate
   b. To limit the rate at which follower replicas replicate data
   c. To set producer rate
   d. To control compaction rate

Ans: b

Explanation: The follower.replication.throttled.rate configuration limits the rate (bytes/sec) at which follower replicas replicate data from leaders. This is useful during partition reassignment or when adding new brokers to prevent replication from overwhelming the network or affecting client traffic. The throttle can be set per broker. It's typically used temporarily during data migration and removed afterward. There's also leader.replication.throttled.rate for controlling the leader side.

### 96. What is the purpose of principal.builder.class?
   a. To set consumer class
   b. To specify a custom class for extracting principal from client certificates for authorization
   c. To define producer class
   d. To set serializer class

Ans: b

Explanation: The principal.builder.class configuration specifies a custom class that implements PrincipalBuilder interface to extract the principal (identity) from client connections. This is used for authentication and authorization. The default implementation extracts principals from SSL certificates. Custom implementations can extract principals from other authentication mechanisms like SASL or custom headers, enabling flexible authentication integration.

### 97. What is the difference between log compaction and log deletion?
   a. They are the same
   b. Compaction retains the latest value per key; deletion removes old segments entirely
   c. Compaction is faster
   d. Deletion requires more disk space

Ans: b

Explanation: Log deletion removes entire segments based on time (retention.ms) or size (retention.bytes), discarding all data in those segments. Log compaction retains at least the latest value for each key within the partition, removing older values for the same key. Deletion is suitable for event streams where old events aren't needed. Compaction is suitable for changelog streams where you need the current state of all keys, like database change streams or caching use cases.

### 98. What is the purpose of replica.fetch.response.max.bytes?
   a. To limit consumer fetch size
   b. To limit the maximum bytes a replica can fetch in a single response from the leader
   c. To set partition size
   d. To control producer batch size

Ans: b

Explanation: The replica.fetch.response.max.bytes configuration limits the maximum bytes that can be returned in a single fetch response to a replica. This prevents a single fetch from using too much memory or bandwidth. The default is 10MB. This should be coordinated with max.message.bytes to ensure that the largest possible messages can be replicated. Setting it too low can cause replication delays for large messages.

### 99. What is the purpose of connections.max.idle.ms?
   a. To set processing timeout
   b. To close idle connections after specified milliseconds
   c. To define rebalance timeout
   d. To set consumer lag threshold

Ans: b

Explanation: The connections.max.idle.ms configuration specifies how long idle connections are kept open before being closed. The default is 9 minutes. This applies to both producer and consumer connections to brokers. Closing idle connections conserves resources but may add latency when resuming communication as new connections must be established. Setting it too low can cause frequent connection churn in bursty workloads.

### 100. What is the purpose of metric.reporters configuration?
   a. To set log level
   b. To specify classes that implement MetricReporter for publishing metrics
   c. To define consumer groups
   d. To set partition count

Ans: b

Explanation: The metric.reporters configuration specifies a list of classes implementing the MetricReporter interface that publish Kafka metrics to external monitoring systems. Kafka provides JMX metrics by default, but custom reporters can send metrics to systems like Prometheus, Datadog, or CloudWatch. Multiple reporters can be configured simultaneously. This is essential for production monitoring, allowing integration with your organization's monitoring infrastructure and enabling proactive alerting on performance and health issues.
