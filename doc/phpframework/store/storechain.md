---
layout: doc
title: Store Chaining
---

# Store Chaining

This page gives you an overview what we understand under Store chaining and why it is useful. 

## Introduction

![usecase](https://cdn.rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-usecase.svg)

<br/>

The following introductions are based on the usecase-picture above and describing an important use case for the store chain. 

Lets start with a store. It provides access to your data which is modelled in graph structures, for instance. To get the data you have to ask the store using SPARQL queries. In Saft we have an adapter for each store we wanna access and each understands SPARQL, more or less. In the use case picture, you see the Virtuoso Store adapter on the third position and it directly communicates with the Store.

In cases of heavy store-traffic, you wanna cache SPARQL queries to take the load off the store. You can use Saft's Query Cache component for that. It basically stores the query result behind the query string, think of it as a key-value-paired store mechanism. In a store chain it should come before the store adapter to prevent calling the store. If the query was executed before and it serves cached results. (See second part in the picture)

The first part in the picture is the access control part. It basically checks if certain queries are allowed to be executed on certain graphs. Yes, it mostly depends on users and other restrictions, but leave that besides for now. Before serving queries using Query Cache or Store, you should check, if the query is allowed to be executed. If not, well, you quit the call with a warning and stop further exection.

In the end it depends on your use case which parts you wanna put in the chain. For instance, if your application is the only one working directly on the graph, you may not need access control. Saft's implemenation allows you to create your own chains. It also supports the creation of chain-tree's, because a store chain instance can also be part in another store chain. Please see the following illustration.

![usecase](https://cdn.rawgit.com/SaftIng/safting.github.io/master/doc/phpframework/store/storechain-trees.svg)
