---
layout: doc
title: Saft PHP Framework
---

The _Saft PHP Framework_ is structured in the _saft.library_, _saft.skeleton_ and _saft.additions_ with the following components:

## saft.library

<a class="btn" href="rdf">saft.rdf</a>
<a class="btn" href="store">saft.store</a>
<a class="btn" href="data">saft.data</a>

* [saft.rdf](rdf): provides interfaces for the basic RDF concepts, such as _Node_ (Namednode/URI-Resource, Literal, Blanknode) and _Statement_ (Triple and Quad). Additionally the StatementIterator provides a datastructure for just holding a list of Statements.
* [saft.store](store): StoreInterface with the implementations AbstractStatementPatternStore and AbstractSparqlStoreAdapter
* [saft.data](data): data interface with
    * DataParser for parsing any RDF serialization and returning a StatementInterator
    * DataSerializer for serializing data to any RDF serialization

## saft.backends
<a class="btn" href="backends">saft.backends</a>

The _Saft.backends_ are actual implementations of the interfaces of _Saft.library_ (e.g. cache, querycache, store adapters and so on) using some special methodology and technology.

## saft.skeleton
> Will be contained in some post 0.1 release

The _Saft.skeleton_ will be a collection of factories and other thing you need to actually build applications with _Saft_.

## Getting Started

### Prerequirements

For using the _Saft PHP Framework_ your system has to match at least the following prerequirements.

#### PHP

`php > 5.3.3`

#### Composer

Composer is a dependency management system for PHP projects.
You can get it at [https://getcomposer.com/](https://getcomposer.org/).
