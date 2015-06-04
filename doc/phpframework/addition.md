---
layout: doc
title: Back-Ends
---

In _Saft_ we are using the concept of back-ends which are concrete implementations of a selection of interfaces of the _Saft.library_. Usually one back-end groups implementations sharing a certain methodology, technology or library.

## Back-Ends

The following list contains back-end shipped with _Saft_ in the default distribution.

### Virtuoso

<a class="btn" href="virtuoso">More information</a>

Store adapter to OpenLink's [Virtuoso Universal Server](http://virtuoso.openlinksw.com/). It provides triple/quad store functionality as well as RDBMS functionality.

### HttpStore

<a class="btn" href="httpstore">More information</a>

Store adapter to access SPARQL-endpoints over HTTP. 

### ARC2

<a class="btn" href="ARC2">More information</a>

This backend provides a Store adapter which utilizes ARC2 for storing RDF data in a MySQL database. ARC2 itself also provides serializer and parser for a couple of RDF serializations. It is planned to support that too.

Saft supports ARC2 for storing RDF in a MySQL database. 

### MemcacheD

Cache adapter to store cache entries in the RAM using MemcacheD daemon. 

Requires the php extension `memcached` which is provided by the package `php5-memcached` in [debian](https://packages.debian.org/stable/php5-memcached) and [ubuntu](http://packages.ubuntu.com/trusty/php5-memcached) and the memcached (daemon), which is provided by the package `memcached` in [debian](https://packages.debian.org/stable/memcached) and [ubuntu](http://packages.ubuntu.com/trusty/memcached)

### Redland

Provides data serializer and parser. Implements the _Saft.data_ and _Saft.Rdf_ interfaces.

Requires the php extensions `redland` which is provided by the package `php5-librdf` in [debian](https://packages.debian.org/stable/php5-librdf) and [ubuntu](http://packages.ubuntu.com/trusty/php5-librdf).
The PHP extension is probably not activated automatically after the installation.
To enable it you have to add a symlink to `/etc/php5/cli/conf.d` pointing to `/etc/php5/mods-available/redland.ini` (if you want to use it with a webserver replace `cli` with `fpm` or `apache2` respectively).

Further information about the redland php bindings are available at: [http://librdf.org/docs/php.html](http://librdf.org/docs/php.html)
