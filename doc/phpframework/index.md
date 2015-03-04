---
layout: doc
title: Saft PHP Framework
---

The _Saft PHP Framework_ is structured in the _saft.library_, _saft.skeleton_ and _saft.additions_ with the following components:

## saft.library

<a class="btn" href="rdf">saft.rdf</a>
<a class="btn" href="store">saft.store</a>

* [saft.rdf](rdf): provides interfaces for the basic RDF concepts, such as _Node_ (Namednode/URI-Resource, Literal, Blanknode) and _Statement_ (Triple and Quad). Additionally the StatementIterator provides a datastructure for just holding a list of Statements.
* [saft.store](store): StoreInterface with the implementations AbstractStatementPatternStore and AbstractSparqlStoreAdapter
* Data Interface with
    * DataParser for parsing any RDF serialization and returning a StatementInterator
    * DataSerializer for serializing data to any RDF serialization

## saft.skeleton


## saft.additions

* saft.cache with a memcached and a file back-end
* saft.querycache

## Getting Started

### Prerequirements

For using the _Saft PHP Framework_ your system has to match at least the following prerequirements.

#### PHP

`php > 5.3.3`

#### Composer

Composer is a dependency management system for PHP projects.
You can get it at [https://getcomposer.com/](https://getcomposer.org/).
