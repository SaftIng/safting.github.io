---
layout: doc
title: Available Additions
---

In _Saft_ we are using the concept of additions which are concrete implementations of a selection of interfaces of the _Saft.library_. Usually one addition groups implementations sharing a certain methodology, technology or library.

The following list contains additions shipped with _Saft_ in the default distribution.

## ARC2

<a class="btn" href="ARC2">More information</a>

This backend provides a Store adapter which utilizes ARC2 for storing RDF data in a MySQL database. ARC2 itself also provides serializer and parser for a couple of RDF serializations. It is planned to support that too.

Saft supports ARC2 for storing RDF in a MySQL database.

## Erfurt

The [Erfurt framework](https://github.com/AKSW/Erfurt) is a mature Semantic Web API for Social Semantic Software. It provides a good query cache solution we wanted to provide through Saft.

## EasyRdf

EasyRdf is a PHP library designed to make it easy to consume and produce RDF. They provide a good parsing and serialization infrastructure which we support through that addition. If you need more of EasyRdf that addition helps you to use their stuff inside of Saft.

## HttpStore

<a class="btn" href="httpstore">More information</a>

Store adapter to access SPARQL-endpoints over HTTP.

## QueryCache

<a class="btn" href="querycache">More information</a>

Our implementation of a query cache solution. It helps you to minimize database load by caching SPARQL queries. Furthermore, if something changed in the data, the query cache is able to recognize that and adapt its cached entries.

## Redland

<a class="btn" href="redland">More information</a>

Provides data serializer and parser. Implements the _Saft.data_ and _Saft.Rdf_ interfaces.

## Virtuoso

<a class="btn" href="virtuoso">More information</a>

Store adapter to OpenLink's [Virtuoso Universal Server](http://virtuoso.openlinksw.com/). It provides triple/quad store functionality as well as RDBMS functionality.
