---
 title: Consistency in ACID is different from Consistency in CAP  
 tags: [database]
 style: fill
 color: light
 excerpt: Interviews aren’t just an opportunity for the company to evaluate you - they’re also your chance to learn more about the company
 comments: true
 categories: computer-science
 last_modified_at: 2024-09-20T15:30:00+05:30
 toc: false
---

Consistency is a cornerstone of data integrity, but its meaning can shift depending on context

### Consistency in Databases 

In the context of ACID(Atomicity, Consistency, Isolation, Durability) properties of database, consistency refers to the integrity of the data. This means that data must meet all validation rules and integrity constraints set in the Database system. If a database has a rule that the balance of any bank account should not be negative, then any transaction that could potentially cause an account balance to go negative must be blocked or adjusted to maintain consistency.

For instance, imagine a banking system where a user tries to transfer Rs 100 from Account A to Account B. If Account A only has Rs 80, the transaction should be denied or only Rs 80 should be transferred, to maintain the integrity that account balances can't be negative.


### Consistency in Distributed Systems
In the distributed systems, consistency refers to how a system synchronizes and ensures that all nodes in the system reflect the same data at a given time. The challenge in distributed systems is to ensure that, despite potential network delays, all parts of the system eventually hold the same data. This is often discussed in the context of the CAP theorem (Consistency, Availability, and Partition tolerance), which states that in the presence of a network partition, a distributed system can provide either consistency or availability, but not both.

For instance, consider a social media platform where a user updates their profile picture. This update needs to be propagated across multiple servers around the world. Consistency in this distributed system means that eventually, all users, regardless of which server they access, will see the updated profile picture. However, due to network latency or synchronization delays, there might be a short period where some users see the old picture while others see the new one.

In summary, database consistency is about maintaining data integrity within a single database, while consistency in distributed systems is about ensuring data synchronization and uniformity across multiple nodes or servers in a network.