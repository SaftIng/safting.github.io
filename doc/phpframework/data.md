---
layout: doc
title: Saft.data
---

The *data* package provides interfaces for parsing and serializing RDF data in various serializations. In this package Saft already provides some concrete serializer and parser, but you can also find other ones in *Saft.addition*.

## Supported Serializations

We support the following serializations using the following string representation, which means, that we identify a serialization using one of the following terms:

- rdf-json
- json-ld
- rdfa
- rdf-xml
- n-triples
- n-quads
- turtle
- trig

So, if you want to serialize a string you must use of these terms to set your serialization. 

In the following you will find two overviews about the supported serialization of our parser and serializer implementations. Most of the serialize and parsing work will be transfered to foreign libraries, such as EasyRdf.

### Parser

The following table contains an overview which serialization is supported by our parser implementations.

Serialization | Saft\Addition\EasyRdf | Saft\Data
------------- | --------------------- | ---------
rdf-json      | X                     |
json-ld       |                       |
rdfa          | X                     |
rdf-xml       | X                     |
n-triples     | X                     |
n-quads       |                       | 
turtle        | X                     |
trig          |                       |


### Serializer

The following table contains an overview which serialization is supported by our serializer implementations.

Serialization | Saft\Addition\EasyRdf | Saft\Data
------------- | --------------------- | ---------
rdf-json      | X                     |
json-ld       |                       |
rdfa          | X                     |
rdf-xml       | X                     |
n-triples     | X                     |
n-quads       |                       | X
turtle        | X                     |
trig          |                       |


### Serialization to MIME-Type conversion

Serialization | MIME-Type
------------- | ---------
rdf-json      | application/json
json-ld       | application/json
rdfa          | text/html
rdf-xml       | application/rdf+xml
n-triples     | application/n-triples
n-quads       | application/n-quads
turtle        | text/turtle (application/x-turtle, application/turtle)
trig          | application/trig`

Related issue:
- https://github.com/SaftIng/Saft/issues/37
