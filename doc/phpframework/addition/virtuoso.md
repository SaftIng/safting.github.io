---
layout: doc
title: Virtuoso
---

Store adapter to OpenLink's [Virtuoso Universal Server](http://virtuoso.openlinksw.com/). It provides triple/quad store functionality as well as RDBMS functionality.

## Requirements

* PHP extensions `odbc` and `pdo_odbc` must be installed and loaded. They are provided by the package `php5-odbc` in [debian](https://packages.debian.org/stable/php5-odbc) and [ubuntu](http://packages.ubuntu.com/trusty/php5-odbc)
* at least Virtuoso Universal Server **6.1.8** installed and running

## Installation

### General

To install and setup a Virtuoso Universal Server please have a look here: http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSBuild

Further information may be found here:
- https://github.com/AKSW/OntoWiki/wiki/VirtuosoBackend
- https://logd.tw.rpi.edu/tutorial/installing_using_virtuoso_sparql_endpoint

We prefer to install Virtuoso using the according packages for your operating system. For instance, Virtuoso Universal Server is part of the extended software collection of Debian and Ubuntu. Please ask questions, how to install Virtuoso on your machine, in the Virtuoso [issue tracker](https://github.com/openlink/virtuoso-opensource/issues) or related channels (mailing list, forum, ...)

### Ubuntu and Debian related

The Linked Data Stack provides a repository to install dozens of packages related to the Semantic Web: http://stack.linkeddata.org/getting-started/installing-components

The following sub-sections describe how to install Virtuoso 7.1 in the system. For further information please have a look into according links, because the Saft team does not provide further Virtuoso support.

#### Ubuntu 14.04

Introductions to install Virtuoso 7.1:

* download the repository package:  `wget http://stack.linkeddata.org/ldstable-repository.deb`
* install the repository package: `sudo dpkg -i ldstable-repository.deb`
* update the repository database: `sudo apt-get update`

Unfortunately, the Linked Data Stack does not contain all packages needed. So you need to add the following line to `/etc/apt/sources.list`:

> deb http://security.ubuntu.com/ubuntu precise-security main 

After that run the following two commands to install Virtuoso Universal Server 7.1:
* `sudo apt-get update`
* `sudo apt-get install virtuoso-opensource-7.1 virtuoso-opensource-7.1-bin libvirtodbc0 libiodbc2`

The reason for these additional steps is, that Virtuoso 7.1 needs `libmagickwand4`, but it is not part of Ubuntu 14.04 repositories anymore.

## Usage

### Query the store

#### Available options

You can set certain options to be used to setup the environment the query will be executed in. The following list contains what is support by the Virtuoso addition.

* **output_format** - (Default: json) - Output format of the result. If set to json, Virtuoso will provide further information about the result. If it is not set, the store will automatically use *json*.
  * json
  * *empty*, means not set
* **default_graph_uri** - (Default: *empty*) - Set a default graph to be used if no FROM clause is set.
  * e.g. http://foo/

## Troubleshooting

### Graph info in statement

If you getting such errors:

> Exception: SQLSTATE[42000]: Syntax error or access violation: 0 [OpenLink][Virtuoso iODBC Driver][Virtuoso Server]SQ074: Line 1: SP030: SPARQL compiler, line 1: syntax error at '{' before 'Graph' (SQLPrepare[0] at /build/buildd/php5-5.5.9+dfsg/ext/pdo_odbc/odbc_driver.c:206)

your current Virtuoso version does not understand queries like:

> INSERT DATA {Graph <http://localhost/Saft/TestGraph/> {<http://s/> <http://p/> <http://o/> . }  }

You must upgrade Virtuoso to at least version **6.1.8** or newer.

## SPARQL support

### SPARQL UPDATE 

#### Default Graph

Virtuoso does not support adding or deleting statements in the default graph. (According [issue](https://github.com/openlink/virtuoso-opensource/issues/417)). The Virtuoso addition throws an error, if you want to do that anyway.
