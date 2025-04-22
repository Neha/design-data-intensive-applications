## Introduction

Focus of this chapter is on the:

- Fundamentals of the data systems.
- what factors to consider while creating data intensive application.

### What are data intensive applications?
Applications such as twitter, facebook etc. are data intensive applications. In these apps the main bottleneck is "data handling" not CPU or memory. 

Apps do data handling in following ways:
 - **database:** storing data. So, that they or another application can use it
 - **caches:** remember the results of the expensive operation, to speed up reads.
 - **search indexs:**  Allow users to search data by keyword or filter it in various ways
 - **stream processing:** Send a message to another process, to be handled sync
 - **batch processing:** Periodically cruch a large amount of acculamted data

### What are the factors to consider while creating data intensive applications?

1. **Reliability:** Keep the lights ON even when there is a fault

- An application should be highly reliable
- If there is any fault, it should be able to either  heal itself or still keep working

**Systems can fail:**
1. due to network failure
2. software failuer
3. or human errors (misconfigured servers)
4. Network failures

**Techniques:**
1. Redundancy (replication)
2. Monitoring
3. Fault-tolerance patterns

eg: An engineer accidentally deletes a database, but a reliable system has backups and recovery plans in place.

2. **Scalable** Holds the load gracefully
- Application should be scalable to accomdate the more users, more load, more data without breaking it.
- It should be able to accomdate the load.

**Type of loads**
1. Volume: More data (GBs → TBs → PBs)
2. Velocity: Faster data (real-time updates)
3. Variety: More types of queries/workloads

**Techniques:**
1. Vertical Scaling
2. Horizontal Scaling

eg: A photo-sharing app starts with 1,000 users. After a celebrity tweet, it spikes to 1 million users. Can the app scale up?

3. **Maintainbility** The system should be easy to work on, adapt, and extend over time
- The application should be maintainable for future engineers
- easy to understand
- Resilient to changes in tech or teams

**Techniques:**
1. Modular code
2. Good abstractions
3. Monitoring and testing
4. Automation (CI/CD)

eg: A well-maintained codebase lets a new developer quickly fix a bug without breaking 10 other things.

4. **Evolvability** 
the system should be able to evolve to the changing technologies.

eg: A small team builds a prototype using a single database. Later, they need replication for reliability, partitioning for scalability, and caching for speed.

