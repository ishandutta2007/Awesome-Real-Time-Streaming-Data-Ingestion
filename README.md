# Awesome-Real-Time-Streaming-Data-Ingestion

## Top Real-Time Streaming Data Ingestion Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Continuous Ingestion, Change Data Capture & Self-Hosted Streaming Platforms*  

**Last updated: November 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Real-Time Streaming Data Ingestion**. These tools enable organizations to continuously capture events, database changes, and telemetry from source systems and deliver them to downstream consumers—warehouses, analytics engines, or applications—with low latency and exactly-once guarantees.



**Examples** include Snowflake Snowpipe Streaming, Confluent Cloud, Redpanda Cloud, AWS Kinesis, Azure Event Hubs, Google Cloud Pub/Sub, Decodable, Estuary, and Striim (the category leaders).



**Open-source emphasis**: Real-Time Streaming Data Ingestion is a domain where open-source tooling is **mature at the transport layer (Kafka) but fragmented at the ingestion and processing layers**. **Apache Kafka** remains the de facto standard for durable event streaming, with **Kafka 4.0 going KRaft-only** (no ZooKeeper) and **4.2 declaring share groups production-ready** for queue-style consumption . **Apache Pulsar** offers a compelling alternative with native multi-tenancy and geo-replication, but its Kafka-on-Pulsar compatibility layer was **archived in January 2024**, pushing Kafka compatibility to StreamNative's commercial products . For **Change Data Capture (CDC)**, **Debezium** is the open-source standard—it reads transaction logs directly and emits row-level change events to Kafka with sub-second latency . For teams wanting to **replace the entire stack** (Debezium + Kafka + Flink + serving DB), **RisingWave** provides a single system that ingests from databases, streams, and webhooks, processes incrementally, and serves results at 10–20ms p99 latency . The critical caveat: **managed platforms differentiate on operational simplicity**—Confluent Cloud and Redpanda Cloud handle broker management, while **Striim** offers GUI-based pipeline configuration with enterprise SLAs . Open-source requires you to own the Kafka infrastructure, schema registry, and connector operations.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-products)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[Confluent Cloud](https://www.confluent.io/)**  

  Fully managed Kafka service with Schema Registry, Kafka Connect, ksqlDB, and Stream Governance; now part of IBM following the March 2026 acquisition. The most mature managed Kafka offering with the deepest ecosystem.



