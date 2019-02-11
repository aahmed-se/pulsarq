# Introduction

PulsarQ is a simple python job queue over apache pulsar.

This is experimental project to design a next generation job queue that builds on a tight integration with apache pulsar.

https://pulsar.apache.org/



# Motivation

Rabbit MQ type stores can work at small scales and relicatbilyt can be managed with HA clusters but only to a point.
Kafka can provide persistence and scalabilty but does not work well as a message queue.

```
One of the biggest problems with treating Kafka as a job queue is that you suffer from head-of-line blocking. Kafka doesn't expose per-message visibility/acknowledgement semantics like RabbitMQ/Redis PUSH+POP/SQS does. Each consumer group tracks offsets into the partitions of a log (aka a topic). This offset is just a number that points to a specific message in the Kafka partition. If you get stuck on message 123, you either can't proceed to 124, proceed and don't commit your offset but risk replaying 124, or skip 123.
```

https://news.ycombinator.com/item?id=12843066

Pulsar circumvents theses issues

https://streaml.io/blog/creating-work-queues-with-apache-pulsar

```
We learned before about Kafka’s high watermark acking. Pulsar supports that type of acknowledgement and another type called selective acknowledgement. Selective acknowledgement allows a consumer to only acknowledge an individual message. You can learn more about selective acknowledgement.

When it comes to work queues, selective acknowledgments really change the game. With a work queue, we’re able to acknowledge that we’ve processed just that message. To do this, we’ll use the acknowledge method.
```
