---
layout: doc
title: Triple Operations Store Interface
---

The light weight REST Store API.

> Maybe we should also consider the [SPARQL 1.1 Graph Store HTTP Protocol](http://www.w3.org/TR/2013/REC-sparql11-http-rdf-update-20130321/) but it doesn't seam to cover all of our requirements.

## Exploring-API

For reading access to the Store.

### GET/POST Parameter

- `s` = subject URI or * (empty)
- `p` = predicate URI or * (empty)
- `o` = object URI or Literal or * (empty)
- `ot` = object type: keyword `uri`/`literal` (mandatory only if `o` is specified)
- `lt` = literal type: language tag (e.g. en_US) or URI or * (empty), `http://www.w3.org/2001/XMLSchema#string` is default if parameter `ot`=`literal`, `*` if parameter `ot`=`uri`

#### More options

- `action` = `get` is default; possible verbs: get, delete, count, ask
- `limit` = `0` is default, integer, equal or higher as 0; indicates the start id in a set of statements
- `offset` = `null` (empty) is default, integer, equal or higher as 1; indicates the amount of statements put into the result set
- `graphUri` = URI of the graph to send the query to
- `case_insensitive` = `true` is default; is the query case insensitive or not
- `reasoning_on` = `false` is default; activate reasoning while query handling

### REQUEST Parameter

Accept: text/json-ld (default)

Possible values are: 

- text/turtle, 
- text/ntriples, 
- text/nquad 

(Comment by @nate: we shouldn't give a default here, because implementations could want other defaults, e.g. an HTML representation.)

## manipulate API

todo: add delete
