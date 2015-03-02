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

- **statements**: \Saft\Sparql\StatementList
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
    - In a quad the target graph is determined. But if you want to override that behavior, you must set *graphUri* parameter, so all matching statements of that graph will be deleted instead.

- **options**: array (optional, standard is empty array, e.g. array())
  - This parameter contains key-value pairs and should provide additional introductions for the store and/or its adapter(s).
 
*Return value*: Returns true, if function performed without errors. In case an error occur, an exception will be thrown.

#### getMatchingStatements

It gets all statements of a given graph which match the following conditions:
- _statement_'s subject is either equal to the subject of the same statement of the graph or it is null.
- _statement_'s predicate is either equal to the predicate of the same statement of the graph or it is null.
- _statement_'s object is either equal to the object of a statement of the graph or it is null.

*Parameter*:

- **statement**: \Saft\Sparql\Statement
  - It can be either a concrete or pattern-statement.
  - A concrete statement is considered with subject, predicate and object are defined, e.g. <http://foobar/>.
  - A pattern statement is considered with at least one of subject, predicate or object is a pattern, e.g. ?s.

- **graphUri**: string (optional, Standard is null)
  - In case you wanna get Triples (Statement instance contains s, p and o):
    - Set parameter *graphUri* to determine the graph where you wanna get triple-statements from. If *graphUri* is invalid (empty or not a valid URI or graph is not available), you will get nothing.
  - In case you wanna add Quads (Statement instance contains s, p, o and graph):
    - In a quad the target graph is determined. But if you want to override that behavior, you must set *graphUri* parameter, so that you will get all matching statements of that graph.

- **options**: array (optional, standard is empty array, e.g. array())
  - This parameter contains key-value pairs and should provide additional introductions for the store and/or its adapter(s).

*Return value*: Returns an instance of \Saft\Sparql\StatementList which contains \Saft\Sparql\Statement instances of all matching statements of the given graph.

#### hasMatchingStatement

Returns true or false depending on whether or not the statements pattern has any matches in the given graph.

*Parameter*:

- **statement**: \Saft\Sparql\Statement
  - It can be either a concrete or pattern-statement.
  - A concrete statement is considered with subject, predicate and object are defined, e.g. <http://foobar/>.
  - A pattern statement is considered with at least one of subject, predicate or object is a pattern, e.g. ?s.

- **graphUri**: string (optional, Standard is null)
  - In case you wanna check for Triples (Statement instance contains s, p and o):
    - Set parameter *graphUri* to determine the graph where to match triple-statements. If *graphUri* is invalid (empty or not a valid URI or graph is not available), no matching will be done.
  - In case you wanna check for Quads (Statement instance contains s, p, o and graph):
    - In a quad the target graph is determined. But if you want to override that behavior, you must set *graphUri* parameter, so that it match statements of that graph.

- **options**: array (optional, standard is empty array, e.g. array())
  - This parameter contains key-value pairs and should provide additional introductions for the store and/or its adapter(s).

*Return value*: Returns true if at least one match was found, false otherwise.
