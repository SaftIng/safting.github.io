---
layout: doc
title: Documentation
permalink: /doc/
---

## Preliminaries

For using Saft you should have a basic understanding of the [Resource Description Framework (RDF)](https://en.wikipedia.org/wiki/Resource_Description_Framework), [SPARQL](https://en.wikipedia.org/wiki/SPARQL) and the idea of the [Semantic Web](https://en.wikipedia.org/wiki/Semantic_Web).

## Structure of Saft

_Saft_ is structured in the _saft.library_ and _saft.skeleton_ with the following components:

### saft.library

* RdfConcepts: provides interfaces for Nodes (Resource, Literal, Blanknode), Statements (Triple and Quad) and Graphs. Additionally the StatementIterator as datastructure for just holding a list of Statements.
* [saft.store](store): StoreInterface with the implementations AbstractStatementPatternStore and AbstractSparqlStoreAdapter
* Data Interface with
    * DataParser for parsing any RDF serialization and returning a StatementInterator
    * DataSerializer for serializing data to any RDF serialization

### saft.additions

* saft.cache with a memcached and a file back-end
* saft.querycache

### saft.skeleton

## Contribution

This is the documentation for _Saft_. If you want to contribute to the documentation (even if it is just a typo) please feel free to fork the [site and documentation repository](https://github.com/SaftIng/safting.github.io) and create a pull request.
