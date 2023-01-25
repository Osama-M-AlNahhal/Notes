# Basics
## Scalability
*throw more money at the problem to solve it*

**2 Approaches :**
1. Horizontal Scaling : *buy more machines.*
2. Vertical Scaling : *upgrade to a bigger machine.*

| Horizontal Scaling                                           | Vertical Scaling                    |
| ------------------------------------------------------------ | ----------------------------------- |
| Load Balancing Required                                      | N/A                                 |
| Resilient                                                    | Signle point of failure             |
| Network Communications = slow (RPC : Remote Procedure Calls) | Inter-process Communications = fast |
| Data Inconsitency Issues/Concerns                            | Consistent                          |
| Scales well as users increase                                | Hardware Limitations                                    |

**What's used in the real world?**
- Both, we use horizontal scaling for the whole system, but each part of the system is vertically scaled as much as possible (relative to the allowed budget and the needs).


---

**How to Scale a system?**
1. Vertical Scaling : optimize processes and increase throughput using the same resources.
2. pre-processing & cron job.
3. backups : make the system resilient by avoiding single points of failure.
4. horizontal scaling : buy/rent more resources.
5. micro-service architecture :
	- divide responsibility depending on strengths and weaknesses of the different parts of the system.
	- scale each part of the system independently.
6. Distributed System : 
	- don't put all ur eggs in one basket.
	- have working clones of your system in different places to minimize the chance of failure.
	- partitioning : local work is done by the closest clone.
	- Load balancer : part of the system that handles efficient routing of requests to different parts of the system based on clear and measurable metrics like total delivery time (takes over this responsibility instead of letting the user deal with it).
7. Decoupling the System :
	- separating concerns to allow for better management/handling of each part more efficiently.
8. Logging & Metric Calculations :
	- this is done for the following reasons:
		1. Analytics (figuring out where errors occured).
		2. Auditing.
		3. Reporting.
		4. Machine Learning.
9. Extensibility :
	- don't redo all the work every single time you want to add something new.
	- each part of the system does abstract work, regardless of the different types of input it may recieve.
		- ex: take a black-box and deliver it, regardless of what's inside it.

---

# HSD vs LSD
*High-Level System Design vs Low-Level System Design*

- HSD : how stuff works overall, abstract view of how things are connected and how they work.
- LSD : how the code itself is written, creating clean code and making it efficient.

---

# Load Balancing
*distributing requests to system resources in an efficient way*

- The standard way to hash objects is to map them to a search space, and then transfer the load to the mapped computer. A system using this policy is likely to suffer when new nodes are added or removed from it. ^f3059d
- extremely high cost of adding a new node is (~100% change).


## Consistent Hashing
- Consistent Hashing maps servers to the key space and assigns requests(mapped to relevant buckets, called load) to the next clockwise server. Servers can then store relevant request data in them while allowing the system flexibility and scalability.


**What does consistent hashing provide ?**
- Fault Tolerance : handling when a machine crashes.
	- we hash the servers and map them to the metric space
	- using multiple different hash functions to preserve multiple spaces for each server on the metric space (ring).
	- we also hash requests and map them to the id space (metric space, ring), and direct them to the closest server clockwise.
	- when one server fails, requests go to the next closest server (clock-wise direction).

- Scalability : machines need to be added to process more requests.
	- when a new node (server) joins the network, only a few keys are affected, and the rest of the nodes are not affected.

### Terms
- request allocation : assigning a request to a server.
- node : the server node mapped to the metric space after hashing (assigned an ID).
- key : the request's key mapped to the metric space after hashing (assigned an)

### Code
[[Consistent hashing|Consistent hasing implementation in java]]

---

# Message/Task Queues
*notifier, heartbeat, Load balancer(consistent hashing), persistence(DB)*

What happens if a server is down?  it will lose it's task queue (if it's stored locally).
Solution : 
	1. Store task list in a database.
	2. add a field in the database that tells you which server the task belongs to.
	3. create a (notifier) which probes servers at specific intervals to check for activity (TCP heartbeat protocol).

## Implementation
1. rabbitmq
2. zeromq
3. apache kafka??
4. apache activemq
5. apache rocketmq
6. ibm mq
7. redis??

---

# Monolith vs Micro-service Architecture

| Architecture  |   Monolith                                                                                                                                                                                                      | Micro-service                                                                                                                                                                        |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Advantages      | - better for small teams<br>- less moving parts<br>- no duplicated code<br>- faster (all calls are inside the system)                                                                                             | - easier to scale<br>- easier for a new team member<br>- parallel developing is easier (each micro-service is developed independently)<br>- easier to reason about (less hidden parts, more stream line approach) |
|Disadvantages  | - complicated to explain for a new team member<br>- complicated deployment (redeploy on each change)<br>- too much responsibility on each server (coupling, single point of failure) | - not easy to design<br>- needs skilled architects                                                                                                                                                                                     |


---

# Optimizing Database Querying

1. optimize queries using SQL optimizer
2. indexing
3. Sharding

## Sharding
*partition the data then each database server handles one partition*

**Partitioning :**
1. Horizontal partitioning : uses a key to break the data into partitions, each handled by a database server. 
2. Vertical partitioning : usies columns to break the data into partitions

**Principles :**
1. Consistency
2. Availability

**Problems :**
1. JOINS :
   - when data needs to be queried from two different partitions then joined together.
 
2. Inflexible :
   - can't have more servers, because [[#^f3059d|it's very costly]].
   - Solution : [[#Consistent Hashing]].

**Note :**
- MEMCACHED : distributed memory-caching database system that used to speed up dynamic database-driven websites by caching data and objects in RAM to reduce the number of times an external data source must be read. ^f95fd7

