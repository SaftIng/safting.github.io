---
layout: doc
title: Back-Ends
---

In _Saft_ we are using the concept of back-ends which are concrete implementations of a selection of interfaces of the _Saft.library_. Usually one back-end groups implementations sharing a certain methodology, technology or library.

## Shipped Back-Ends

Back-ends shipped with _Saft_ in the default distribution are:

- Virtuoso: implements the `Store` interface as adapter to OpenLink Virtuoso triple stores ([external requirements](#virtuoso-setup))
- HttpStore: implements the `Store` interface as adapter to access SPARQL-endpoints over HTTP ([external requirements](#httpstore))
- LocalStore: implements the `Store` interface for storing RDF on the local filesystem
- FileCache: implements the `Cache` interfaces
- MemcacheD: implements the `Cache` interfaces ([external requirements](#memcached))
- PhpArrayCache: implements the `Cache` interfaces

## Other Back-Ends

- Redland: implements the _Saft.data_ and _Saft.Rdf_ interfaces

## Virtuoso Setup

Requires the php extensions `odbc` and `pdo_odbc` which are provided by the package `php5-odb` in [debian](https://packages.debian.org/stable/php5-odbc) and [ubuntu](http://packages.ubuntu.com/trusty/php5-odbc)

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## HttpStore

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## MemcacheD

Requires the php extension `memcached` which is provided by the package `php5-memcached` in [debian](https://packages.debian.org/stable/php5-memcached) and [ubuntu](http://packages.ubuntu.com/trusty/php5-memcached) and the memcached (daemon), which is provided by the package `memcached` in [debian](https://packages.debian.org/stable/memcached) and [ubuntu](http://packages.ubuntu.com/trusty/memcached)

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## Redland

Requires the php extensions `redland` which is provided by the package `php5-librdf` in [debian](https://packages.debian.org/stable/php5-librdf) and [ubuntu](http://packages.ubuntu.com/trusty/php5-librdf)

Further information about the redland php bindings are available at: [http://librdf.org/docs/php.html](http://librdf.org/docs/php.html)
