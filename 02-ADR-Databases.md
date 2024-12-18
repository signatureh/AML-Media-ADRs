---
# Configuration for the Jekyll template "Just the Docs"
parent: Decisions
nav_order: 2
title: Database Choice


status: proposed
date: 07/12/24
decision-makers: {Harvey Spencer, Ethan Hemingway, James Kerridge, Tasnim Begum}
consulted: {Soumya Basu & Chris Bates}
informed: {Soumya Basu & Chris Bates}
---

# {Cloud Computing & Dealing with scalability in large data sets}

## Context and Problem Statement

{Originally, the decision was to use a cloud database for scalability and centralized data management across multiple geographical locations. However, after further evaluation, the team has decided to switch from a cloud-based database to CouchDB, a NoSQL database that provides a more flexible solution for distributed systems. This change reflects a need for improved offline capabilities, simplified replication across locations, and a design optimized for scalability in a library system with expected annual growth of 10%.

}

<!-- This is an optional element. Feel free to remove. -->
## Decision Drivers

* {decision driver 1, Scalability: CouchDB’s NoSQL design enables easy horizontal scaling and replication.}
* {decision driver 2, Data Synchronization: CouchDB’s built-in replication protocol ensures seamless synchronization across distributed systems.}
* {decision driver 3, The database must handle large library collections and user requests without significant performance degradation.}

## Considered Options

* {CouchDB}
* {MongoDB}
* {Amazon DynamoDB}
* {PostgreSQL}


## Decision Outcome

Chosen option: {"CouchDB", because it offers a NoSQL architecture with document-based storage and built-in replication, aligning well with the distributed nature of the AML library system.

CouchDB’s focus on consistency and replication simplifies managing geographically distributed data. It provides robust performance and flexibility while reducing dependency on always-online cloud infrastructure.}

### Consequences

* Good, because {CouchDB uses a document based NoSQL model, making it easy to store and query JSON documents, this is ideal for library data and user records}
* Good, because {CouchDB offers built in replication to ensure syncronisation between branches even during network downtime}
* Bad, because {Complex querying may require additional processing power compared to relational databases, especially as the program grows larger}



### Confirmation

{Initially, cloud databases such as MongoDB, Amazon DynamoDB, and PostgreSQL were considered for their centralization and management capabilities. However, the decision to switch to CouchDB was driven by the need for a system optimized for geographically distributed operations and offline-first functionality. Unlike managed cloud databases, CouchDB’s replication and synchronization capabilities align better with the requirements of a distributed library system.}


## Pros and Cons of the Options

### {CouchDB}

<!-- This is an optional element. Feel free to remove. -->
{CouchDB | CouchDB is a NoSQL document database optimized for distributed and offline-first systems.| https://couchdb.apache.org/}

* Good, because {Schema-less document storage makes it ideal for dynamic data structures.}
* Good, because {Seamlessly synchronizes data across distributed locations}
* Bad, because {Updates take time to propagate, which may not suit systems requiring immediate consistency.}
* Bad, because {Large-scale replication setups may demand expertise to optimize effectively.}

### {Amazon DynamoDB}
{Amazon DynamoDB | DynamoDB is a serverless database designed for high throughput and low-latency workloads.  https://aws.amazon.com/dynamodb/}
* Good, because {Automatically scales to handle variable workloads with no manual intervention.}
* Good, because {Optimized for fast read/write operations under heavy loads.}
* Good, because {RoseDB can efficiently handle large data sets and can even exceed available RAM without significant performance loss.}
* Neutral, because {Pricing can become unpredictable in high-throughput environments.}
* Bad, because {Cannot operate offline, limiting its utility in distributed systems requiring local data access.}

### {Rosedb}

{Rosedb | rosedb is a lightweight storage engine written entirely in Go. It is a simple, non relational database that only stores data as key-value pairs. | [pointer to more information](https://rosedblabs.github.io/)}

* Good, because {Rosedb is written entirely in Go, making it extremely lightweight and easy to embed into Go applications such as ours.}
* Good, because {Rosedb has an append only and write once design which ensures fast crash recovery with minimal data loss.}
* Good, because {RoseDB can efficiently handle large data sets and can even exceed available RAM without significant performance loss.}
* Neutral, because {The focus on simplicity may make the database easier to develop and maintain, but it may also limit its ability to adapt to changing requirements}
* Bad, because {RoseDB is designed to only store simple key-value pairs meaning that the data complexity stored can only be low}

### {PostgreSQL}

{PostgreSQL | PostgreSQL is a powerful, open-source relational database with support for hybrid relational and JSON workloads. | https://www.postgresql.org/docs/}
* Good, because {Hybrid querying is possible using relational SQL and document JSON queries}
* Good, because {Extensive tooling, extensions, and community support.}
* Good, because {Can be deployed as a managed cloud service for scalability.}
* Bad, because {Advanced configurations for scaling and replication can be time-consuming.}
* Bad, because {Requires structured schemas which can pose challenges during iterative development}
<!-- This is an optional element. Feel free to remove. -->

### {References}
* The Apache Software Foundation. (2024). Apache CouchDB. Couchdb.apache.org. https://couchdb.apache.org/
* PostgreSQL: Documentation. (n.d.). Www.postgresql.org. https://www.postgresql.org/docs/
* RoseDB Labs | RoseDB. (2023). Github.io. https://rosedblabs.github.io/
* AWS. (2024). Amazon DynamoDB - Overview. Amazon Web Services, Inc. https://aws.amazon.com/dynamodb/

‌

‌
‌

‌
