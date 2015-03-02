---
layout: doc
title: saft.store
---

Package _saft.store_ consists of Triple- and Quadstore related classes and interfaces. Its purpose is to provide a foundation to built a store implementation on.

## Content 

### StoreInterface

The _StoreInterface_ describes, which methods a store implementation has to provide. We propose to implement it in other languages if you need a store implementation, to have the best compatibility between different implementations.

#### Methods

##### getAvailableGraphs

Returns a list of all available graph URIs of the store. It also can include access control, to check if the user has the rights to see certain graphs. 

**Parameter**: none

**Return value**: 
- array: It contains available graph URI's, whereby the keys and values are graph URIs.


##### addStatements

Adds multiple Statements to (default-) graph. 
