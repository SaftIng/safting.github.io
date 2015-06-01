---
layout: doc
title: Saft PHP Framework
---

The _Saft PHP Framework_ consists of:

- Saft - Library. Here are all important classes of Saft located. It consists of different part which will be described below.

- Skeleton (saft.skeleton) - Skeleton application. It contains additional helper classes to speed up developing using Saft library.


## Saft library

<a class="btn" href="backends">saft.backend</a>
<a class="btn" href="rdf">saft.rdf</a>
<a class="btn" href="store">saft.store</a>
<a class="btn" href="data">saft.data</a>
<a class="btn" href="querycache">saft.querycache</a>

* [Saft.backend](backends) are actual implementations of the interfaces of _Saft.library_ (e.g. cache, querycache, store adapters and so on) using some special methodology and technology.
* [Saft.rdf](rdf): provides interfaces for the basic RDF concepts, such as _Node_ (Namednode/URI-Resource, Literal, Blanknode) and _Statement_ (Triple and Quad). Additionally the StatementIterator provides a datastructure for just holding a list of Statements.
* [Saft.store](store): StoreInterface with the implementations AbstractStatementPatternStore and AbstractSparqlStoreAdapter
* [Saft.data](data): data interface with
    * DataParser for parsing any RDF serialization and returning a StatementInterator
    * DataSerializer for serializing data to any RDF serialization
* [Saft.querycache](querycache): The QueryCache component provides a layer based on our cache infrastructure to store query results and provide them later on.

## Saft Skeleton Application (saft.skeleton)
> Will be contained in some post 0.1 release

The _Saft.skeleton_ will be a collection of helper classes (such as factories, ..) and other things that helps you accelerate while build applications with _Saft_.
