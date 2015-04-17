---
layout: doc
title: Back-Ends
---

# Back-Ends

In _Saft_ we are using the concept of back-ends which are concrete implementations of a selection of interfaces of the _Saft.library_. Usually one back-end groups implementations sharing a certain methodology, technology or library.

## Shiped Back-Ends

Back-ends shiped with _Saft_ in the default distribution are:

- Virtuoso: implements the `Store` interface as adapter to OpenLink Virtuoso triple stores ([external requirements](#virtuoso-setup))
- HttpStore: implements the `Store` interface as adapter to access SPARQL-endpoints over HTTP ([external requirements](#httpstore))
- LocalStore: implements the `Store` interface for storing RDF on the local filesystem
- FileCache:
- MemcacheD: ([external requirements](#MemcacheD))
- PhpArrayCache:

## Virtuoso Setup

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## HttpStore

> TODO
>
> 1. Installation
> 2. Setup
> 3. …

## MemcacheD

> TODO
>
> 1. Installation
> 2. Setup
> 3. …
