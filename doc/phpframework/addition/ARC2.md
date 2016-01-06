---
layout: doc
title: ARC2
---

> TODO:
> add link to examples
> short description of how to setup

This backend provides a Store adapter which utilizes the PHP library [ARC2](https://github.com/semsol/arc2) for storing RDF data in a MySQL database. ARC2 itself also provides serializer and parser for a couple of RDF serializations. It is planned to support that too.

Currently, Saft supports ARC2 for storing RDF in a MySQL database. 

ARC2 provides good documentation, if you need further information: [https://github.com/semsol/arc2/wiki](https://github.com/semsol/arc2/wiki)


## Installation

Basically, you dont have to anything to setup a database to use ARC2. It is configured in a way to use the given information and to setup everything for you. It needs a database name and access information, if you want, you can also set the host and table-prefix. 

The default information which Saft is trying to use are:

- username: saft
- password: saft
- database: saft
- host: localhost
- table-prefix: saft

Of course, you can override it with your own data. ARC2 will create the database, if it has the rights and it does not exist yet. After that, all neccessary tables will be created as well.

> add link to example which demonstrate how to setup a connection

### Setup MySQL certain user and database

You can setup MySQL accordingly with the following set of SQL commands:

    create user 'saft'@'localhost' identified by 'saft';
    create database saft;
    grant all privileges on saft.* to 'saft'@'localhost';

You can execute those commands using the `mysql` commandline tool. Or perhaps you want to use phpMyAdmin to create the user and a database. [Here](https://www.youtube.com/watch?v=lfjzAbaW32c) is a short youtube video how to accomplish that.

## Compatibility

This section documents the changes on the behavior of the ARC2 adapter. ARC2 lacks certain SPARQL features, such as SPARUL or uses its own implementation ([SPARQL+](https://github.com/semsol/arc2/wiki/SPARQL%2B)). This adapter extends ARC2 to support for further SPARQL 1.0/1.1 features.

### DELETE WHERE (no quad support)

ARC2 uses SPARQL+, its own SPARQL extension, to provide data management. To remove triples, you have to use queries such as:

> DELETE FROM <http://example.com/inferred> { ?s rel:wouldLikeToKnow ?o . } WHERE { ?s kiss:kissed ?o . }

The ARC2 adapter rewrites DELETE queries with quads inside to support quads in DELETE queries anyway. What does it mean:
- Support for quads, where the graph is an URI and *not* a pattern/variable
