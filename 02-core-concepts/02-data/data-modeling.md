# Data Modeling

Model for your **access patterns**, not for the entities in the abstract.

## Process

1. List the queries (reads and writes) with rough frequency.
2. Pick the primary access path and the key that serves it.
3. Choose store type, then partition key, then secondary access paths.

## Relational vs NoSQL

| Pick relational (PostgreSQL) when | Pick NoSQL (Cassandra, Cosmos DB, DynamoDB) when |
|---|---|
| Multi-row transactions and constraints | Known access patterns, massive scale |
| Ad hoc queries and joins | Horizontal write scale, multi-region |
| Moderate scale (single primary plus replicas) | Latency SLAs on key lookups |

Default to relational unless you can name the reason you cannot. Most interview problems fit one Postgres cluster for a long time.

## Normalize vs denormalize

- **Normalize** for consistency and update simplicity.
- **Denormalize** for read speed: embed what is read together, copy fields you would otherwise join.
- Denormalized copies need an update path (transaction, CDC, or async job) and an accepted staleness window.

## Schema checklist per entity

- Primary key, and whether it is client-generated (UUID, ULID, Snowflake) or DB-generated.
- Partition/shard key and its cardinality; avoid hot keys.
- Timestamps, soft-delete, `version` for optimistic locking.
- Retention and archival rules.

## Key design

| Technique | Use |
|---|---|
| Composite key (`user_id`, `ts`) | Time-ordered per-user queries |
| Time-bucketed partitions | Avoid unbounded partitions |
| Sortable IDs (ULID, Snowflake) | Time ordering plus uniqueness without coordination |

## Blob data

Store large binaries in object storage; keep a row with metadata and the object key in the database.

## Gotchas

- Unbounded arrays inside one document/row grow forever; split into child records.
- One hot partition key (celebrity, current hour) beats the whole cluster.
- Changing a partition key later means a full migration; get it right early.