- **[Redpanda Cloud](https://redpanda.com/)**  

  Managed Redpanda service with BYOC deployment options; provides Kafka-compatible API with lower operational overhead and lower latency than JVM-based Kafka. **Community Edition uses BSL 1.1** (converts to Apache 2.0 after 4 years) .



- **[Amazon Kinesis](https://aws.amazon.com/kinesis/)**  

  AWS's serverless streaming service with shard-based provisioning; strict per-shard ordering and Enhanced Fan-Out for low-latency consumers.



- **[Azure Event Hubs](https://azure.microsoft.com/en-us/products/event-hubs)**  

  Azure's event streaming platform with native Kafka protocol compatibility; **note**: Microsoft lists Kafka transactions, exactly-once semantics, and AdminClient topic management as unsupported .



- **[Google Cloud Pub/Sub](https://cloud.google.com/pubsub)**  

  Fully serverless, globally auto-sharding message queue with no partition provisioning required; strong for unpredictable traffic and zero-ops pipelines.



- **[Snowflake Snowpipe Streaming](https://docs.snowflake.com/)**  

  Continuous, low-latency data ingestion into Snowflake tables; designed for streaming use cases where data must be queryable within seconds.



- **[Decodable](https://www.decodable.co/)**  

  Managed stream processing platform built on Apache Flink; connects to Kafka, Pulsar, and other sources for real-time ETL and event-driven applications.



- **[Estuary](https://estuary.dev/)**  

  Real-time data integration platform with CDC and streaming pipelines; positions itself as a managed alternative to batch-oriented ELT tools.



- **[Striim](https://www.striim.com/)**  

  Commercial real-time data integration platform with CDC capabilities; connects to source databases, applies transformations, and delivers to Kafka, cloud warehouses, or streaming systems. **GUI-based configuration and enterprise support SLAs** differentiate it from open-source CDC tools . Pricing starts around **$50,000 annually** .



## Open-Source GitHub Projects



### Transport Layer (Event Streaming)



- **[Apache Kafka](https://github.com/apache/kafka)**  

  The foundational open-source event streaming platform (Apache 2.0); distributed, partitioned, replicated commit log. **Kafka 4.0 removed ZooKeeper entirely** (KRaft only), and **4.2 declared share groups production-ready** for queue-style consumption . The standard for durable event transport with the deepest connector ecosystem (Kafka Connect).



- **[Apache Pulsar](https://github.com/apache/pulsar)**  

  Open-source distributed pub/sub messaging and streaming platform (Apache 2.0) with **native multi-tenancy** and **separate compute/storage layers** (brokers + BookKeeper) . **Critical caveat**: Kafka-on-Pulsar compatibility was **archived in January 2024**; Kafka compatibility now requires StreamNative's commercial Ursa/KSN products . Production deployment requires **6 machines minimum** (3 metadata nodes + 3 broker/bookie nodes) . Best for multi-tenant, multi-region platforms.



- **[Redpanda](https://github.com/redpanda-data/redpanda)**  

  Kafka-compatible streaming platform written in C++ (no JVM, no ZooKeeper); provides lower latency and operational simplicity. **Community Edition uses BSL 1.1** (source-available, not OSI-approved) . **Not a drop-in replacement**—test clients, Kafka Connect connectors, and transactions before migration .



### Change Data Capture (CDC)



- **[Debezium](https://github.com/debezium/debezium)**  

  The **open-source standard for CDC** (Apache 2.0); built on Kafka Connect, reads transaction logs directly (WAL, redo log, binlog), and emits row-level change events as JSON or Avro to Kafka . **Sub-second latency** from database commit to Kafka topic . **Operational burden is high**—you manage Kafka, Kafka Connect workers, connector configurations, schema registry, and failure recovery . Best for teams with Kafka expertise wanting maximum flexibility.



- **[Flink CDC](https://github.com/ververica/flink-cdc-connectors)**  

  Streaming data integration tool for CDC from databases into Flink; alternative to Debezium for teams already using Flink for stream processing.



### Unified Streaming Stacks (Replace Kafka + Flink + Serving DB)



- **[RisingWave](https://github.com/risingwavelabs/risingwave)**  

  Open-source **event streaming platform** (Apache 2.0) that **replaces the traditional stack** (Debezium + Kafka + Flink + serving DB) with a single system . Features: **ingest from databases (native CDC), event streams (Kafka, Pulsar, Kinesis), webhooks, and batch sources**; **incremental computation** with end-to-end freshness under 100ms; **serves results at 10–20ms p99** via PostgreSQL wire protocol; **writes to Apache Iceberg** for long-term retention . **Internal state stored in object storage** (S3) for cost efficiency (~100x cheaper than RAM) . Docker Compose, Kubernetes Helm, and Operator deployment. **Best for teams wanting a single system for ingest, process, and serve**—but it is a database-like system, not a pure transport layer.



### ETL & Pipeline Tools (CDC-Adjacent)



- **[Airtruct](https://pkg.go.dev/github.com/sananguliyev/airtruct@v0.2.1)**  

  Open-source **lightweight data pipeline tool** (Apache 2.0, single binary) positioned as a self-hosted alternative to Airbyte and Fivetran . Features: **visual pipeline builder UI**, Bloblang DSL transformations, **Kafka, HTTP, AMQP, MySQL CDC, PostgreSQL sources**, coordinator/worker architecture for horizontal scaling, **MCP integration** for AI assistants . **Best for teams wanting a lightweight, self-hosted ETL tool** with CDC support—but it is ETL-focused rather than a pure streaming platform.



### Additional Strong Open-Source Options



- **kafka.do** — Kafka-compatible streaming platform on Cloudflare Workers with Durable Objects (MIT) . Uses SQLite for hot data, R2 for archives; **early-stage/experimental**—supports Kafka wire protocol but not production-grade yet.

- **Chronik** — Kafka-compatible platform with built-in SQL, full-text search, and vector search per topic . **Benchmarks withdrawn pending re-measurement**—verify before adoption.

- **SeaTunnel** — Apache incubating project for data integration with CDC support; alternative to Debezium + Kafka for teams wanting an integrated tool .



**Frameworks for building custom systems**: For **pure transport with the deepest ecosystem**, Apache Kafka (KRaft only in 4.x) . For **CDC into Kafka**, Debezium (accepting operational complexity) . For **replacing the full stack** (CDC + processing + serving), RisingWave . For **multi-tenant platforms needing geo-replication**, Apache Pulsar (accepting 6-machine minimum and no open Kafka compatibility) . For **managed Kafka without operations**, Confluent Cloud or Redpanda Cloud (BSL caveat) . No open-source project matches the **managed simplicity** of Confluent Cloud or Striim's GUI-based pipeline configuration—those are commercial advantages.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Real-time streaming ingestion platforms handling production data must comply with organizational security policies and data governance requirements; **CDC connectors require read access to database transaction logs**—scope credentials to minimum necessary permissions.

- **Open-source streaming ingestion is mature at the transport layer but requires operational investment**—Kafka and Debezium provide production-grade event transport and CDC , and RisingWave consolidates the stack . However, **managed platforms differentiate on operational simplicity**—Confluent Cloud handles broker management, and Striim offers GUI-based pipeline configuration with SLAs . **Redpanda Community Edition uses BSL 1.1** (source-available, not OSI-approved) . **Pulsar's Kafka compatibility was archived**—verify protocol compatibility before migration .

- Verify license terms for commercial use; Kafka uses Apache 2.0, Debezium uses Apache 2.0, RisingWave uses Apache 2.0, and Redpanda Community uses BSL 1.1 .



---



**Made for data engineers, platform teams, and organizations building real-time data pipelines.**  

Let's make streaming data ingestion more open, but with clear eyes about the operational complexity and licensing trade-offs that define each path.
