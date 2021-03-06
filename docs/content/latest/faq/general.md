---
title: General FAQ
linkTitle: General FAQ
description: General FAQ
aliases:
  - /faq/product/
menu:
  latest:
    identifier: general-faq
    parent: faq
    weight: 2710
isTocNested: false
showAsideToc: true
---

## When is YugabyteDB a good fit?

YugabyteDB is a good fit for fast-growing, cloud native applications that need to serve business-critical data reliably, with zero data loss, high availability and low latency. Common use cases include:

1. Distributed Online Transaction Processing (OLTP) applications needing multi-region scalability without compromising strong consistency and low latency. E.g. User identity, Retail product catalog, Financial data service.

2. Hybrid Transactional/Analytical Processing (HTAP), also known as Translytical, applications needing real-time analytics on transactional data. E.g User personalization, fraud detection, machine learning.

3. Streaming applications needing to efficiently ingest, analyze and store ever-growing data. E.g. IoT sensor analytics, time series metrics, real-time monitoring.

A few such use cases are detailed [here](https://www.yugabyte.com/).

## When is YugabyteDB not a good fit?

YugabyteDB is not a good fit for traditional Online Analytical Processing (OLAP) use cases that need complete ad-hoc analytics. Use an OLAP store such as [Druid](http://druid.io/druid.html) or a data warehouse such as [Snowflake](https://www.snowflake.net/).

## How many major releases YugabyteDB has had so far?

YugabyteDB has had 6 major releases.

- [v0.9 Beta](https://blog.yugabyte.com/yugabyte-has-arrived/) in November 2017
- [v1.0](https://blog.yugabyte.com/announcing-yugabyte-db-1-0-%F0%9F%8D%BE-%F0%9F%8E%89/) in May 2018
- [v1.1](https://blog.yugabyte.com/announcing-yugabyte-db-1-1-and-company-update/) in September 2018
- [v1.2](https://blog.yugabyte.com/announcing-yugabyte-db-1-2-company-update-jepsen-distributed-sql/) in March 2019
- [v1.3](https://blog.yugabyte.com/announcing-yugabyte-db-v1-3-with-enterprise-features-as-open-source/) in July 2019
- [v2.0](https://blog.yugabyte.com/announcing-yugabyte-db-2-0-ga:-jepsen-tested,-high-performance-distributed-sql/ ) in September 2019

The next major release is the v2.1 release in Winter 2020.

## Can I deploy YugabyteDB to production?

Yes, both YugabyteDB APIs are production ready. [YCQL](https://blog.yugabyte.com/yugabyte-db-1-0-a-peek-under-the-hood/) achieved this status starting with v1.0 in May 2018 while [YSQL](https://blog.yugabyte.com/announcing-yugabyte-db-2-0-ga:-jepsen-tested,-high-performance-distributed-sql/) became production ready starting v2.0 in September 2019.

## Which companies are currently using YugabyteDB in production?

Reference deployments are listed [here](https://www.yugabyte.com/all-resources/resource-parent/case-studies/).

## What is the definition of the "Beta" feature tag?

Some features are marked Beta in every release. Following are the points to consider:

- Code is well tested. Enabling the feature is considered safe. Some of these features enabled by default.

- Support for the overall feature will not be dropped, though details may change in incompatible ways in a subsequent beta or GA release. 

- Recommended only for non-production use.

Please do try our beta features and give feedback on them on our [Slack channel](https://www.yugabyte.com/slack) or by filing a [GitHub issue](https://github.com/yugabyte/yugabyte-db/issues).

## Any performance benchmarks available?

[Yahoo Cloud Serving Benchmark (YCSB)](https://github.com/brianfrankcooper/YCSB/wiki) is a popular benchmarking framework for NoSQL databases. We benchmarked Yugabyte Cloud QL (YCQL) API against standard Apache Cassandra using YCSB. YugabyteDB outperformed Apache Cassandra by increasing margins as the number of keys (data density) increased across all the 6 YCSB workload configurations. 

[Netflix Data Benchmark (NDBench)](https://github.com/Netflix/ndbench) is another publicly available, cloud-enabled benchmark tool for data store systems. We ran NDBench against YugabyteDB for 7 days and observed P99 and P995 latencies that were orders of magnitude less than that of Apache Cassandra. 

Details for both the above benchhmarks are published in [Building a Strongly Consistent Cassandra with Better Performance](https://blog.yugabyte.com/building-a-strongly-consistent-cassandra-with-better-performance-aa96b1ab51d6).

## What about correctness testing?

[Jepsen](https://jepsen.io/) is a widely used framework to evaluate databases’ behavior under different failure scenarios. It allows for a database to be run across multiple nodes, and create artificial failure scenarios, as well as verify the correctness of the system under these scenarios. YugabyteDB 1.2 passes [formal Jepsen testing](https://blog.yugabyte.com/yugabyte-db-1-2-passes-jepsen-testing/). 

## Is YugabyteDB open source?

Starting with [v1.3](https://blog.yugabyte.com/announcing-yugabyte-db-v1-3-with-enterprise-features-as-open-source/), YugabyteDB is 100% open source. It is licensed under Apache 2.0 and the source is available on [GitHub](https://github.com/yugabyte/yugabyte-db).

## How do YugabyteDB, Yugabyte Platform and Yugabyte Cloud differ from each other?

[YugabyteDB](../../quick-start/) is the 100% open source core database. It is the best choice for the startup organizations with strong technical operations expertise looking to deploy to production with traditional DevOps tools.

[Yugabyte Platform](../../deploy/enterprise-edition/) is commercial software for running a self-managed YugabyteDB-as-a-Service. It has built-in cloud native operations, enterprise-grade deployment options and world-class support. It is the simplest way to run YugabyteDB in mission-critical production environments with one or more regions (across both public cloud and on-premise data centers).

[Yugabyte Cloud](http://yugabyte.com/cloud) is Yugabyte's fully-managed cloud service on AWS and GCP. You can [sign up](https://www.yugabyte.com/cloud/) for early access now.

For a more detailed comparison between YugabyteDB and Yugabyte Platform, see [Adopt YugabyteDB Your Way
](https://www.yugabyte.com/platform/#compare-editions).

## What are the trade-offs involved in using YugabyteDB?

Trade-offs depend on the type of database used as baseline for comparison.

### Distributed SQL

Examples: Amazon Aurora, Google Cloud Spanner, CockroachDB, TiDB

**Benefits of YugabyteDB**

- Low-latency reads and high-throughput writes. 
- Cloud-neutral deployments with a Kubernetes-native database.
- 100% Apache 2.0 open source even for enterprise features.

**Trade-offs**

- None

Learn more: [What is Distributed SQL?](https://blog.yugabyte.com/what-is-distributed-sql/)

### Monolithic SQL

Examples: PostgreSQL, MySQL, Oracle, Amazon Aurora.

**Benefits of YugabyteDB**

- Scale write throughput linearly across multiple nodes and/or geographic regions. 
- Automatic failover and native repair.
- 100% Apache 2.0 open source even for enterprise features.

**Trade-offs**

- Transactions and JOINs can now span multiple nodes, thereby increasing latency.

Learn more: [Distributed PostgreSQL on a Google Spanner Architecture – Query Layer](https://blog.yugabyte.com/distributed-postgresql-on-a-google-spanner-architecture-query-layer/)

### Traditional NewSQL

Examples: Vitess, Citus

**Benefits of YugabyteDB**

- Distributed transactions across any number of nodes.
- No single point of failure given all nodes are equal.
- 100% Apache 2.0 open source even for enterprise features.

**Trade-offs**

- None

Learn more: [Rise of Globally Distributed SQL Databases – Redefining Transactional Stores for Cloud Native Era](https://blog.yugabyte.com/rise-of-globally-distributed-sql-databases-redefining-transactional-stores-for-cloud-native-era/)

### Transactional NoSQL 

Examples: MongoDB, Amazon DynamoDB, FoundationDB, Azure Cosmos DB.

**Benefits of YugabyteDB**

- Flexibility of SQL as query needs change in response to business changes.
- Distributed transactions across any number of nodes.
- Low latency, strongly consistent reads given that read-time quorum is avoided altogether.
- 100% Apache 2.0 open source even for enterprise features.

**Trade-offs**

- None

Learn more: [Why are NoSQL Databases Becoming Transactional?](https://blog.yugabyte.com/nosql-databases-becoming-transactional-mongodb-dynamodb-faunadb-cosmosdb/)

### Eventually Consistent NoSQL

Examples: Apache Cassandra, Couchbase.

**Benefits of YugabyteDB**

- Flexibility of SQL as query needs change in response to business changes.
- Strongly consistent, zero data loss writes.
- Strongly consistent as well as timeline-consistent reads without resorting to eventual consistency-related penalties such as read repairs and anti-entropy.
- 100% Apache 2.0 open source even for enterprise features.

**Trade-offs**

- Extremely short unavailability during the leader election time for all shard leaders lost during a node failure or network partition. 

Learn more: [Apache Cassandra: The Truth Behind Tunable Consistency, Lightweight Transactions & Secondary Indexes](https://blog.yugabyte.com/apache-cassandra-lightweight-transactions-secondary-indexes-tunable-consistency/)

## How does YugabyteDB compare to other SQL and NoSQL databases?

See [YugabyteDB in Comparison](../../comparisons/)

- [Google Cloud Spanner](../../comparisons/google-spanner/)
- [CockroachDB](https://www.yugabyte.com/yugabyte-db-vs-cockroachdb/)
- [MongoDB](../../comparisons/mongodb/)
- [FoundationDB](../../comparisons/foundationdb/)
- [Amazon DynamoDB](../../comparisons/amazon-dynamodb/)
- [Apache Cassandra](../../comparisons/cassandra/)
- [Azure Cosmos DB](../../comparisons/azure-cosmos/)

## What is the status of the YEDIS API?

In the near-term, Yugabyte is not actively working on new feature or driver enhancements to the [YEDIS](../../yedis/) API other than bug fixes and stability improvements. Current focus is on [YSQL](../../api/ysql) and [YCQL](../../api/ycql).

For key-value workloads that need persistence, elasticity and fault-tolerance, YCQL (with notion of keyspaces, tables, role-based access control and more) is often a great fit, especially if the application new rather than an existing one already written in Redis. The YCQL drivers are also more clustering aware, and hence YCQL is expected to perform better than YEDIS for equivalent scenarios. In general, our new feature development (support for data types, built-ins, TLS, backups and more), correctness testing (using Jepsen) and performance optimization is in the YSQL and YCQL areas.
