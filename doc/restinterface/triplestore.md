---
layout: doc
title: Triple Operations Store Interface
---

The light weight REST Store API.

> Maybe we should also consider the [SPARQL 1.1 Graph Store HTTP Protocol](http://www.w3.org/TR/2013/REC-sparql11-http-rdf-update-20130321/) but it doesn't seam to cover all of our requirements.

# Exploring-API

For reading access to the Store.

## Request

## HTTP-Header

### Accept

Prefered value: application/json

Possible values are overall: 

- application/json
- text/turtle
  - alternatives: application/x-turtle, application/turtle
- application/n-triples, 
- text/nquads

**Important note:** It is called *prefered* value and not *default* value, because it is not guarantueed that the later implementation supports it and so you should not rely on it. Instead, add a full list of accepted content types.

### Required parameters

- `s` = subject URI or * (empty)
- `p` = predicate URI or * (empty)
- `o` = object URI or Literal or * (empty)
- `ot` = object type: keyword `uri`/`literal` (mandatory only if `o` is specified)

### Optional parameters

- `lt` = literal type: language tag (e.g. en_US) or URI or * (empty), `http://www.w3.org/2001/XMLSchema#string` is default if parameter `ot`=`literal`, `*` if parameter `ot`=`uri`
- `action` = `get` is default; possible verbs: add, ask, count, delete, get
- `limit` = `0` is default, integer, equal or higher as 0; indicates the start id in a set of statements
- `offset` = `null` (empty) is default, integer, equal or higher as 1; indicates the amount of statements put into the result set
- `graphUri` = URI of default graph is default; URI of the graph to send the query to (an implementation may not support certain actions on the default graph)
- `case_insensitive` = `true` is default; is the query case insensitive or not
- `reasoning_on` = `false` is default; activate reasoning while query handling

# Manipulate API

todo: add delete
todo: neccessary to split exploring and manipulating API?
