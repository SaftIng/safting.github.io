---
layout: doc
title: Store Chaining
---

# Store Chaining

This page gives you an overview what we understand under Store chaining and why it is useful. 

## Introduction

![usecase](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-usecase.svg)

<br/>

The following introductions are based on the usecase-picture above and describing an important use case for the store chain. 

Lets start with a store. It provides access to your data which is modelled in graph structures, for instance. To get the data you have to ask the store using SPARQL queries. In Saft we have an adapter for each store we wanna access and each understands SPARQL, more or less. In the use case picture, you see the Virtuoso Store adapter on the third position and it directly communicates with the Store.

In cases of heavy store-traffic, you wanna cache SPARQL queries to take the load off the store. You can use Saft's Query Cache component for that. It basically stores the query result behind the query string, think of it as a key-value-paired store mechanism. In a store chain it should come before the store adapter to prevent calling the store. If the query was executed before and it serves cached results. (See second part in the picture)

The first part in the picture is the access control part. It basically checks if certain queries are allowed to be executed on certain graphs. Yes, it mostly depends on users and other restrictions, but leave that besides for now. Before serving queries using Query Cache or Store, you should check, if the query is allowed to be executed. If not, well, you quit the call with a warning and stop further exection.

In the end it depends on your use case which parts you wanna put in the chain. For instance, if your application is the only one working directly on the graph, you may not need access control. Saft's implemenation allows you to create your own chains. It also supports the creation of chain-tree's, because a store chain instance can also be part in another store chain. Please see the following illustration.

![tree](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-trees.svg)

<br/>

## Technical details

Now will follow a technical introduction about how the current implementation works. Please have a look at the following picture:

<br/>

![part interaction](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-partsinteraction.svg)

<br/>

This image illustrates the basic structure of a store chain. It consists of different parts, each provides unique functionalities. Each part has a successor and the communication flow usually works calling a successor function and compute its result.

The store chain saves references of all its parts. But each part only knows his successor. 

### Successor handling

Each part has to handle its successor. For that, it has to provide the following functions:

- **setChainSuccessor** - Its purpose is to save the reference for a given instance which implements [StoreInterface](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/StoreInterface.php). The given instance has to be setup *before* it will be passed to.
 
Each part of the store chain at least has to implement [StoreInterface](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/StoreInterface.php). The following functions have to support successor-calls:

- addStatements
- deleteMatchingStatements
- getMatchingStatements
- getStoreDescription
- hasMatchingStatements
- query

As you see in the picture above, each function either gets a SPARQL query or statement as parameter, primarly. Yes, there are other parameters beside that, but this is the relevant one. 

When a part of the store chain calls its successor, that means, that it calls the same method which was called by him. For instance, if you called the query method of Query Cache part and Virtuoso Store is its successor, it has to call his query method with the same parameter. Furthermore, each part *has* to return its own result and not the result of its successor. If the part has no active functionality in the method, it just can forward the result which came from its successor. Thats the case by Query Cache's addStatements method; it has no real effect on the store, so it either forwards the result from its successor or throws an exception, if no successor is available.

### Result types

Each successor has to return a result, even if an exception appears. In this way, there is only one communication channel and no bypassing information. 

#### StatementIterator

A [statement iterator](https://github.com/SaftIng/Saft/blob/master/src/Saft/Rdf/AbstractStatementIterator.php) provides access to a list of Statements. It will be used for statement-oriented methods, such as getMatchingStatements.

#### ResultSet

The [resultset](https://github.com/SaftIng/Saft/blob/master/src/Saft/Sparql/ResultSet.php) will be used for all non-statement lists. They usually belonging to non-statement-oriented methods, such as query.

#### ResultValue

[This](https://github.com/SaftIng/Saft/blob/master/src/Saft/Sparql/ResultValue.php) type of result will be used in cases where only a simply value will be returned, for instance to answer an ASK-query.

#### ResultError

In case something went wrong, for instance the query was malformed, the request has to be quit with an error. But no exception will be thrown, as usually, an instance of [ResultError](https://github.com/SaftIng/Saft/blob/master/src/Saft/Sparql/ResultError.php) will be returned. It contains all information neccessary to handle the error.
