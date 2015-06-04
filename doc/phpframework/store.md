---
layout: doc
title: saft.store
---

Package _saft.store_ consists of Triple- and Quadstore related classes and interfaces. Its purpose is to provide a foundation to built a store implementation on.

## Store

This interface describes, which methods a store implementation has to provide. We propose to implement it in other 
languages if you need a store implementation, to have the best compatibility between different implementations. 

Documentation [here](storeinterface).

To help you to create further adapters, we provide two abstract classes: AbstractTriplePatternStore and AbstractSparqlStore. 
They already implement basic methods to save you time and work.

#### [AbstractSparqlStore](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/AbstractSparqlStore.php)

Its purpose is to be the basement for adapters which interfact with a triple/quad store with a SPARQL engine.

#### [AbstractTriplePatternStore](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/AbstractTriplePatternStore.php)

If you want to write an adapter for a store, which does not provide a SPARQL engine, you can use that abstract class. That could be the case if you, for instance, want to store triples on the file system.


## ChainableStore

A store chain consists of components to basically return results for given queries. It is modular and can be configured by the developer depending on his needs. For instance, if you just need store access, you can use a chain consisting of a query logger and a store adapter. Another example are environments with high server load, in that case you can use access control, together with a query cache and a store adapter.

Documentation [here](storechain).


