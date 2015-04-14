---
layout: doc
title: Store Chaining
---

# Store Chaining

This page gives you an introduction to the concept of _Store Chaining_ and why it is useful.
The following image depicts a use-case which is described in the introduction and should serve as a motivating use-case for the _Store Chain_ concept.

![usecase](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-usecase.svg)

<br/>

## Introduction

Lets start with a store. It provides access to data in a graph structure. To get the data you have to ask the store using SPARQL queries. In Saft we have an adapter for each store which we want to access and each of them understands SPARQL (more or less). In the use-case picture, you see the Virtuoso Store adapter on the right hand side and it directly communicates with the Store Database.

In cases of heavy store-traffic, you might want to cache SPARQL queries to take the load off the store. You can use Saft's Query Cache component for that. It basically stores the query result behind the query string, think of it as a key-value-paired store mechanism. In a store chain it should come before the store adapter to prevent calling the store (in the middle of the use-case picture). If the query was executed earlier the cache will serve the previous result again.

On the left hand side of the picture you can see the access control component. It basically checks if certain queries are allowed to be executed on certain graphs. Yes, it mostly depends on users and other restrictions, but leave that besides for now. Before serving queries using Query Cache or Store, you should check, if the query is allowed to be executed. If not, well, you quit the call with a warning and stop further execution.

In the end it depends on your use case which parts you want to put in the chain. For instance, if your application is the only one working directly on the graph, you may not need any access control. Saft's implementation allows you to configure your own _Store Chains_.

> It also supports the creation of chain-tree's, because a store chain instance can also be part in another store chain. Please see the following illustration.

> Comment: is this based on the instance? I would realize this with a store component with allows multiple stores as successors.

![tree](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-trees.svg)

<br/>

## Technical details

Now will follow a technical introduction about how the current implementation works. Please have a look at the following picture:

<br/>

![part interaction](https://rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-partsinteraction.svg)

<br/>

This image illustrates the basic structure of a store chain. It consists of different parts, each provides unique functionalities. Each part has a successor and the communication flow usually works calling a successor function and compute its result.

The store chain saves references of all its parts. But each part only knows its successor.

### Successor handling

Each intermediate/chainable store has to handle its successor. For that, it has to provide the following method:

- `setChainSuccessor($successorReference)` - Its purpose is to take the reference of another instance which implements the [StoreInterface](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/StoreInterface.php). This method has to be called *before* the respective store instance is used to setup the successor store.

> Comment: I think this method should be defined in a separate `ChainableStore` or `IntermediateStore` interface.

> Comment: If `setChainSuccessor()` was not called prior to any other method call which needs a successor a `ChainableStore` or `IntermediateStore` could throw some `NotSetupException` (or similar).

Each part of the store chain at least has to implement [StoreInterface](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/StoreInterface.php). The following functions have to support successor-calls:

- addStatements
- deleteMatchingStatements
- getMatchingStatements
- getStoreDescription
- hasMatchingStatements
- query

> Comment: I think which methods are implemented by which kind of successor-calles should be up to the implementation.

As you see in the picture above, each method either gets a SPARQL query or statement as parameter, primarly. Yes, there are other parameters beside that, but this is the relevant one.


> Comment: I think the purpose of the following paragraph is not very clear.

When a part of the store chain calls its successor, that means, that it calls the same method which was been called on it. For instance, if you called the query method of Query Cache part and Virtuoso Store is its successor, it has to call its query method with the same parameter.
Furthermore, each part *has* to return its own result and not the result of its successor.
If the part has no active functionality in the method, it just can forward the result which came from its successor.
Thats the case for Query Cache's `addStatements()` method; it has no real effect on the store, so it either forwards the result from its successor or throws an exception, if no successor is available.

### Result types

Each successor has to return a result, even if an exception appears. In this way, there is only one communication channel and no bypassing information.

> Comment: Alternatively we could define a set of exceptions which are thrown in certain situations. This will still not enable bypassing since exceptions are thrown along the caller stack. This would make sure that malfunctions can be treated hierarchically and will no be ignored.

> Further we can define the return type for methods like `getMatchingStatements` and don't have to alway add an alternative for the error case. I case we handle exceptions with instances of `ResultError` we alway have to check the result e.g. of `addStatements` while if we use exceptions we could call it in a fire-and-forget manner and only have to care about the result in the case of an exception.

> Another aspect could be to check if there is any performance difference between exceptions and returned results

#### StatementIterator

A [StatementIterator](https://github.com/SaftIng/Saft/blob/master/src/Saft/Rdf/AbstractStatementIterator.php) provides access to a list of Statements. It will be used for statement-oriented methods, such as `getMatchingStatements` or `CONSTRUCT`-queries.

#### ResultSet

The [ResultSet](https://github.com/SaftIng/Saft/blob/master/src/Saft/Sparql/ResultSet.php) will be used for result lists. They are usually returned on to non-statement-oriented methods, such as `SELECT`-queries.

#### ResultValue

A [ResultValue](https://github.com/SaftIng/Saft/blob/master/src/Saft/Sparql/ResultValue.php) will be used in cases there is only a simply value to be returned, for instance to answer an `ASK`-query or `hasMatchingStatement`.

#### ResultError

In case something went wrong, for instance the query was malformed, the request has to be quit with an error. But no exception will be thrown, as usually, an instance of [ResultError](https://github.com/SaftIng/Saft/blob/master/src/Saft/Sparql/ResultError.php) will be returned. It contains all information neccessary to handle the error.
