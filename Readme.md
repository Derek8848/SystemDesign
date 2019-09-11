
# System Design To Do List

  During the Technical Deep Dive, we will discuss your background, experience and comfort with the following topics, which are commonly encountered in the day-to-day of a Solution Architect at Elastic.

## Architecture

The challenges of building large scale distributed apps (e.g. Facebook, Twitter, eBay, Netflix), including requisite components, potential design trade-offs, and data storage options (e.g. Relational vs NoSQL).
### Netflix Architecture
![Netflix Achitecture](https://miro.medium.com/max/1997/0*Tzr9zCrDGhguxnhW)
### Load Balancing	
### Caching
- Cached Database Queries
- Cached Objects
	- user sessions
	- fully rendered blog articles
	- activity streams
	- user<->friend relationships
	
### Data Partioning
### Indexes
### Proxies
### Redundancy and Replication
### SQL vs. NoSQL
### CAP Theorem
### Consistent Hashing
### Long-Polling vs WebSocket vs Server-Sent Events


### SQL
- It stores data in row & columns
- MySQL, Oracle, SQLite
- Each record has fixed schema, colums must be decides before data entry, can be altered but involves modifying whole database & going offine
- It uses SQL Query
-  SQL are vertically scalable  eg: by increasing the higher memory, CPU of hardware, which can be expensive

### NoSQL
- Schema are dynamic, column can be added on the fly & each row doesn't have to be contain each columns
- Queries are focused on a collection of documents. It's also known as UNQL(Unstructured Query Language)
- Horizontally scalable meaning we can add more servers easily. Lots of servers are distributed data server also
- Most of NoSQL sacrifice ACID compliance for performance & scalability
- Cloud based computing & storage. They are desgined to be scaled across multiple data servers

### NoSQL Database
- Key-Value Stores: Redis, Voldemart, Dynamo
- Document Databases: MongoDB, CouchDB
- Wide-Column database:
	- Column familites
	- Best suited for analyzing large dataset
	- Cassendra, Hbase
- Graph Database
	- Data is saved in graph structure with nodes(entities), properties & lines(Connection)
	- Neo4J, InfiniteGraph  

#### When to choose SQL Database
- When schema not likely to change much
- When you want to ensure ACID compliance & your data is structured & unchanging

#### When to choose NoSQL Database
- When schemas are dynamic
- When storing large volume of data with rapid development with no structure fixed
- When data need to be stored across servers in different regions.

 

## Distributed Systems

The benefits and challenges of distributed systems, including CAP Theorem, ACID, programming patterns like MapReduce, and other considerations in large scale distributed system design.

## Application Development / Architecture

Modern design patterns, e.g. the “12 factor” factor app, managing session state.

## Integration

Different integration approaches and patterns, schema on read vs schema on write, portable data encodings, event streams, and message queues.

## Analytics

Data storage choice and the impact on analytics, visualization, the place of machine learning.

## Cloud

Experience with different providers, different offerings, monitoring and managing the environment, scaling, HA/DR.

## DevOps

Familiarity with CI/CD and related tools and processes, benefits vs traditional release processes.

## Security

Security considerations in architecture planning and application development, authentication and authorization, encryption, regulatory environment.

## Search

Information retrieval, search vs query, balancing relevancy and precision. 
