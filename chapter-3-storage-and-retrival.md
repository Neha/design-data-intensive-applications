## Chapter 3: Storage and Retrival 

Focus:

1. Why knowing storage engine is crucial

2. Different storage engines and use-cases

As a developer you might not be developing a database from scratch but it is important to know 
what each storage engine we have, use-cases, and trade-offs to take tech decisions.

In a simple way, data storage is just db_set(key, value), db_get(key);  

Basically, imagine you just want to set a key-value in a file, and retrieve the value when key is provided. 
This will be append only log based file. The data will keep appending leads to duplication as we are not overwritting the value but we assume the latest will be also the new value. 

However, the problem comes when we try to access a value db_get(k1); When there will be multiple entries it will lead to o(n).


## Index and DB

## type of storage engines

1. Log based:

- SSTable

- LSM trees

2. Page based:

- B trees

## OLTP vs OLAP

OLTP: Online Transaction Processing

OLAP: Online Analytics Processing

