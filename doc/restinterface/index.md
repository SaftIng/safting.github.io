---
layout: doc
title: Saft REST Interface
---

The _Saft REST Interface_ provides a REST-API which is available through standard HTTP.
It allows read and write access to the data in the underlaying store.

For basic triple resp. quad (statement) operations on the store we specify the [Triple Operations Store Interface](triplestore).

The _Saft REST Interface_ should also be backward compatible to normal SPARQL services/endpoints.
For SPARQL access to the underlaying store a query method should be available as described in the [SPARQL 1.1 Protocol](http://www.w3.org/TR/2013/REC-sparql11-protocol-20130321/). (The SPARQL interface should be optional for _Saft_ Stores.)
