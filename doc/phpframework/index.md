---
layout: doc
title: Saft PHP Framework
---

The _Saft PHP Framework_ is structured in the _saft.library_, _saft.skeleton_ and _saft.additions_ with the following components:

## saft.library

* RdfConcepts: provides interfaces for Nodes (Resource, Literal, Blanknode), Statements (Triple and Quad) and Graphs. Additionally the StatementIterator as datastructure for just holding a list of Statements.
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
