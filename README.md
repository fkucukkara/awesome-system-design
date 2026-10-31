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
| 14 | [LLM Fundamentals for System Designers](02-core-concepts/14-llm-fundamentals.md) |
| 15 | [Embeddings, Vector Search and RAG](02-core-concepts/15-embeddings-vector-search-rag.md) |
| 16 | [Agent Memory and Context Engineering](02-core-concepts/16-agent-memory-and-context-engineering.md) |
| 17 | [Tool Use, MCP and Agent Protocols](02-core-concepts/17-tool-use-mcp-and-agent-protocols.md) |
| 18 | [Agent Orchestration Patterns](02-core-concepts/18-agent-orchestration-patterns.md) |
| 19 | [Agent Pattern Decision Cheat-Sheet](02-core-concepts/19-agent-pattern-decision-cheat-sheet.md) |
| 20 | [Evaluation and Observability for LLM Systems](02-core-concepts/20-evaluation-and-observability-for-llm-systems.md) |
| 21 | [Agent Security, Safety and Guardrails](02-core-concepts/21-agent-security-safety-guardrails.md) |

## 3. Key Technologies

| Technology | Reach for it when |
|---|---|
| [Redis](03-key-technologies/redis.md) | Sub-ms cache, counters, locks, leaderboards |
| [Elasticsearch](03-key-technologies/elasticsearch.md) | Full-text search, faceting, log analytics |
| [Kafka](03-key-technologies/kafka.md) | Durable ordered log, event streaming, decoupling |
| [Cosmos DB](03-key-technologies/cosmos-db.md) | Managed multi-region NoSQL with tunable consistency |
| [Cassandra](03-key-technologies/cassandra.md) | Write-heavy, always-on, wide-column workloads |
| [PostgreSQL](03-key-technologies/postgresql.md) | Default relational store, transactions, rich queries |
| [Microsoft Foundry](03-key-technologies/foundry.md) | Managed agent runtime, model deployments, toolboxes, governance |
| [Azure AI Search](03-key-technologies/azure-ai-search.md) | Hybrid and vector search, RAG backbone, agentic retrieval |
| [Azure API Management AI Gateway](03-key-technologies/azure-api-management-ai-gateway.md) | Token quotas, model load balancing, semantic cache, MCP governance |
| [Vector Databases](03-key-technologies/vector-databases.md) | Choosing pgvector, Cosmos DB, AI Search or a dedicated engine |
| [Durable Orchestration](03-key-technologies/durable-orchestration.md) | Crash-safe long-running agent runs, approvals, sagas |
| [Agent Frameworks](03-key-technologies/agent-frameworks.md) | Agent Framework, LangGraph, workflows vs agents |
| [Service Bus and Event Grid](03-key-technologies/service-bus-event-grid.md) | Reliable queues, sessions, DLQ, event fan-out for agents |
| [Azure Container Apps](03-key-technologies/azure-container-apps.md) | Hosting agents and MCP servers, sandboxed code execution |

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
2. Concepts in order: [LLM Fundamentals](02-core-concepts/14-llm-fundamentals.md), [RAG](02-core-concepts/15-embeddings-vector-search-rag.md), [Memory](02-core-concepts/16-agent-memory-and-context-engineering.md), [Tools and MCP](02-core-concepts/17-tool-use-mcp-and-agent-protocols.md), [Orchestration](02-core-concepts/18-agent-orchestration-patterns.md), [Pattern Cheat-Sheet](02-core-concepts/19-agent-pattern-decision-cheat-sheet.md), [Evals](02-core-concepts/20-evaluation-and-observability-for-llm-systems.md), [Security](02-core-concepts/21-agent-security-safety-guardrails.md).
3. Technologies: [Foundry](03-key-technologies/foundry.md), [AI Search](03-key-technologies/azure-ai-search.md), [APIM AI Gateway](03-key-technologies/azure-api-management-ai-gateway.md), [Vector Databases](03-key-technologies/vector-databases.md), [Durable Orchestration](03-key-technologies/durable-orchestration.md), [Agent Frameworks](03-key-technologies/agent-frameworks.md), [Service Bus and Event Grid](03-key-technologies/service-bus-event-grid.md), [Container Apps](03-key-technologies/azure-container-apps.md).
4. Problems in order: Chatbot, RAG Q&A, Agent Memory, MCP Platform, Agent Runtime, Customer Support Agent, Deep Research Agent.
