---
layout: doc
title: RDF core component
---

The Saft RDF library provides interfaces for the basic RDF concepts, such as _Node_ (Named Node/URI-Resource, Literal, Blanknode) and _Statement_ (Triple and Quad). Additionally the StatementIterator provides a data structure for just holding a list of Statements.

## Main interfaces

We provide interfaces which describe basic RDF concepts, such as a node. For each interface we alsow provide a standard implementation. If you need to change the behavior of a standard implementation, just extend it or create a fresh class which implements the related interface(s).

**List of RDF specific interfaces:**
  * Node
  * Literal
  * NamedNode
  * BlankNode
  * Statement
  * AnyPattern

Each has a related classes, suffixed with Impl, e.g. [NamedNodeImpl](https://github.com/SaftIng/Saft/blob/master/src/Saft/Rdf/NamedNodeImpl.php). That is a standard implementation and is ready to use. Saft internally only checks for the interfaces to be implemented, not for certain classes. Because of that approach, you are able to provide your own implementation without working against Saft. That was the case for the Redland addition. They handled RDF data a certain way and using this approach, we could implement a wrapper for Redland specific stuff to be able to use that library inside of Saft. That said, you really should not rely on a certain implementation rather to implement it yourself. Our Impl-classes may change in the near future, only the interface will remain stable.

There are a few [examples](https://github.com/SaftIng/Saft.example) to help you understand how the stuff is working.
