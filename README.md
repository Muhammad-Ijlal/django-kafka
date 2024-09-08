# Event Driven Cloud Kitchen Demo App using Kafka (WIP)
This is a basic demo project for a cloud kitchen order management. It is based on the event driven architecture with 3 microservices developed using Python Django.

https://github.com/conduktor/kafka-stack-docker-compose/tree/master

## Tidbits
### Kafka topic naming convention:

From: https://cnr.sh/essays/how-paint-bike-shed-kafka-topic-naming-conventions

`<message_type>.<dataset name>.<data name>`

**Typical message types:**
* logging:
    For logging data (slf4j, syslog, etc)
* queuing: 
    For classical queuing use cases.
* tracking: 
    For tracking events such as user clicks, page views, ad views, etc.
* etl/db:
    For ETL and CDC use cases such as database feeds.
* streaming:
    For intermediate topics created by stream processing pipelines.
* push:
    For data that’s being pushed from offline (batch computation) environments into online environments.
* user:
    For user-specific data such as scratch and test topics.

**Dataset name:**
The dataset name is analogous to a database name in traditional RDBMS systems. It’s used as a category to group topics together.

**Data name:**
The data name field is analogous to a table name in traditional RDBMS systems, though it’s fine to include further dotted notation if developers wish to impose their own hierarchy within the dataset namespace.

### Message orderign in kafka partitions

Message order is guranteed only within a partiton and not cross partitions. To ensure that a set of message are in order assign them a common key (set identifier) do they are always pushed to a specific partition hence kept in order.