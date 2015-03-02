---
layout: doc
title: saft.store
---

Package _saft.store_ consists of Triple- and Quadstore related classes and interfaces. Its purpose is to provide a foundation to built a store implementation on.

> The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).

## StoreInterface

The _StoreInterface_ describes, which methods a store implementation has to provide. We propose to implement it in other languages if you need a store implementation, to have the best compatibility between different implementations.

### Methods

#### getAvailableGraphs

Returns a list of all available graph URIs of the store. It also can include access control, to check if the user has the rights to see certain graphs. 

*Parameter*: none

*Return value*: Array, which contains available graph URI's, whereby the keys and values are graph URIs.


#### addStatements

Adds multiple Statements to (default-) graph. 

*Parameter*:

- **statements**: StatementList
  - *statements* must contain Statement instances.
  - Statement instances must be concrete- and not pattern-statements, such as ?s ?p ?o. 
  - In case *statements* is empty, nothing will be added.

- **graphUri**: string (optional, Standard is null)
  - In case you wanna add Triples (Statement instance contains s, p and o):
    - Set parameter *graphUri* to determine the graph all the statements has to add to. If *graphUri* is invalid (empty or not a valid URI or graph is not available), nothing will be added.
  - In case you wanna add Quads (Statement instance contains s, p, o and graph):
    - In a quad the target graph is determined. But if you want to override that behavior, you can set *graphUri* parameter. In that case all statements of *statements* will be added to the graph defined by *graphUri*.
 
- **options**: array (optional, standard is empty array, e.g. array())
  - This parameter contains key-value pairs and should provide additional introductions for the store and/or its adapter(s).

*Return value*: Returns true, if function performed without errors. In case an error occur, an exception will be thrown.

#### deleteMatchingStatements

Removes all statements from a (default-) graph which match with given statement. 

*Parameter*:

- **statement**: \Saft\Sparql\Statement
  - It can be either a concrete or pattern-statement.
  - A concrete statement is considered with subject, predicate and object are defined, e.g. <http://foobar/>.
  - A pattern statement is considered with at least one of subject, predicate or object is a pattern, e.g. ?s.

- **graphUri**: string (optional, Standard is null)
  - In case you wanna delete Triples (Statement instance contains s, p and o):
    - Set parameter *graphUri* to determine the graph where all the statements will be deleted. If *graphUri* is invalid (empty or not a valid URI or graph is not available), nothing will be deleted.
  - In case you wanna add Quads (Statement instance contains s, p, o and graph):
    - In a quad the target graph is determined. But if you want to override that behavior, you can set *graphUri* parameter, so all matching statements of that graph will be deleted instead.

 - **options**: array (optional, standard is empty array, e.g. array())
  - This parameter contains key-value pairs and should provide additional introductions for the store and/or its adapter(s).
 
*Return value*: Returns true, if function performed without errors. In case an error occur, an exception will be thrown.
