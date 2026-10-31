# Awesome System Design

A concise, Staff-level system design guide for interview preparation. Every problem follows one repeatable delivery framework, so you practice the *process*, not just the answers.

> The delivery framework is inspired by the structure popularized by [Hello Interview](https://www.hellointerview.com/learn/system-design/in-a-hurry/delivery). All content here is original.

## How to use this repo

1. Read the [Delivery Framework](01-delivery-framework/README.md) first. It is the skeleton for every answer.
2. Skim [Core Concepts](02-core-concepts/) and [Key Technologies](03-key-technologies/) until the trade-offs feel automatic.
3. Practice each [Problem Breakdown](04-problem-breakdowns/): attempt it on paper for 35 minutes, then compare.

## 1. Delivery Framework

| Step | Time | Output |
|---|---|---|
| Requirements | ~5 min | Top 3 functional, top 3-5 quantified non-functional |
| Core Entities | ~2 min | Nouns the system persists and exchanges |
| API | ~5 min | REST by default, identity from the auth token |
| Data Flow (optional) | ~5 min | Ordered steps for pipeline-style systems |
| High-Level Design | 10-15 min | Simple boxes that satisfy the API |
| Deep Dives | ~10 min | Harden for NFRs, bottlenecks, failures |

[Read the full framework](01-delivery-framework/README.md)

## 2. Core Concepts

| # | Concept |
|---|---|
| 1 | [Networking Essentials](02-core-concepts/01-networking-essentials.md) |
| 2 | [API Design](02-core-concepts/02-api-design.md) |
| 3 | [Data Modeling](02-core-concepts/03-data-modeling.md) |
| 4 | [Caching](02-core-concepts/04-caching.md) |
| 5 | [Sharding](02-core-concepts/05-sharding.md) |
| 6 | [Consistent Hashing](02-core-concepts/06-consistent-hashing.md) |
| 7 | [CAP Theorem](02-core-concepts/07-cap-theorem.md) |
| 8 | [Database Indexing](02-core-concepts/08-database-indexing.md) |
| 9 | [Numbers to Know](02-core-concepts/09-numbers-to-know.md) |
| 10 | [Replication and Consistency Models](02-core-concepts/10-replication-and-consistency.md) |
| 11 | [Message Queues and Streaming](02-core-concepts/11-message-queues-and-streaming.md) |
| 12 | [Rate Limiting, Idempotency and Retries](02-core-concepts/12-rate-limiting-idempotency-retries.md) |
| 13 | [Observability and Reliability](02-core-concepts/13-observability-and-reliability.md) |

## 3. Key Technologies

| Technology | Reach for it when |
|---|---|
| [Redis](03-key-technologies/redis.md) | Sub-ms cache, counters, locks, leaderboards |
| [Elasticsearch](03-key-technologies/elasticsearch.md) | Full-text search, faceting, log analytics |
| [Kafka](03-key-technologies/kafka.md) | Durable ordered log, event streaming, decoupling |
| [Cosmos DB](03-key-technologies/cosmos-db.md) | Managed multi-region NoSQL with tunable consistency |
| [Cassandra](03-key-technologies/cassandra.md) | Write-heavy, always-on, wide-column workloads |
| [PostgreSQL](03-key-technologies/postgresql.md) | Default relational store, transactions, rich queries |

## 4. Problem Breakdowns

| Problem | Core challenge |
|---|---|
| [Bitly (URL shortener)](04-problem-breakdowns/bitly.md) | Unique short codes, 100:1 read-heavy redirects |
| [Dropbox (file sync)](04-problem-breakdowns/dropbox.md) | Large files, chunking, resumable sync |
| [Ticketmaster](04-problem-breakdowns/ticketmaster.md) | Contention on scarce inventory, flash crowds |
| [LeetCode](04-problem-breakdowns/leetcode.md) | Safe execution of untrusted code, contests |
| [WhatsApp](04-problem-breakdowns/whatsapp.md) | Real-time delivery, offline users, ordering |
| [Distributed Rate Limiter](04-problem-breakdowns/distributed-rate-limiter.md) | Shared counters at low latency |
| [YouTube](04-problem-breakdowns/youtube.md) | Upload, transcode, adaptive streaming |
| [Uber](04-problem-breakdowns/uber.md) | Geospatial matching, high write rate of locations |
| [Web Crawler](04-problem-breakdowns/web-crawler.md) | Politeness, dedup, fault-tolerant frontier |
| [News Feed](04-problem-breakdowns/news-feed.md) | Fan-out, celebrity problem, ranking latency |

New problems should start from the [template](04-problem-breakdowns/_template.md). See [CONTRIBUTING](CONTRIBUTING.md).
