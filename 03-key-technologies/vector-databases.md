# Vector Databases

Stores for embeddings with approximate nearest neighbor (ANN) search. Decide between a **vector column in a database you already run** and a **dedicated search/vector engine**. Last verified: 2026-10.

## Choosing

| Option | Strengths | Limits | Pick when |
|---|---|---|---|
| **PostgreSQL + pgvector** | Same transaction as relational data, SQL filters, HNSW and IVFFlat indexes | RAM-bound at large scale, single-node write limits | Up to ~10M vectors, strong relational filtering, one datastore |
| **Cosmos DB for NoSQL** | Vectors next to documents, `VectorDistance` in queries, `flat` (<=505 dims), `quantizedFlat` and `diskANN` (<=4096 dims), global distribution | Index needs >=1,000 vectors to quantize, RU cost, config changes need drop and re-add | Per-user or per-tenant data (memory, chat), partition-scoped search |
| **Azure AI Search** | Hybrid, semantic reranking, indexers, agentic retrieval | Not a system of record; vector index memory quotas | Document RAG at scale, see [Azure AI Search](azure-ai-search.md) |
| **Redis (vector sets / search)** | Sub-ms, doubles as semantic cache | Memory cost | Small hot sets, caches, see [Redis](redis.md) |
| **Qdrant, Weaviate, Milvus, Pinecone** | Purpose-built, rich filtering, scale-out | Another system to run or pay for | Very large or specialized workloads |

## Index types

| Index | Memory | Recall | Notes |
|---|---|---|---|
| Flat (exact) | Full vectors | 100% | Fine up to ~10^5 vectors or when filters shrink the scan |
| HNSW | High (graph + vectors) | High | Fast queries, slower builds, tune `m`, `ef_construction`, `ef_search` |
| IVF(+PQ) | Lower | Tunable | Tune `nprobe`; train on representative data |
| DiskANN | Low RAM, SSD graph | High | Billion scale; Cosmos DB `diskANN` is this family |

## Design rules

- **Filtered search**: filter on tenant, ACL, date in the index query, not after. Check recall with filters on.
- **Partitioning**: per-tenant index or partition key keeps tenant data isolated and searches small. In Cosmos DB use the partition key (such as `userId`) so search scopes to one logical partition.
- **Dimensions and precision**: fewer dims and `float16`/`int8` cut memory and RU cost with small recall loss.
- **Embedding model changes** require re-embedding and a new index; version the vector field.
- **Hybrid** (keyword + vector) beats vector alone for IDs and rare terms.
- Evaluate recall@k against an exact baseline on your data before choosing parameters.

## Failure modes

- Random vectors in tests give misleading recall; use real embeddings.
- Hot tenant dominates a shared index: isolate or shard.
- Memory pressure from HNSW: quantize or move to DiskANN-style.
- Stale vectors after document updates: upsert and delete by document ID, keep `embeddingModelVersion`.

## Interview cheat-sheet

- Say: "pgvector or Cosmos DB for per-user memory and small corpora, AI Search for document RAG with hybrid and rerank; filter inside the ANN query; version the embedding model and rebuild blue/green."
- Related: [Embeddings and RAG](../02-core-concepts/15-embeddings-vector-search-rag.md), [PostgreSQL](postgresql.md), [Cosmos DB](cosmos-db.md).
