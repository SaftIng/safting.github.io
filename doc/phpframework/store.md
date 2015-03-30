---
layout: doc
title: saft.store
---

Package _saft.store_ consists of Triple- and Quadstore related classes and interfaces. Its purpose is to provide a foundation to built a store implementation on.

## Main parts

### StoreInterface

It describes, which methods a store implementation has to provide. We propose to implement it in other languages if you need a store implementation, to have the best compatibility between different implementations. 

Documentation [here](storeinterface.md).

### Store Chain

A store chain consists of components to basically return results for given queries. It is modular and can be configured by the developer depending on his needs. For instance, if you just need store access, you can use a chain consisting of a query logger and a store adapter. Another example are environments with high server load, in that case you can use access control, together with a query cache and a store adapter.

Documentation [here](storechain.md).


