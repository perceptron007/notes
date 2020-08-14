# Backend 
- Communication Protocol
    - TCP vs UDP
        - OSI Model
        - What happens during TCP ?
        - What happens during UDP ?
        - Which is slow ? What use case does someone solve ?
    - HTTP / HTTP2 / HTTP3
        - How do they work ?
        - What problems does they solve ?
    - Bidirectional Communications 
    - gRPC
    - webRTC
- Web Servers
    - Caching / Serving Static Content 
    - Edge Web Server
    - Etags / Etags generation
    - Single / Multiple Threading
    - Web Server working as Proxy (Nginx)
- Messaging Queue
- Database Engineering
    - Relational
    - NoSQL
    - Index Based Searching (Elastic Search)
    - ACID Properties
- Proxies
    - Proxy vs Reverse Proxy 
    - Caching Layer
    - Layer 7 Proxying
    - Layer 4 Proxying
    - Different layer of proxying
    - Load Balancing
    - Service Mashes
- Caching
    - Stateful vs Stateless Caching
    - Distributed Caching
- Messaging System
    - Queue (Rabbit MQ)
    - Pub Sub System
- API Web Framework
    - Django
    - Node JS
    - Golang
- Message Formats
    - Protocol Buffer
    - XML
    - JSON
- Security
    - How to communicae between two nodes ?
    - How to keep your database secure ?
    - What ports to open, what to close ?
    - Web security / Network Securtiy

## OSI Model
Open System Interconnection Model 

**Assumptions**
We have a router which is connected to different devices on our connection.

-  


## TCP vs UDP 
  **What is TCP**
  
  **What is UDP**

## Reverse Proxy

## Encryption

### Homomorphic Encryption

#### What is Encryption ?
**Symmetric Encryption**
You have data, you use a Key to encrypt this and then you use the same key to decrypt the data.



#### Why we can't always Encrypt ?
- Database Queries can only be performed on plain text. 
- Analysis, Indexing, tuning.
- Applications must read data to process it. 
- TLS Termination layer 7 reverse proxies and load balancing.  [ ? ]


#### What is Homomorphic Encryption ?
- Would provide ability to perform arithmetic operation on encrypted data
- No need to decrypt
- You can query a database that is encrypted ( A query is Binary Search Tree)
- Layer 7 reverse proxies don't have to terminate TLS, can route traffic based on rules without decrypting traffic.
- Databases can index and optimize without decrypting data.

#### Demo (IBM FHE toolkit)
[DEMO REPO]([https://github.com/IBM/fhe-toolkit-linux/blob/master/GettingStarted.md](https://github.com/IBM/fhe-toolkit-linux/blob/master/GettingStarted.md))

### Best Practices For Back End
- Have different User for Database Read / Database Write / Database Delete.
- Create three different pool for database read / database write / database delete. 
- You can also have a separate pool for database where transaction multiple parts say for example you have a transaction which delete as well as update record. 
- Don't write unbounded queries to sql. (Always range your limit with the help of pagination)
- Don't return the database and server errrors to user / Instead return Custom errors. 
