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
