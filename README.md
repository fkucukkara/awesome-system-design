# Awesome System Design

A concise, Staff-level system design guide for interview preparation. Every problem follows one repeatable delivery framework, so you practice the *process*, not just the answers. It covers classic distributed systems and an **agentic track** (LLMs, RAG, agent memory, MCP, multi-agent workflows) with Azure and Microsoft Foundry mappings.

> The delivery framework is inspired by the structure popularized by [Hello Interview](https://www.hellointerview.com/learn/system-design/in-a-hurry/delivery). All content here is original.

## How to use this repo

1. Read the [Delivery Framework](01-delivery-framework/README.md) first. It is the skeleton for every answer.
2. Skim [Core Concepts](02-core-concepts/) and [Key Technologies](03-key-technologies/) until the trade-offs feel automatic.
3. Practice each [Problem Breakdown](04-problem-breakdowns/): attempt it on paper for 35 minutes, then compare.
4. For LLM and agent systems, follow the [Agentic learning path](#agentic-learning-path) and the [Agentic add-on](01-delivery-framework/README.md#agentic-add-on) to the framework.

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

### Foundations

| Concept |
|---|
| [Networking Essentials](02-core-concepts/01-foundations/networking-essentials.md) |
| [API Design](02-core-concepts/01-foundations/api-design.md) |
| [Numbers to Know](02-core-concepts/01-foundations/numbers-to-know.md) |

### Data

| Concept |
|---|
| [Data Modeling](02-core-concepts/02-data/data-modeling.md) |
| [Database Indexing](02-core-concepts/02-data/database-indexing.md) |
| [Sharding](02-core-concepts/02-data/sharding.md) |
| [Consistent Hashing](02-core-concepts/02-data/consistent-hashing.md) |
| [Replication and Consistency Models](02-core-concepts/02-data/replication-and-consistency.md) |
| [CAP Theorem](02-core-concepts/02-data/cap-theorem.md) |

### Performance and Reliability

| Concept |
|---|
| [Caching](02-core-concepts/03-performance-and-reliability/caching.md) |
| [Message Queues and Streaming](02-core-concepts/03-performance-and-reliability/message-queues-and-streaming.md) |
| [Rate Limiting, Idempotency and Retries](02-core-concepts/03-performance-and-reliability/rate-limiting-idempotency-retries.md) |
| [Observability and Reliability](02-core-concepts/03-performance-and-reliability/observability-and-reliability.md) |

### Agentic

| Concept |
|---|
| [LLM Fundamentals for System Designers](02-core-concepts/04-agentic/llm-fundamentals.md) |
| [Embeddings, Vector Search and RAG](02-core-concepts/04-agentic/embeddings-vector-search-rag.md) |
| [Agent Memory and Context Engineering](02-core-concepts/04-agentic/agent-memory-and-context-engineering.md) |
| [Tool Use, MCP and Agent Protocols](02-core-concepts/04-agentic/tool-use-mcp-and-agent-protocols.md) |
| [Agent Orchestration Patterns](02-core-concepts/04-agentic/agent-orchestration-patterns.md) |
| [Agent Pattern Decision Cheat-Sheet](02-core-concepts/04-agentic/agent-pattern-decision-cheat-sheet.md) |
| [Evaluation and Observability for LLM Systems](02-core-concepts/04-agentic/evaluation-and-observability-for-llm-systems.md) |
| [Agent Security, Safety and Guardrails](02-core-concepts/04-agentic/agent-security-safety-guardrails.md) |

## 3. Key Technologies

### Databases

| Technology | Reach for it when |
|---|---|
| [PostgreSQL](03-key-technologies/01-databases/postgresql.md) | Default relational store, transactions, rich queries |
| [Cosmos DB](03-key-technologies/01-databases/cosmos-db.md) | Managed multi-region NoSQL with tunable consistency |
| [Cassandra](03-key-technologies/01-databases/cassandra.md) | Write-heavy, always-on, wide-column workloads |
| [Vector Databases](03-key-technologies/01-databases/vector-databases.md) | Choosing pgvector, Cosmos DB, AI Search or a dedicated engine |

### Caching and Search

| Technology | Reach for it when |
|---|---|
| [Redis](03-key-technologies/02-caching-and-search/redis.md) | Sub-ms cache, counters, locks, leaderboards |
| [Elasticsearch](03-key-technologies/02-caching-and-search/elasticsearch.md) | Full-text search, faceting, log analytics |
| [Azure AI Search](03-key-technologies/02-caching-and-search/azure-ai-search.md) | Hybrid and vector search, RAG backbone, agentic retrieval |

### Messaging and Streaming

| Technology | Reach for it when |
|---|---|
| [Choosing a Messaging Technology](03-key-technologies/03-messaging-and-streaming/choosing-a-messaging-technology.md) | Decision tree and feature matrix across all five |
| [Kafka](03-key-technologies/03-messaging-and-streaming/kafka.md) | Durable ordered log, event streaming, replay |
| [RabbitMQ](03-key-technologies/03-messaging-and-streaming/rabbitmq.md) | Flexible routing, priorities, task queues, RPC |
| [Service Bus](03-key-technologies/03-messaging-and-streaming/service-bus.md) | Reliable queues, sessions, DLQ, transactions on Azure |
| [Event Hubs and Event Grid](03-key-technologies/03-messaging-and-streaming/event-hubs-event-grid.md) | Telemetry ingestion with replay; push event fan-out |

### Agentic Platform

| Technology | Reach for it when |
|---|---|
| [Microsoft Foundry](03-key-technologies/04-agentic-platform/foundry.md) | Managed agent runtime, model deployments, toolboxes, governance |
| [Agent Frameworks](03-key-technologies/04-agentic-platform/agent-frameworks.md) | Agent Framework, LangGraph, workflows vs agents |
| [Durable Orchestration](03-key-technologies/04-agentic-platform/durable-orchestration.md) | Crash-safe long-running agent runs, approvals, sagas |
| [Azure API Management AI Gateway](03-key-technologies/04-agentic-platform/azure-api-management-ai-gateway.md) | Token quotas, model load balancing, semantic cache, MCP governance |
| [Azure Container Apps](03-key-technologies/04-agentic-platform/azure-container-apps.md) | Hosting agents and MCP servers, sandboxed code execution |

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

## 5. Agentic Problem Breakdowns

Same framework plus the [Agentic add-on](01-delivery-framework/README.md#agentic-add-on). Each problem ends with an "Agentic Concerns" table (evals, guardrails, cost, latency, fallback).

| Problem | Core challenge |
|---|---|
| [Chatbot](05-agentic-problem-breakdowns/chatbot.md) | Token streaming, conversation history, tenant quotas, safety |
| [RAG Q&A System](05-agentic-problem-breakdowns/rag-qa.md) | Retrieval quality, permission-aware search, freshness, citations |
| [Agent Memory Service](05-agentic-problem-breakdowns/agent-memory-service.md) | What to remember, fast recall, forgetting, privacy |
| [MCP Platform](05-agentic-problem-breakdowns/mcp-platform.md) | Registry, gateway, OAuth and audience binding, tool rate limits |
| [Agent Runtime](05-agentic-problem-breakdowns/agent-runtime.md) | Durable runs, idempotent tools, approvals, budgets |
| [Customer Support Agent](05-agentic-problem-breakdowns/customer-support-agent.md) | Routing, safe actions, human handoff |
| [Deep Research Agent](05-agentic-problem-breakdowns/deep-research-agent.md) | Orchestrator-workers, parallel retrieval, citation integrity |

New agentic problems start from the [agentic template](05-agentic-problem-breakdowns/_template.md).

## Agentic learning path

1. Framework: [Agentic add-on](01-delivery-framework/README.md#agentic-add-on).
2. Concepts in order: [LLM Fundamentals](02-core-concepts/04-agentic/llm-fundamentals.md), [RAG](02-core-concepts/04-agentic/embeddings-vector-search-rag.md), [Memory](02-core-concepts/04-agentic/agent-memory-and-context-engineering.md), [Tools and MCP](02-core-concepts/04-agentic/tool-use-mcp-and-agent-protocols.md), [Orchestration](02-core-concepts/04-agentic/agent-orchestration-patterns.md), [Pattern Cheat-Sheet](02-core-concepts/04-agentic/agent-pattern-decision-cheat-sheet.md), [Evals](02-core-concepts/04-agentic/evaluation-and-observability-for-llm-systems.md), [Security](02-core-concepts/04-agentic/agent-security-safety-guardrails.md).
3. Technologies: [Foundry](03-key-technologies/04-agentic-platform/foundry.md), [AI Search](03-key-technologies/02-caching-and-search/azure-ai-search.md), [APIM AI Gateway](03-key-technologies/04-agentic-platform/azure-api-management-ai-gateway.md), [Vector Databases](03-key-technologies/01-databases/vector-databases.md), [Durable Orchestration](03-key-technologies/04-agentic-platform/durable-orchestration.md), [Agent Frameworks](03-key-technologies/04-agentic-platform/agent-frameworks.md), [Service Bus](03-key-technologies/03-messaging-and-streaming/service-bus.md), [Event Hubs and Event Grid](03-key-technologies/03-messaging-and-streaming/event-hubs-event-grid.md), [Container Apps](03-key-technologies/04-agentic-platform/azure-container-apps.md).
4. Problems in order: Chatbot, RAG Q&A, Agent Memory, MCP Platform, Agent Runtime, Customer Support Agent, Deep Research Agent.
