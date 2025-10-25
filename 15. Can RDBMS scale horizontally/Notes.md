# Can RDBMS scale horizontally?

➡️ **In theory**: Yes

➡️ **In practice**: It’s very difficult and limited compared to NoSQL databases.

Traditional RDBMS (like MySQL, PostgreSQL, SQL Server, Oracle) are designed for vertical scaling, not for easy horizontal scaling.

However, modern architectures and tools (e.g., Vitess, Citus, CockroachDB, Google Spanner) have made horizontal scaling possible, but it comes with significant challenges.

## What is RDBMS?
- Software that performs data operations on relational databases.
- **Operations**: Store, Manage Query, and retrieve data.
- **Tables**: Data is represented in the form of tables.
- **Foreign Keys**: The relationship between the two tables is represented by foreign keys.

### Advantages of RDBMS
- No data redundancy and inconsistency.
- **Data concurrency**: A locking system is provided by RDBMS to prevent abnormalities from occurring.
- **Data searching**: Built-in searching capabilites (no need of a separate programme as in FS)
- **Data Integrity**: Ex- To maintain data numeric columns won't have alphabetic data.
(There is no process in the file system to check these constraints automatically)

### Disadvantages of RDBMS
- Rigid Schema (No Flexibility)
- High Cost
- Scalability Issues (Horizontal Scaling / Sharding is very difficult)