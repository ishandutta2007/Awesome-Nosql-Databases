# Awesome-Nosql-Databases

# Top NoSQL Databases Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Horizontal Scalability, Flexible Schemas & Multi-Model Support*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **NoSQL Databases**. These tools abandon the rigid table-and-row model of relational databases in favor of documents, key-value pairs, wide columns, or graphs — trading strict consistency and SQL familiarity for horizontal scale, schema flexibility, and workload-specific performance.

**Examples** include MongoDB, Apache Cassandra, Redis, Apache HBase, CouchDB, Amazon DynamoDB, Azure Cosmos DB, ScyllaDB, Couchbase, and Valkey (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, community-governed forks, and transparent consistency models — especially critical now that **Redis's 2024 license change drove community adoption toward the Valkey fork**.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **Amazon DynamoDB** — Fully managed key-value and document store with single-digit millisecond latency, automatic scaling, and deep AWS integration. **Ranked #3 in key-value stores** on DB-Engines with a score of 53.41, though its score dropped **22.49 points year-over-year** [citation:1]. **Trade-offs**: **request-based billing means traffic spikes hit the bill**, complete vendor lock-in, and query flexibility is strictly constrained by primary key design [citation:15]. **Best for AWS-native teams** with simple, stable access patterns.

- **Microsoft Azure Cosmos DB** — Globally distributed multi-model database with document, key-value, graph, and wide-column APIs. **Ranked #4 in key-value stores** (score 21.38) and **#2 in wide column stores** [citation:1][citation:4]. **Best for Azure-native applications** needing multi-region distribution and multiple data models from one service.

- **MongoDB Atlas** — Managed version of the leading document database. MongoDB tops both the **key-value store ranking (score 381.31)** and **document store ranking** on DB-Engines [citation:2][citation:3]. **Trade-offs**: **MongoDB Community is under the SSPL since 2018** — source is publicly viewable but not OSI-compliant [citation:5]. **Best for teams wanting the largest document database ecosystem** with managed operations.

- **DataStax Astra DB** — Managed Cassandra-compatible database built on the DataStax Enterprise distribution. **Best for teams wanting Cassandra's scale** without operating the cluster.

- **Couchbase Capella** — Managed Couchbase with **N1QL (SQL for JSON)** query language, giving SQL developers a familiar entry point into document modeling [citation:15]. **Best for enterprises wanting document flexibility** with SQL-like querying.

## Open-Source GitHub Projects

- **[Apache Cassandra](https://github.com/apache/cassandra)**  
  **The write-optimized wide-column giant** — Apache 2.0 licensed, **ranked #1 in wide column stores** on DB-Engines with a score of 98.86 [citation:4]. **Designed for "write never stops" workloads** — validated by Netflix, Apple, and Instagram at trillion-request scale [citation:15]. **Peer-to-peer architecture with no master node** — every node is equal, eliminating the primary bottleneck [citation:15]. **Linear scalability** (add nodes, add capacity), **tunable consistency** (choose strong or eventual per query), and **automatic cross-datacenter replication** [citation:15]. **Trade-offs**: **CQL is less expressive than MongoDB's query language** — no full-text search, weak complex aggregation, **no cross-partition joins or transactions**; **partition keys are hard to change once chosen**, front-loading modeling pressure; cluster operations and tuning are heavier than MongoDB; eventual consistency demands developer discipline [citation:15]. **Best for massive write volumes, time-series data, and globally distributed telemetry/logs** where write throughput matters more than query flexibility.

- **[MongoDB](https://github.com/mongodb/mongo)**  
  **The most popular NoSQL database overall** — tops both key-value and document store rankings on DB-Engines [citation:2][citation:3]. **Document model with per-document schema flexibility** — fields can vary across documents in the same collection [citation:10]. **Rich query API and aggregation pipeline** with `$setWindowFields` for window functions, `$densify` for missing time points, and `$dateTrunc` for time bucketing [citation:10]. **Trade-offs**: **SSPL license since 2018** — not OSI-compliant, which drives some organizations toward alternatives [citation:5]; **16MB document size limit**; **single-primary write bottleneck** [citation:15]. **Best for teams wanting the broadest document database ecosystem** with flexible schemas and familiar query patterns.

- **[Redis](https://github.com/redis/redis)**  
  **The in-memory data structure store** — **ranked #2 in key-value stores** on DB-Engines (score 158.06) [citation:2]. **Microsecond latency** with rich data structures (Sorted Sets, HyperLogLog, Streams) and mature persistence options [citation:15]. **Trade-offs**: **memory cost limits full-dataset scale**; **key-based access only, no ad-hoc queries**; **2024 license change restricted community use**, driving the Valkey fork [citation:5]. **Best for hot data layers** — sessions, caches, leaderboards, real-time counters — paired with a primary database rather than replacing it [citation:15].

- **[Apache HBase](https://github.com/apache/hbase)**  
  **The Hadoop-native wide-column store** — Apache 2.0 licensed, **ranked #3 in wide column stores** (score 18.22) [citation:4]. **Built on HDFS** with strong consistency and random read/write access to billions of rows. **Best for Hadoop-ecosystem organizations** needing random access over HDFS data.

- **[CouchDB](https://github.com/apache/couchdb)**  
  **The offline-first multi-master document database** — Apache 2.0 licensed. **Multi-master replication** — any node can write, no single-primary bottleneck. **No 16MB document limit** unlike MongoDB [citation:15]. **Built-in HTTP server** with RESTful API requiring no proprietary driver. **Pairs with PouchDB for offline-first apps** — write offline, sync automatically when connected, with automatic conflict detection and resolution [citation:15]. **Trade-offs**: **MapReduce views are less flexible and performant than modern query engines**; **smaller community and ecosystem**; **operational tooling for large deployments is thinner** [citation:15]. **Best for mobile/weak-network applications** and collaborative tools needing offline capability.

- **[ScyllaDB](https://github.com/scylladb/scylladb)**  
  **The C++ reimplementation of Cassandra** — Apache 2.0 licensed, **ranked #6 in wide column stores** (score 4.76) [citation:4]. **Shard-per-core architecture** with no JVM, delivering significantly lower latency and higher throughput than Cassandra on the same hardware. **Cassandra-compatible CQL** for drop-in migration. **Best for teams hitting Cassandra's JVM performance ceiling** but wanting to keep the CQL ecosystem.

- **[Valkey](https://github.com/valkey-io/valkey)**  
  **The community-governed Redis fork** — BSD-3-Clause licensed, **ranked #16 in key-value stores** (score 2.58) on DB-Engines [citation:2]. **Forked after Redis's 2024 license change** and now backed by the Linux Foundation. **Fully Redis-compatible** with the same data structures and commands. **The community alternative for teams avoiding Redis's license restrictions** [citation:5]. **Best for Redis workloads** where OSI-compliant licensing matters.

### Additional Strong Open-Source Options

- **RocksDB** — Embedded key-value store optimized for fast storage (SSDs). **Ranked #12 in key-value stores** (score 3.79) [citation:2]. Used as a storage engine inside many other databases. Best for embedded persistence in applications.
- **etcd** — Distributed reliable key-value store for configuration and service discovery. **Ranked #8 in key-value stores** (score 7.36) [citation:2]. The backbone of Kubernetes cluster state.
- **Apache Ignite** — In-memory key-value store with distributed caching and compute grid capabilities. **Ranked #16 in key-value stores** [citation:2].
- **Aerospike** — Multi-model document store optimized for real-time, high-throughput workloads. **Ranked #11 in key-value stores** [citation:2].
- **RavenDB** — Document database with ACID transactions and strong consistency. **Ranked #20 in document stores** [citation:3].
- **IBM Cloudant** — Managed CouchDB-compatible document store. **Ranked #17 in document stores** [citation:3].

**Frameworks for building custom systems**: Combine **MongoDB** for the broadest document database ecosystem with flexible schemas, **Apache Cassandra** for write-heavy globally distributed workloads where CQL's constraints are acceptable, **Redis or Valkey** for hot data caching and real-time counters, **CouchDB** for offline-first mobile synchronization, **ScyllaDB** for Cassandra-compatible workloads needing lower latency, and **HBase** for Hadoop-native random access — to build a NoSQL data layer tailored to your access patterns, consistency requirements, and operational maturity.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- NoSQL databases differ significantly in data model, consistency guarantees, and query expressiveness. **Cassandra's write throughput is unmatched for its class** but **CQL lacks joins, transactions, and full-text search** — partition keys are hard to change once chosen [citation:15]. **MongoDB leads in popularity** but its **SSPL license is not OSI-compliant** [citation:5], its **16MB document limit** constrains large payloads, and its **single-primary write bottleneck** limits write scale [citation:15]. **Redis is not a primary database** — it's a hot data layer whose memory cost limits full-dataset scale [citation:15]. **Valkey is the community fork** for teams avoiding Redis's 2024 license change [citation:5]. **DynamoDB's request-based billing** means traffic spikes hit the bill, and query flexibility is strictly constrained by primary key design [citation:15]. **Selecting NoSQL means knowing your access patterns before choosing a database** — the opposite of relational modeling where schemas evolve later.
- Self-hosted open-source solutions require proper cluster sizing, replication factor configuration, and monitoring of compaction and consistency latency.

---

**Made for backend engineers and architects choosing non-relational databases that match their write patterns, consistency needs, and scale targets.**
Let's make NoSQL databases more open, workload-appropriate, and license-transparent.
