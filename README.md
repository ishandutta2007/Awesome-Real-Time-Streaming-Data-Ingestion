# Awesome Real-Time Streaming Data Ingestion [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of leading SaaS products, continuous ingestion platforms, Change Data Capture (CDC) systems, and open-source real-time streaming data ingestion frameworks.

Streaming data ingestion systems capture, transport, and load high-velocity event streams, transaction logs (CDC), telemetry, and time-series data into warehouses, data lakes, and real-time analytical engines with sub-second latencies and strict ordering or delivery guarantees.

---

## Table of Contents

- [Sector Overview & Market Dynamics](#sector-overview--market-dynamics)
- [SaaS & Managed Cloud Platforms](#saas--managed-cloud-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
  - [Top Projects Ranked by Community Stars](#top-projects-ranked-by-community-stars)
  - [Architectural Roles & Ecosystem Breakdown](#architectural-roles--ecosystem-breakdown)
- [How to Contribute](#how-to-contribute)
- [Disclaimer & License Notes](#disclaimer--license-notes)

---

## Sector Overview & Market Dynamics

The global real-time streaming data ingestion and event stream processing (ESP) market is estimated at **$53.2 billion in 2026** (with the broader streaming analytics and data ingestion pipeline market projected to exceed **$440 billion by 2035** at a CAGR of ~26.6%). 

The sector exhibits **moderate concentration with a bifurcated dynamic**: foundational cloud transport is dominated by hyperscalers (AWS, Microsoft, Google Cloud) and enterprise streaming vendors (IBM/Confluent), while specialized change data capture (CDC), serverless stream routing, and unified ingest-and-serve layers remain fragmented across specialized innovators (Redpanda, Decodable, Estuary, Striim).

---

## SaaS & Managed Cloud Platforms

The table below lists top SaaS and managed streaming ingestion platforms, sorted in descending order by company scale (market capitalization, parent enterprise valuation, or private market valuation).

| Platform | Company Valuation / Revenue Scale | Starting Tier Pricing | Free Tier Limits / Free Trial Specifications | Primary Ingestion Focus |
|:---|:---|:---|:---|:---|
| **[Microsoft Azure Event Hubs](https://azure.microsoft.com/en-us/products/event-hubs)** | **~$3.1 Trillion** (Market Cap) | **$0.015/hour** per Throughput Unit + **$0.028 per million events** (Basic tier) | **Free evaluation:** Azure $200 free credit valid for 30 days; select lightweight ingress services free within 12 months | Enterprise Kafka-compatible streaming pub/sub |
| **[Amazon Kinesis Data Streams](https://aws.amazon.com/kinesis/)** | **~$2.2 Trillion** (Amazon Market Cap) | **$0.015/hour** per shard + **$0.014 per million** PUT units (Provisioned mode; On-Demand at **$0.04/shard-hour** + **$0.08/GB**) | **AWS Free Tier:** 1 million GET records/month via Kinesis Data Streams for the first 12 months | Fully managed partitioned sharded ingestion |
| **[Google Cloud Pub/Sub](https://cloud.google.com/pubsub)** | **~$2.1 Trillion** (Alphabet Market Cap) | **$40.00 per TiB** ($0.04/GiB) for data ingestion & delivery | **Forever Free Tier:** First **10 GiB per month** of message ingestion free every month (no expiration) | Serverless global event ingestion and distribution |
| **[Snowflake Snowpipe Streaming](https://docs.snowflake.com/)** | **~$55–65 Billion** (Snowflake Market Cap) | **0.0037 Snowflake credits/GB** uncompressed data (~$7.58 to $15.15 per TB depending on Snowflake edition) | **30-Day Free Trial:** $400 in trial credits for new Snowflake accounts; Snowpipe Streaming billed against trial credits | Direct row-level low-latency streaming to Snowflake tables |
| **[Confluent Cloud](https://www.confluent.io/)** | **~$11 Billion** (IBM / Confluent Enterprise Valuation) | **$0.00/base fee**; Basic cluster usage starts at **$0.10/GB write** and **$0.10/GB read** | **30-Day Free Trial:** **$400 in promotional credits** valid for first 30 days across Kafka, connectors, and Flink | Fully managed Apache Kafka, Schema Registry & Flink |
| **[Redpanda Cloud](https://redpanda.com/)** | **$1.0 Billion** (Series D Valuation; ~$26M ARR) | **$0.00/base fee**; Serverless pay-as-you-go starts at **$0.08/GB ingress** + compute units | **30-Day Free Trial:** **$100 in free serverless credits** valid for 30 days (no credit card required upfront) | C++ Kafka-compatible engine, low latency & BYOC |
| **[Striim Cloud](https://www.striim.com/)** | **~$108M+ Funding** (~$40M–$45M ARR) | Enterprise subscriptions starting at **~$50,000/year** (or hourly pay-as-you-go marketplace starting at ~$2.50/hour) | **14-Day Free Trial:** Full access to Striim Cloud connectors and real-time CDC pipeline builder | Real-time CDC data integration & streaming ETL |
| **[Decodable](https://www.decodable.co/)** | **~$80 Million** (Series A Valuation; $25.5M Funding) | Pay-as-you-go at **$0.10 to $0.12 per credit-hour** per active task | **Forever Free Tier:** Up to **4 concurrent running tasks**, restricted to Small/Medium task sizes, 20 streams, and 24h/10 GB retention | Managed Apache Flink streaming ETL & CDC integration |
| **[Estuary Flow](https://estuary.dev/)** | **~$68 Million** (Series A Valuation; $24M Funding) | Cloud Pay-As-You-Go starts at **$0.50/GB** data moved + **$100/month** per connector (first 6 connectors) | **Forever Free Developer Tier:** **10 GB/month** data movement and up to **2 active connector instances** forever | Real-time streaming CDC & millisecond ELT pipeline |

---

## Open-Source GitHub Projects

### Top Projects Ranked by Community Stars

The following table presents open-source streaming data ingestion, CDC, and event broker frameworks ranked by GitHub stargazers count in descending order. Each star badge links directly to the repository's stargazers page.

| Project & Repo Link | GitHub Stars | Primary License | Description |
|:---|:---:|:---:|:---|
| **[Apache Kafka](https://github.com/apache/kafka)** | [![GitHub stars](https://img.shields.io/github/stars/apache/kafka?style=social&color=white)](https://github.com/apache/kafka/stargazers) | Apache-2.0 | De facto standard distributed event streaming platform and partitioned append-only commit log (KRaft-only architecture in Kafka 4.x). |
| **[Apache Flink](https://github.com/apache/flink)** | [![GitHub stars](https://img.shields.io/github/stars/apache/flink?style=social&color=white)](https://github.com/apache/flink/stargazers) | Apache-2.0 | High-throughput, low-latency stateful stream processing framework providing event-driven continuous ingestion and exact-once semantics. |
| **[Vector](https://github.com/vectordotdev/vector)** | [![GitHub stars](https://img.shields.io/github/stars/vectordotdev/vector?style=social&color=white)](https://github.com/vectordotdev/vector/stargazers) | MPL-2.0 | High-performance, lightweight observability and streaming data collector/shipper built in Rust for high-throughput log and telemetry ingestion. |
| **[Airbyte](https://github.com/airbytehq/airbyte)** | [![GitHub stars](https://img.shields.io/github/stars/airbytehq/airbyte?style=social&color=white)](https://github.com/airbytehq/airbyte/stargazers) | Elv2 / MIT | Open-source data movement engine supporting 300+ database and API connectors with incremental log-based CDC streaming. |
| **[Apache Pulsar](https://github.com/apache/pulsar)** | [![GitHub stars](https://img.shields.io/github/stars/apache/pulsar?style=social&color=white)](https://github.com/apache/pulsar/stargazers) | Apache-2.0 | Multi-tenant distributed pub-sub messaging system decoupling serving brokers from durable BookKeeper segment storage. |
| **[Debezium](https://github.com/debezium/debezium)** | [![GitHub stars](https://img.shields.io/github/stars/debezium/debezium?style=social&color=white)](https://github.com/debezium/debezium/stargazers) | Apache-2.0 | The open-source standard for Change Data Capture (CDC), streaming row-level database WAL/binlog mutations into Kafka topics in sub-second latency. |
| **[Redpanda](https://github.com/redpanda-data/redpanda)** | [![GitHub stars](https://img.shields.io/github/stars/redpanda-data/redpanda?style=social&color=white)](https://github.com/redpanda-data/redpanda/stargazers) | BSL 1.1 | C++ Kafka-compatible streaming engine operating without JVM or ZooKeeper, designed for mission-critical sub-millisecond p99 latency. |
| **[Apache SeaTunnel](https://github.com/apache/seatunnel)** | [![GitHub stars](https://img.shields.io/github/stars/apache/seatunnel?style=social&color=white)](https://github.com/apache/seatunnel/stargazers) | Apache-2.0 | Next-generation ultra-high-performance distributed data integration tool supporting real-time CDC synchronization across 100+ connectors. |
| **[RisingWave](https://github.com/risingwavelabs/risingwave)** | [![GitHub stars](https://img.shields.io/github/stars/risingwavelabs/risingwave?style=social&color=white)](https://github.com/risingwavelabs/risingwave/stargazers) | Apache-2.0 | Unified streaming database that continuously ingests from CDC, Kafka, and streams, performs incremental materialized views, and serves low-latency SQL. |
| **[Redpanda Connect (formerly Benthos)](https://github.com/redpanda-data/connect)** | [![GitHub stars](https://img.shields.io/github/stars/redpanda-data/connect?style=social&color=white)](https://github.com/redpanda-data/connect/stargazers) | MIT | Resilient, high-performance stream processing engine (Go) featuring declarative pipeline definitions, buffer management, and 200+ connectors. |
| **[Fluent Bit](https://github.com/fluent/fluent-bit)** | [![GitHub stars](https://img.shields.io/github/stars/fluent/fluent-bit?style=social&color=white)](https://github.com/fluent/fluent-bit/stargazers) | Apache-2.0 | Ultra-lightweight, super-fast streaming telemetry agent (C) collecting, filtering, and shipping millions of event records per second. |
| **[Flink CDC](https://github.com/apache/flink-cdc)** | [![GitHub stars](https://img.shields.io/github/stars/apache/flink-cdc?style=social&color=white)](https://github.com/apache/flink-cdc/stargazers) | Apache-2.0 | Integrated streaming CDC framework for Apache Flink supporting concurrent snapshot reading, schema evolution, and full-database pipeline sync. |
| **[Apache NiFi](https://github.com/apache/nifi)** | [![GitHub stars](https://img.shields.io/github/stars/apache/nifi?style=social&color=white)](https://github.com/apache/nifi/stargazers) | Apache-2.0 | Visual dataflow orchestration and streaming ingestion platform with data provenance tracking, backpressure management, and protocol mediation. |
| **[Apache Pinot](https://github.com/apache/pinot)** | [![GitHub stars](https://img.shields.io/github/stars/apache/pinot?style=social&color=white)](https://github.com/apache/pinot/stargazers) | Apache-2.0 | Real-time distributed OLAP datastore designed to ingest directly from streaming sources (Kafka, Pulsar) and execute analytical queries in milliseconds. |
| **[Memphis.dev](https://github.com/memphisdev/memphis)** | [![GitHub stars](https://img.shields.io/github/stars/memphisdev/memphis?style=social&color=white)](https://github.com/memphisdev/memphis/stargazers) | BSL 1.1 | Developer-friendly message broker and streaming data platform featuring built-in schema management, dead-letter stations, and telemetry. |
| **[Bytewax](https://github.com/bytewax/bytewax)** | [![GitHub stars](https://img.shields.io/github/stars/bytewax/bytewax?style=social&color=white)](https://github.com/bytewax/bytewax/stargazers) | Apache-2.0 | Python-native stream processing and ingestion engine powered by a Timely Dataflow Rust core, ideal for real-time ML feature ingestion. |

---

### Architectural Roles & Ecosystem Breakdown

- **Distributed Event Transport (Append-Only Logs):**
  - **[Apache Kafka](https://github.com/apache/kafka):** The enterprise benchmark for durable, partitioned, and replayable event logs. Kafka 4.x eliminates ZooKeeper completely in favor of KRaft metadata quorum.
  - **[Apache Pulsar](https://github.com/apache/pulsar):** Cloud-native tiered storage separating stateless brokers from stateful BookKeeper storage nodes.
  - **[Redpanda](https://github.com/redpanda-data/redpanda):** Engineered in C++ with thread-per-core hardware utilization, providing Kafka API compatibility with single-digit millisecond latency.

- **Change Data Capture (CDC):**
  - **[Debezium](https://github.com/debezium/debezium):** Connects to MySQL, PostgreSQL, Oracle, SQL Server, and MongoDB transaction logs to stream exact change events.
  - **[Flink CDC](https://github.com/apache/flink-cdc):** Enables lock-free parallel historical snapshots and continuous CDC binlog stream consumption directly within Apache Flink.
  - **[Apache SeaTunnel](https://github.com/apache/seatunnel):** Streamlines CDC sync pipelines with built-in connector discovery and distributed execution.

- **Unified Streaming Ingest & Serve:**
  - **[RisingWave](https://github.com/risingwavelabs/risingwave):** Eliminates complex multi-hop pipelines by fusing ingestion, stateful stream processing, and serving into a single Postgres-compatible streaming database.
  - **[Apache Pinot](https://github.com/apache/pinot):** Consumes streaming events directly into columnar segments for sub-second user-facing dashboards and real-time metrics.

- **Edge, Agents & Lightweight Stream Pipelines:**
  - **[Redpanda Connect](https://github.com/redpanda-data/connect):** Zero-dependency single-binary stream processor for transforming and routing streams between protocols.
  - **[Vector](https://github.com/vectordotdev/vector) & [Fluent Bit](https://github.com/fluent/fluent-bit):** Ultra-efficient agents deployed on edge nodes or Kubernetes pods to ingest gigabytes of logs and telemetry per second.
  - **[Bytewax](https://github.com/bytewax/bytewax):** Streamlines real-time feature extraction for AI/ML pipelines using clean Python APIs.

---

## How to Contribute

1. Fork this repository.
2. Add your SaaS product or open-source repository to `README.md` following the existing format.
3. For SaaS platforms: include verified starting tier pricing, free tier/trial limits, and company scale metrics.
4. For Open-Source repositories: ensure you include the star badge linking to the stargazers page:
   ```markdown
   [![GitHub stars](https://img.shields.io/github/stars/<owner>/<repo>?style=social&color=white)](https://github.com/<owner>/<repo>/stargazers)
   ```
5. Submit a pull request with a concise description of the addition.

---

## Disclaimer & License Notes

- This repository is a community-maintained curated index. Company market capitalizations, private valuations, and pricing tiers reflect publicly available figures as of 2026.
- Database CDC connectors require continuous log-tailing access to source engines (WAL, binlog, redo logs); ensure credentials adhere to least-privilege principles.
- Software licenses vary across projects (e.g., Apache 2.0, MPL 2.0, BSL 1.1, and Elv2). Check individual project licenses prior to enterprise deployment.
