---
layout: doc
title: Triple Operations Store Interface
---

The light weight REST Store API.

## explore API

For reading access to the Store

### GET/POST Parameter

- `s p o ot lt`
    - `s` = subject URI or * (empty)
    - `p` = predicate URI or * (empty)
    - `o` = object URI or Literal or * (empty)
    - `ot` = object type: keyword `uri`/`literal` (mandatory only if `o` is specified)
    - `lt` = literal type: language tag or URI or * (empty)
- more options
    - `action`/`verb` (get is default, possible verbs: get, delete, count, ask)
    - `limit`
    - `offset`
    - `graph`
    - `case_insensitive`
    - `reasoning_on`

### REQUEST Parameter

- Accept: text/json-ld (default), possible values: text/turtle, text/ntriples, text/nquad (Comment by @nate: we shouldn't give a default here, because implementations could want other defaults, e.g. an HTML representation.)

## manipulate API

todo: add delete
