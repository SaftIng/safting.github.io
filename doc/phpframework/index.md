---
layout: doc
title: Saft PHP Framework
---

The _Saft PHP Framework_ consists of:

- Saft - Library. Here are all important classes of Saft located. It consists of different part which will be described below.

- Skeleton (saft.skeleton) - Skeleton application. It contains additional helper classes to speed up developing using Saft library.


## Saft Library

The *Saft Library* is structured as components. Here is a short list:

<a class="btn" href="addition">Saft.addition</a>
<a class="btn" href="rdf">Saft.rdf</a>
<a class="btn" href="store">Saft.store</a>
<a class="btn" href="data">Saft.data</a>
<a class="btn" href="querycache">Saft.querycache</a>

### Saft.addition

<a class="btn" href="addition">Documentation</a>

Additions are actual implementations of the interfaces of _Saft.library_, for instance a cache or store adapter. Some may provide different kinds of implementations.

### Saft.rdf

<a class="btn" href="rdf">Documentation</a>

The RDF component provides interfaces for the basic RDF concepts, such as _Node_ (Namednode/URI-Resource, Literal, Blanknode) and _Statement_ (Triple and Quad). Additionally the StatementIterator provides a datastructure for just holding a list of Statements. It was designed to fit the terminology of the Semantic Web.

### Saft.store

<a class="btn" href="store">Documentation</a>

The Store component contains classes and interfaces to provide store/database access. We provide the [Store](https://github.com/SaftIng/Saft/blob/master/src/Saft/Store/Store.php) interface, which defines a minimum of methods an adapter has to implement to provide store/database access (data querying and data insert/update/deletion).

### Saft.data

<a class="btn" href="data">Documentation</a>

The Data component provides parser and serializer interfaces and classes:

- DataParser for parsing any RDF serialization and returning a StatementInterator
- DataSerializer for serializing data to any RDF serialization

### Saft.querycache

<a class="btn" href="querycache">Documentation</a>

The QueryCache component provides a layer based on our cache infrastructure to store query results and provide them later on.

## Saft Skeleton Application (saft.skeleton)
> Will be contained in some post 0.1 release

The _Saft.skeleton_ will be a collection of helper classes (such as factories, ..) and other things that helps you accelerate while build applications with _Saft_.
