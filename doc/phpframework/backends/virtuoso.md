---
layout: doc
title: Virtuoso
---

Store adapter to OpenLink's [Virtuoso Universal Server](http://virtuoso.openlinksw.com/). It provides triple/quad store functionality as well as RDBMS functionality.

## Requirements

* PHP extensions `odbc` and `pdo_odbc` must be installed and loaded. They are provided by the package `php5-odbc` in [debian](https://packages.debian.org/stable/php5-odbc) and [ubuntu](http://packages.ubuntu.com/trusty/php5-odbc)

## Installation

For more information how to install and setup a Virtuoso Universal Server please have a look here: http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSBuild

Further information may be found here:
- https://github.com/AKSW/OntoWiki/wiki/VirtuosoBackend
- https://logd.tw.rpi.edu/tutorial/installing_using_virtuoso_sparql_endpoint

We prefer to install Virtuoso using the according packages for your operating system. For instance, Virtuoso Universal Server is part of the extended software collection of Debian and Ubuntu. Please ask questions, how to install Virtuoso on your machine, in the Virtuoso [issue tracker](https://github.com/openlink/virtuoso-opensource/issues) or related channels (mailing list, forum, ...)
