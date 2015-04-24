---
layout: doc
title: saft.querycache
---

The QueryCache component provides a layer based on our cache infrastructure to store query results and provide them later on. Our intention while developing it was, to provide a fast way, to reuse query results. 

There is a paper from Michael Martin called [*Improving the performance of semantic web applications with SPARQL query caching*](Link: http://www.informatik.uni-leipzig.de/~auer/publication/caching.pdf) that we used to get an idea how to organize the whole internal structure. The paper describes the principles and a solution using a TripleStore and relational database system.

## Restrictions

There are a couple of restrictions for the QueryCache. Here is a short overview about them.

### No transaction support

It is not possible yet, to group queries and their results to one transaction. That means, that if one of the queries gets invalidated, the rest will too. 

We plan to support transactions in the near future.

### Cache uses no locking

Because we use a simple key-value-based caching solution, there is no lock if you write a key-value-pair. But with the current implementation of QueryCache multiple instances could update at the same time the same key-value-pair which might lead to race conditions.

