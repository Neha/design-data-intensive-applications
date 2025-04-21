## Chapter 5: Replication

### Focus of this chapter
How to have database replicas in your application for low latency, increase availability, and increase read and throughput.

### Important terms

1. Evenetual consistency
2. read your writes
3. Monotonic reads
4. Quorom 


### Questions this chapter answer
1. What is replication
2. why we need replication
3. What are the trade off
4. Cost of replication
5. How to manage changing data and replication?
6. Algo for replication
7. what will happen when the databased fails?
8. how to know database/replica is failed?
9. what is sync/async data update
10. Handling failover

### Summary:

- replication means keeping a copy of the same data on multiple machine that are connected via a network. 
- We need replication:
   1. low latecny : To keep the data  geographicall near to your users
   2. Increase availability: System will keep working even if some of its parts failed
   3. Increae read and throughput: Scale out the number of machines that can serve read queries
- If your data is not changing with time, then replication is easy. Just copy the data to every node once and you are done. The complication comes when the data is changing.
- Algos for replication are below (each have their pros and cons)
    1. Single-leader replication
    2. multi-leader replication
    3. leaderless replication
- Common things to think about:
    1. async or sync replication
    2. How to handle failed replicas
- leader and followers 
- Synchronus vs async replication

#### Single Leader based:

- Each node that stores a copy of the db is called "replica"
- to make sure that replica has the same data we can use the "single leader", "master slave", "active/passive" replication (config option)
- This mode of replication is a built in feature of many db - relation db, non-relation db, and brokers too
- Asnyc/sync (config option):


#### Leader less

- there is no leader
- all writes and reads will go to all replicas
- dynamoDB uses leader less
- what is one replica fails? 
    - In leaderless - failover configuration does not exist
          - Handling Failover:
                - Read repair
                - anti entropy
        - The other are there to read and write
        - If replica fails and comeback and read requests goes to it?
        - How to catchup with the stale writes
- Quorums: 
    - n = number of nodes
    - w = number of writes
    - r = number of reads
    n < w + r ; if we have 3 nodes and we are fine with 2 to always healthy and responding OK then we 
    can assume all is good. We won't wait for the 3rd replica's OKAY 
    - What is w and r are lesser than n? it will give an error
    - In DynamoDB we can set these values
- Limitations of Quorums:
  

### Examples

- Calendar design
- room booking


