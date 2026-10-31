# Numbers to Know

Order-of-magnitude figures for sanity-checking a design. Use them to decide whether you need a cache, shards or a queue, not to impress with arithmetic.

## Latency

| Operation | Approx. |
|---|---|
| L1/L2 cache or main memory reference | 1-100 ns |
| Redis/Memcached get (same AZ) | 0.2-1 ms |
| SSD random read | 0.1 ms |
| Same-region network round trip | 0.5-2 ms |
| Simple indexed DB query | 1-10 ms (budget 30-50 ms under load) |
| HDD seek | 10 ms |
| Cross-region round trip | 50-150 ms |
| Mobile network RTT | 50-200 ms |

## Throughput per single node (rough)

| Component | Capacity |
|---|---|
| Web/app server | 1k-10k RPS for simple requests |
| Redis | 100k+ ops/s |
| PostgreSQL / MySQL | 5k-20k simple QPS, a few thousand writes/s |
| Cassandra node | 10k-50k writes/s |
| Kafka broker | 100s of MB/s, 100k+ msgs/s per broker |
| Elasticsearch node | 1k-5k queries/s, depends heavily on query |

## Capacity

| Item | Approx. |
|---|---|
| Single DB node data | up to 1-5 TB comfortably |
| Redis node memory | 10s of GB up to ~100s GB |
| Object storage | effectively unlimited |
| Hot single key (row or partition) | roughly 1k-10k writes/s before contention dominates |

## Conversion shortcuts

- 1 day = ~100k seconds (86,400). So `1M requests/day` is ~12 RPS and `100M/day` is ~1.2k RPS.
- Peak is typically 2-10x average. Design for peak.
- 1 char = 1 byte (ASCII) to ~4 bytes (UTF-8 worst case). A tweet is ~300 B with metadata, an image ~200 KB-2 MB, and 1 minute of 1080p streamed video ~30-60 MB (about 5-8 Mbps).
- Powers: 2^10 = 1 KB, 2^20 = 1 MB, 2^30 = 1 GB, 2^40 = 1 TB.

## Availability

| Target | Downtime per year |
|---|---|
| 99.9% | ~8.8 hours |
| 99.99% | ~52 minutes |
| 99.999% | ~5 minutes |

Serial dependencies multiply: three 99.9% services in a chain give ~99.7%.

## How to use in an interview

1. Estimate the number that changes a decision (e.g. 1B URLs x 500 B = 500 GB: fits one node, so sharding is not needed for size).
2. Round aggressively and say assumptions out loud.
3. Compare to a single-node limit above. If you exceed it, say what you add (replicas, shards, cache, queue).
