---
layout: doc
title: saft.querycache
---

The QueryCache component provides a layer based on our cache infrastructure to store query results and provide them later on. Our intention while developing it was, to provide a fast way, to reuse query results. 

#### Inspired by paper

There is a paper from Michael Martin called [*Improving the performance of semantic web applications with SPARQL query caching*](Link: http://www.informatik.uni-leipzig.de/~auer/publication/caching.pdf) that we used to get an idea how to organize the whole internal structure. The paper describes the principles and a solution using a TripleStore and relational database system.

## Usage

To get an idea what the QueryCache is for, here are a couple of code snippets.

### How to setup

The QueryCache relies on the cache infrastructure located under saft.cache. It is simple key-value-pair based. All information about queries and their parts will be saved using the given cache instance.

  // setup a cache instance
  $cache = new Cache( /* ... */ );

  // setup QueryCache instance with cache instance
  $queryCache = new QueryCache($cache);

### Save a query result

Saving a query result is very simple, you just need the SPARQL query and the according result. It does not matter where the result is coming from; it does not need to be created by Saft at all. 

Our current caching infrastructure (with MemcacheD and FileCache) can serialize nearly all PHP-structure, no matter if its an array or an object structure.

  // Instance of Query
  $query = AbstractQuery::initByQueryString(
    "SELECT ?s FROM <http://graph/> WHERE {?s ?p ?o.}"
  );

  // The $result variable contains the result of a previous SPARQL query
  $result = ...
  
  // store result for a given query
  $queryCache->saveResult($query, $result);


After calling the saveResult method you can retrieve the result by calling:


  $savedResult = $queryCache->getResult($query);

Now you have the result in $savedResult, you stored previously. If you call saveResult for the same query but with different results, all obsolete information will be removed automatically.


### Update and invalidate existing results

Well, you don't have to think about that (anymore), because QueryCache will handle that for you. You only need to use saveResult and getResult, much like a simple key-value-pair based cache. 


## Internals

### Storage structure

![part interaction](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/querycache/querycache-overview.svg)

The QueryCache needs a key-value-pair based caching solution. It stores different parts of the query, using their value as keys. Of the given query the graph URIs (1) and triple patterns (2) will be extracted and used as keys and a list of according queries is the value. The query list contains SPARQL query strings. A graph URI can be part of different SPARQL queries, so it has a connection to each one of them. Same for the triple pattern. 

Each query of the query list points to a query cache container (4). It contains all information neccessary about a certain SPARQL query:
- Graph URI's
- Used triple pattern
- Query result
- SPARQL Query itself

As you can see, there is a back-reference from elements of the query cache container to the graph URI and triple pattern, we talked about above.

## Restrictions

There are a couple of restrictions for the QueryCache. Here is a short overview about them.

### No transaction support

It is not possible yet, to group queries and their results to one transaction. That means, that if one of the queries gets invalidated, the rest will too. 

We plan to support transactions in the near future.

### Cache uses no locking

Because we use a simple key-value-based caching solution, there is no lock if you write a key-value-pair. But with the current implementation of QueryCache multiple instances could update at the same time the same key-value-pair which might lead to race conditions.

