---
layout: doc
title: Back-Ends
---

In _Saft_ we are using the concept of back-ends which are concrete implementations of a selection of interfaces of the _Saft.library_. Usually one back-end groups implementations sharing a certain methodology, technology or library.

## Back-Ends

The following list contains back-end shipped with _Saft_ in the default distribution.

- Virtuoso - Store adapter to OpenLink Virtuoso triple stores. ([external requirements](#virtuoso))
- HttpStore - Store adapter to access SPARQL-endpoints over HTTP. ([external requirements](#httpstore))
- LocalStore - Store adapter for storing RDF on the local filesystem.
- ARC2 - This backend provides a Store adapter which utilizes ARC2 for storing RDF data in a MySQL database. ([external requirements](#arc2)) ARC2 itself also provides serializer and parser for a couple of RDF serializations. It is planned to support that too.
- FileCache - Cache adapter to store cache entries on the local filesystem.
- MemcacheD - Cache adapter to store cache entries in the RAM using MemcacheD daemon. ([external requirements](#memcached))
- Redland: Provides data serializer and parser. Implements the _Saft.data_ and _Saft.Rdf_ interfaces.

## Virtuoso

### Requirements

* PHP extensions `odbc` and `pdo_odbc` must be installed and loaded. They are provided by the package `php5-odbc` in [debian](https://packages.debian.org/stable/php5-odbc) and [ubuntu](http://packages.ubuntu.com/trusty/php5-odbc)

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## HttpStore

### Requirements 

* PHP extension `curl` must be installed and loaded. It is provided by the package `php5-curl`.

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## ARC2

Saft supports ARC2 for storing RDF in a MySQL database. 

### Setup

> TODO:
> add link to examples
> short description of how to setup

The default access credentials which Saft is trying to use are:

- username: saft
- password: saft
- database: saft

You can setup mysql accordingly with the following set of mysql commands:

    create user 'saft'@'localhost' identified by 'saft';
    create database saft;
    grant all privileges on saft.* to 'saft'@'localhost';

you can execute those commands using the `mysql` commandline tool. Or perhaps you want to use phpMyAdmin to create the user and a database. [Here](https://www.youtube.com/watch?v=lfjzAbaW32c) is a short youtube video how to accomplish that.

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

Requires the php extensions `redland` which is provided by the package `php5-librdf` in [debian](https://packages.debian.org/stable/php5-librdf) and [ubuntu](http://packages.ubuntu.com/trusty/php5-librdf).
The PHP extension is probably not activated automatically after the installation.
To enable it you have to add a symlink to `/etc/php5/cli/conf.d` pointing to `/etc/php5/mods-available/redland.ini` (if you want to use it with a webserver replace `cli` with `fpm` or `apache2` respectively).

Further information about the redland php bindings are available at: [http://librdf.org/docs/php.html](http://librdf.org/docs/php.html)
