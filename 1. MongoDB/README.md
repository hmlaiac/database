# Introduction

MongoDB is a popular open-source `document-oriented database system`. It is designed to store and
manage `unstructured data`
in the form of documents, which are similar to `JSON objects`. MongoDB is known for its flexible data model, horizontal
scalability, and ease of use.

# MongoDB VS SQL Database

## Advantages of MongoDB

1. Data Model: MongoDB is a document-oriented database, which means that data is stored in a more flexible and dynamic
   way
   compared to traditional SQL databases, which are based on a rigid table structure. In MongoDB, data is stored in
   collections of documents, which are similar to JSON objects and can have varying structures. In contrast, SQL
   databases
   use tables with a `fixed schema`, where each row has the `same set of columns`.
2. Query Language: MongoDB uses a query language called MongoDB Query Language `(MQL)`, which is based on `JSON` and
   allows
   for more flexible and expressive queries. SQL databases, on the other hand, use SQL (Structured Query Language),
   which is more rigid and requires a predefined schema.
3. Scalability: MongoDB is designed to `scale horizontally`, which means that it can easily handle large datasets by
   distributing them across multiple servers. Traditional SQL databases, on the other hand, are designed to scale
   vertically, which means that they rely on adding more resources to a single server.
4. Performance: MongoDB can provide `faster performance` for certain types of queries, especially when dealing
   with `large
   datasets`. This is because it can use `indexing and other optimization techniques` to speed up queries. In contrast,
   traditional SQL databases may experience performance issues when dealing with complex queries or large datasets.

## Disadvantages of MongoDB

1. Transactions: MongoDB supports transactions, but with some limitations. Traditional SQL databases, on the other hand,
   have strong support for transactions and provide advanced features suchas ACID (Atomicity, Consistency, Isolation,
   and Durability) compliance, which ensures that transactions are executed reliably and with data integrity.
2. Data Relationships: MongoDB supports data relationships between documents using a feature called document embedding
   or referencing. This allows for more flexible and efficient data modeling compared to traditional SQL databases,
   which use foreign keys to establish relationships between tables.

# Conclusion

In my points of view, MongoDB is a good choice for big data analysis and data mining due to its flexibility and easy
migration. However, it is not a good choice for transactional data due to its lack of ACID compliance. e.g. databse of
Salvio Environmental Monitor.

## ACID Compliance

- Atomicity: This property ensures that a transaction is treated as a single, indivisible unit of work. It means that
  either all the operations in a transaction are completed successfully, or none of them are completed at all. If any
  part
  of a transaction fails, the entire transaction is rolled back to its original state.

- Consistency: This property ensures that a transaction brings the database from one valid state to another. It means
  that
  a transaction should not violate any integrity constraints or business rules defined by the database schema. If a
  transaction violates any constraints or rules, it is rolled back to its original state.

- Isolation: This property ensures that multiple transactions can execute concurrently without interfering with each
  other. It means that each transaction should be executed in isolation from other transactions, and the results of a
  transaction should not be visible to other transactions until it is committed.

- Durability: This property ensures that the results of a transaction are permanent and survive system failures. It
  means
  that once a transaction is committed, its changes are saved to non-volatile storage, such as a hard disk or SSD, and
  will still be available even if the system crashes.