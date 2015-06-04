---
layout: doc
title: Saft.data
---

The *data* package provides interfaces for parsing and serializing RDF data in various serializations. In this package Saft already provides some concrete serializer and parser, but you can also find other ones in *Saft.addition*.

## Supported Serializations

We support the following serializations using the following string representation, which means, that we identify a serialization using one of the following terms:

- json-ld
- n-quads
- n-triples
- rdf-json
- rdf-xml
- rdfa
- trig
- turtle

So, if you want to serialize a string you must use of these terms to set your serialization. 

In the following you will find two overviews about the supported serialization of our parser and serializer implementations. Most of the serialize and parsing work will be transfered to foreign libraries, such as EasyRdf.

### Parser

The following table contains an overview which serialization is supported by our parser implementations.

Serialization | Saft\Addition\EasyRdf | Saft\Data
------------- | --------------------- | ---------
json-ld       |                       |
n-triples     | X                     |
n-quads       |                       | 
rdf-xml       | X                     |
rdf-json      | X                     |
rdfa          | X                     |
trig          |                       |
turtle        | X                     |


### Serializer

The following table contains an overview which serialization is supported by our serializer implementations.

Serialization | Saft\Addition\EasyRdf | Saft\Data
------------- | --------------------- | ---------
json-ld       |                       |
n-triples     | X                     |
n-quads       |                       | X
rdf-xml       | X                     |
rdf-json      | X                     |
rdfa          | X                     |
trig          |                       |
turtle        | X                     |


### Serialization to MIME-Type conversion

Serialization | MIME-Type
------------- | ---------
json-ld       | application/json
n-triples     | application/n-triples
n-quads       | application/n-quads
rdf-json      | application/json
rdf-xml       | application/rdf+xml
rdfa          | text/html
trig          | application/trig
turtle        | text/turtle (application/x-turtle, application/turtle)

Related issue:
- https://github.com/SaftIng/Saft/issues/37
