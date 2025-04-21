## Consistency and consenus

In distributed systems,  a lot can go wrong - packeta can be lost, reordered, duplicated, or arbitarely delay in the network, clocks are approximetly at best, and nodes can pause, or crash at any time.

if we are fine with failing of the system and showing an error to user then it is fine.

if we want make the system keep working even their is a faulty component then we need to figure out how. However, there are limits - what can and cannot be done 

- in some situataions it is possible for the system to tolerate faults and continue working and in a few we can't.
- we need to understand the scope.

one of the best way of building fault-tolerant systems is to find some general purpose abstractions with useful gurantees, implement them once, and then let applications rely on those gurantees just like transactions (atmociity, isolations, and durability)

even though crashes , race conditions, and disk failures do occure, the transaction abstracton hides those problems
so that the application doesn't need to worry about them.

Our goal is to find the abstraction. This will allow an appliction to ignore some of the problems with the distributed systems.  

1) Consenus: Egetting all the nodes to agree on something. Eg: in database with single leader replication. if the leaders die and you need to fil over to another node,then remaning database nodes will vote to elect the new leader and consenus can be use here. If not, database can end up with the 2 leader and this is known as "brain split". Consenus helps in avoiding this.

2) Consistency: 