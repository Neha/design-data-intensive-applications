## Consistency and Consenus

**Focus of the chapter is:**
    1. how distrubted system keeps the data consistent and agree on values even when there is a failure.
    2. It dives deep into consistency models and the challenge of reaching consensus across unreliable networks and nodes.
    3. Introduces linearizability, consensus problems, and algorithms like Paxos and Raft.

--

In distributed systems,  a lot can go wrong - packet(s):

1. can be lost, 
2. reordered, 
3. duplicated, or arbitarely delay in the network, 
4. clocks are approximetly at best, 
5. and nodes can pause, or crash at any time.

If we are fine with failing of the system and showing an error to user then it is fine.

but, if we want make the system keep working even their is a faulty component then we need to figure out how. However, there are limits - what can and cannot be done 

Need to understand the scope:
    In some situataions it is possible for the system to tolerate faults and continue working and in a few we can't. So, need to understand what can and can't. 

##  Building fault-tolerant systems:

one of the best way of building fault-tolerant systems is to find some general purpose abstractions with:

1. Useful gurantees, implement them once, and then let applications rely on those gurantees just like transactions (atmociity, isolations, and durability)

even though crashes , race conditions, and disk failures do occure, the transaction abstracton hides those problems. So that the application doesn't need to worry about them.

Our goal is to find the abstraction. This will allow an appliction to ignore some of the problems with the distributed systems.  

1) **Consenus:** 

Getting all the nodes to agree on something. 

Eg: in database with single leader replication. if the leaders die and you need to fil over to another node,then remaning database nodes will vote to elect the new leader and consenus can be use here. If not, database can end up with the 2 leader and this is known as "brain split". Consenus helps in avoiding this.

**Consensus Algorithms:**

1. Paxos – Classic, but complex to implement
2. Raft – Easier to understand and widely adopted
3. Zab – Used in Apache Zookeeper
4. PBFT – Byzantine Fault Tolerant (handles malicious nodes)

**The classic problems solved by consensus:**

- How do machines agree on something (like who’s the leader)? it is difficult because: Nodes may fail and Messages may be lost or delayed

- Leader election

- Agreeing on a log of operations (important for replication)

**Challenges of Consensus**

- Asyncronus network: where messages can be delayed infinitely , and  make it impossible to guarantee consensus reliably 

Systems often trade off performance to achieve stronger consistency guarantees when needed


## Linearziability (Strong Consistency): 

Linearizability provides the strongest consistency model. 
When you update your bank balance, everyone (you and the bank) immediately sees the updated balance.

However, there are pros and cons

**What is Linearziability?**

Linearziability means the transcations will take always in order. 
also known as: atomic consistency, strong consistency, immediate consistency or external consistency.

1. in an eventually consistent database, if a user will ask same question to 2 different replica. There might be a chance the response would be different because of "replication lag. It would be confusing. It would be better if we can give the impression that there is only 1 copy and we won't be worrying about lag.

2. basic idea of "linearziability" to make a system appear as if there is only one copy of the data, and all operations on it are atomic. though there will be multiple replicas.

3. Eg: as soon as one client successfully complete a write, all clients reading from the DB must be able to see the value just written. No stale data, no cache nothing. Linearziable is a "recency gurantee"

**Where to use linearizable?**

1. Bank accounts

2. Inventory systems

3. Locking services: Like ZooKeeper (leader election, distributed locks).

**Implement system linearizable?**

1. Single write: write on one node and other nodes can replicate 

2. Multi writer (Consensus): Nodea sgree on the order of operation before applying them

3. Quorum Algo: Write and read to/from a majority of nodes.

**Cost of linearizable?**

1. Latency: to read or write, nodes needs to talk to eachother and agree first. This will add networj delays

2. Availability: If too many nodes crash or network splits happen (like internet issues), the system cannot respond until they recover

3. Throughput  : The system can only handle limited operations per second compared to eventually consistent systems.

4. Slower than eventually consistent systems.

## CAP theorm

C: consistency

A: Availability

P: Fault Partition


## Total broadcast Order


With Consenus, Total broadcast Order is related.  If you solve one, other will be solved.

For replicates state machines (DBs), TOB assures every node applies the same updates at the same order - keeping them consistent. 

TOB, assures all nodes deliver the same messages and in the same order. Consequences algorithims (paxos, and raft) can implement TOB. 


## Important 

1. serialize vs linearziability

Linearizability: Applies to individual operations on a single object (e.g., read/write a key).
Serializability: Applies to multi-object transactions (multiple keys/documents).

Both are about ordering, but serializability is broader and more about transactions.
