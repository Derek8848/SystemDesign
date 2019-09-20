
# System Design To Do List

  During the Technical Deep Dive, we will discuss your background, experience and comfort with the following topics, which are commonly encountered in the day-to-day of a Solution Architect at Elastic.

## Architecture

The challenges of building large scale distributed apps (e.g. Facebook, Twitter, eBay, Netflix), including requisite components, potential design trade-offs, and data storage options (e.g. Relational vs NoSQL).
### Netflix Architecture
![Netflix Achitecture](https://miro.medium.com/max/1997/0*Tzr9zCrDGhguxnhW)
### Load Balancing
#### Load Balancing Algorithms:  
- Least Connection Method
- l	east Response Time Method
- least Bandwidth Method
- Round Robin Method
- Weighted Round Robin Method
- IP Hash

 
### Caching
- Application Server Cache
- Content Distribution Network (CDN)
- Cache Invalidation
	- Write-through cache  
	data is written into the cache and the corresponding database at the same time
	- Write-around cache  
	This technique is similar to write through cache, but data is written directly to permanent storage, bypassing the cache
	- Write-back cache  
	data is written to cache alone and completion is immediately confirmed to the client
	 
- Cache Eviction Policies
	1. First In First Out (FIFO): The cache evicts the first block accessed first without any regard to how often or how many times it was accessed before.
	2. Last In First Out (LIFO): The cache evicts the block accessed most recently first without any regard to how often or how many times it was accessed before.
	3. Least Recently Used (LRU): Discards the least recently used items first.
	4. Most Recently Used (MRU): Discards, in contrast to LRU, the most recently used items first.
	5. Least Frequently Used (LFU): Counts how often an item is needed. Those that are used least often are discarded first.
	6. Random Replacement (RR): Randomly selects a candidate item and discards it to make space when necessary.
- Cached Database Queries
- Cached Objects
	- user sessions
	- fully rendered blog articles
	- activity streams
	- user<->friend relationships
	
### Data Partioning
- Partition Methods
	- Horizontal Partitioning  
		- Different rows in different tables
	- Vertical Partitioning
	- Directory Based Partitioning
		- create a lookup service which knows your current partitioning scheme and abstracts it away from the DB access code.
- Partition Criteria
	- Key or Hash-based Partitioning
	- List Partioning 
	- Round Robin Partitioning
	- Composite Partitioning
- Common Problem of Data Partitioning
	- Joins and Denormalization  
		- A common workaround for join table across multi-partitions is to denormalize the database so that queries that previously required joins can be performed from a single table.  
		- Cons: data inconsistency
	- Referential Integrity
		- Enforce data integrity on partitioned database can be extremely difficult
	- Rebalancing
		- The data distribution is not uniform
		- A lot of load on a partition
		- Solutions: Create more DB partitions or rebalance existing partitions
	
### Indexes
### Proxies
- Proxy Types
	- Open Proxy
		- Anonymous Proxy
		- Transparent Proxy
	- Reverse Proxy  
	


### SQL vs. NoSQL
#### SQL
- It stores data in row & columns
- MySQL, Oracle, SQLite
- Each record has fixed schema, colums must be decides before data entry, can be altered but involves modifying whole database & going offine
- It uses SQL Query
-  SQL are vertically scalable  eg: by increasing the higher memory, CPU of hardware, which can be expensive

#### NoSQL
- Schema are dynamic, column can be added on the fly & each row doesn't have to be contain each columns
- Queries are focused on a collection of documents. It's also known as UNQL(Unstructured Query Language)
- Horizontally scalable meaning we can add more servers easily. Lots of servers are distributed data server also
- Most of NoSQL sacrifice ACID compliance for performance & scalability
- Cloud based computing & storage. They are desgined to be scaled across multiple data servers
 
#### High Level differences between SQL and NoSQL

- Storage
	- SQL: Tables
	- NoSQL: Key-Value, document, graph, columnar
- Schema
	- 	
- Querying
- Scalability
- Reliability or ACID Compliancy ( Atomicity, Consistency, Isolation, Durability )

#### When to choose SQL Database
- When schema not likely to change much
- When you want to ensure ACID compliance & your data is structured & unchanging

#### When to choose NoSQL Database
- When schemas are dynamic
- When storing large volume of data with rapid development with no structure fixed
- When data need to be stored across servers in different regions
- Rapid deployment

#### NoSQL Database
- Key-Value Stores: Redis, Voldemart, Dynamo
- Document Databases: MongoDB, CouchDB
- Wide-Column database:
	- Column familites
	- Best suited for analyzing large dataset
	- Cassendra, Hbase
- Graph Database
	- Data is saved in graph structure with nodes(entities), properties & lines(Connection)
	- Neo4J, InfiniteGraph 


### CAP Theorem
CAP theorem states that it is impossible for a distributed software system to simultaneously provide more than two out of three of the following guarantees (CAP): Consistency, Availability, and Partition tolerance.

- Consistency: All nodes see the same data at the same time. .

- Availability: Every request gets a response on success/failure. .

- Partition tolerance: The system continues to work despite message loss or partial failure. A system that is partition-tolerant can sustain any amount of network failure that doesn’t result in a failure of the entire network. Data is sufficiently replicated across combinations of nodes and networks to keep the system up through intermittent outages. 

We cannot build a general data store that is continually available, sequentially consistent, and tolerant to any partition failures. We can only build a system that has any two of these three properties. Because, to be consistent, all nodes should see the same set of updates in the same order. But if the network suffers a partition, updates in one partition might not make it to the other partitions before a client reads from the out-of-date partition after having read from the up-to-date one. The only thing that can be done to cope with this possibility is to stop serving requests from the out-of-date partition, but then the service is no longer 100% available.

### ACID
- A	 Atomicity
- C Consistency
- I Isolation
- D Durability

### Redundancy and Replication


### Consistent Hashing



### Long-Polling vs WebSocket vs Server-Sent Events

 

## Distributed Systems

The benefits and challenges of distributed systems, including CAP Theorem, ACID, programming patterns like MapReduce, and other considerations in large scale distributed system design.

## Application Development / Architecture

Modern design patterns, e.g. the “12 factor” factor app, managing session state.

## Integration

Different integration approaches and patterns, schema on read vs schema on write, portable data encodings, event streams, and message queues.

## Analytics

Data storage choice and the impact on analytics, visualization, the place of machine learning.

#### Data Analytics: as the name suggests - Analysis of data i.e get a pattern from data or extract rich information from data .

A data analyst is usually the person who can do basic descriptive statistics, visualize data and communicate data points for conclusions. They must have a basic understanding of statistics, a very good sense of databases, the ability to create new views, and the perception to visualize the data. Data analytics can be referred to as the basic level of data science.



#### Machine Learning: is basically teaching a machine how to respond to a unknown input , but still produce accurate output. It also contains extracting useful inormation from DATA and then doing some mathematics on it.

Machine learning is a method of computational learning underlying most artificial intelligence (AI) applications. In ML, systems or algorithms improve themselves through data experience without relying on explicit programming. ML algorithms are wide-ranging tools capable of carrying out predictions while simultaneously learning from over trillions of observations.

Machine learning is considered a modern-day extension of predictive analytics. Efficient pattern recognition and self-learning are the backbones of ML models, which automatically evolve based on changing patterns in order to enable appropriate actions.

Machine learning can be defined as the practice of using algorithms to use data, learn from it and then forecast future trends for that topic. According to the experts from The App Solutions, traditional machine learning software comprised of statistical analysis and predictive analysis that are used to spot patterns and catch hidden insights based on perceived data. A good example of machine learning implementation is Facebook. Facebook’s machine learning algorithms gather behavioral information for every user on the social platform. Based on one’s past behavior, the algorithm predicts interests and recommends articles and notifications on the News Feed. Similarly, when Amazon recommends “You might also like” products, or when Netflix recommends a movie based on past behaviors, machine learning is at work.


### Machine Learning Algorithms:
- K-Means
- K-Nearest Neighbors (KNN)
- Linear Learner
- XGBosst
- Random Cut Forest

## Cloud

Experience with different providers, different offerings, monitoring and managing the environment, scaling, HA/DR.

## DevOps

Familiarity with CI/CD and related tools and processes, benefits vs traditional release processes.

## Security

Security considerations in architecture planning and application development, authentication and authorization, encryption, regulatory environment.

## Search

Information retrieval, search vs query, balancing relevancy and precision. 
