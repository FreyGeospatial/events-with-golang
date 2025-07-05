# README

Here, I'll be working through a tutorial on golang based aorund event-driven architectures.

Tech I will be using:
- Golang
- Docker (and Docker Compose)
- Kafka

## Quick Start:

To spin up the kafka environment, run `docker compose up` in the directory containing the docker compose file.

Use `docker ps` to check that the images are running.

Assuming you have `go` already installed, `cd` to the `/publisher` directory, and run `go mod init publisher`, followed by `go mod tidy`. The `mod init` command will initialize the directory as a module, and `mod tidy` will attempt to install any 3rd party dependencies.

Then, do the same while in the `/subcriber` directory.

Run the publisher using `go run publisher.go`.

## Apache Kafka

- Distributed streaming platform used for building real-time data platforms.
- High throughput, scalable, and fault-tolerant.

Like SQS or Google Pub/Sub, Kafka has *topics* (essentially event repositories) which an event *producer* sends messages to. And like those other services, a *consumer* of a Kafka topic reads messages from a Kafka topic. Kafka also uses *partitions*, which is a log for a particular topic, where records are ordered and immutable. Kafka also makes use of an event *broker*, which is a server that stores data and serves clients.



### Other Kafka notes:

Apache ZooKeeper is a distributed coordination service that was traditionally used by Apache Kafka to manage and coordinate various aspects of the Kafka cluster. It is currently being outmoded.

#### Cluster Metadata Management

ZooKeeper kept track of Kafka brokers, topics, partitions, and leadership information.

#### Broker Registration & Discovery

Kafka brokers would register themselves with ZooKeeper so that other components could discover them.

#### Controller Election

One Kafka broker is elected as the controller, which manages leader election for partitions. ZooKeeper helped elect this controller.

#### Topic Configuration & ACLs

Configuration data like topic settings and access control lists (ACLs) were stored in ZooKeeper.

#### Failure Detection

ZooKeeper helped detect when a broker went down and notified the Kafka controller to reassign partition leaders.

#### As of Kafka 2.8+ (2021) and officially Kafka 3.3+ (2022):

Kafka started removing its dependency on ZooKeeper.

This effort is known as KRaft (Kafka Raft Metadata Mode), where Kafka uses its own internal Raft consensus protocol to manage metadata and broker coordination natively.

```golang

```