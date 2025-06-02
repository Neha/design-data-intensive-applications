## Chapter 3: Storage and Retrival 

Focus:

1. Why knowing storage engine is crucial

2. Different storage engines and use-cases

## OLTP vs OLAP

OLTP: Online Transaction Processing

OLAP: Online Analytics Processing


As a developer you might not be developing a database from scratch but it is important to know 
what each storage engine we have, use-cases, and trade-offs to take tech decisions.

In a simple way, data storage is just db_set(key, value), db_get(key);  

Basically, imagine you just want to set a key-value in a file, and retrieve the value when key is provided. 
This will be append only log based file. The data will keep appending leads to duplication as we are not overwritting the value but we assume the latest will be also the new value. 

However, the problem comes when we try to access a value db_get(k1); When there will be multiple entries it will lead to o(n).

## Index and DB

To solve the above issue, we can use INDEX (another data strcuture). It is kind of metadata stored in a seprate  file.
This is made from the original data. 

However, writes are expensive as everytime we are writing to the storage we need to update the index. 

Hence, database doesn't provide the index by default.

Leave it on the developers to decide index based on the access pattern.

## type of storage engines

1. Log based:

- append only

- new writes goes at the end

- writes are fast, reads are slow 

- good for recovery (resilant)

- LevelDB, Cassandra uses

- memtable, LSM , SSTable

![log based](/images/log-based.png)

2. Page based:

- Data is split into fixed-size blocks or pages (like 4KB).

- Updates happen "in-place"

- databases use **B-trees** to index them.

- Good for random reads

- In-place updates can be complex under high write load

- MySQL (InnoDB), Postgres eg: 



