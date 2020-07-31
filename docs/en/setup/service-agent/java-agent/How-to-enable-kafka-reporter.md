# How to enable Kafka Reporter

The Kafka reporter plugin support report traces, JVM metrics, Instance Properties, and profiled snapshots to Kafka cluster, which is disabled in default. Move the jar of the plugin from `optional-reporter-plugins` to `reporter-plugins` for activating.

Notice, currently, the agent still needs to configure GRPC receiver for delivering the task of profiling. In other words, the following configure cannot be omitted.

```properties
# Backend service addresses.
collector.backend_service=${SW_AGENT_COLLECTOR_BACKEND_SERVICES:127.0.0.1:11800}

# Kafka producer configuration
plugin.kafka.bootstrap_servers=${SW_KAFKA_BOOTSTRAP_SERVERS:localhost:9092}
plugin.kafka.producer_config[delivery.timeout.ms]=12000
```

Kafka reporter plugin support to customize all configurations of listed in [here](http://kafka.apache.org/24/documentation.html#producerconfigs).

After you activated the Kafka reporter, you need to open [Kafka fetcher](../../backend/backend-fetcher.md#kafka-fetcher) at the OAP side.