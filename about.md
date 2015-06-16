---
layout: doc
title: About
permalink: /about/
---

## Saft

### ... is a collection of lightweight components

Saft is the aim to build a collection of components which helps you to create applications by using Semantic Web/Linked Data technology. The main goal of Saft is to provide a full fledged middleware, which supports a wide range of use cases in the Semantic Web field, from data consuming, data manipulation, querying and database/store interaction. The project structure can be devided into [_saft.library_](/doc/phpframework), containing interfaces and components which can be included in any existing application structure, and the [_saft.skeleton_](/doc/phpframework), which helps developers to bootstrap an application from the scratch.

### ... is an integration platform

Saft is also an integration platform, which integrates for foreign libraries and technologies, such as [ARC2](https://github.com/semsol/arc2), [EasyRdf](http://www.easyrdf.org/) or [Redland](http://librdf.org/). They will be used, for instance, for parsing/serialization or triple store access. Saft handles the configuration and setup and appears as one API for the user. But he has the option to opt-in, if he wants.

#### Basic illustration

<img src="http://safting.github.io/doc/integrationplatform.png" style="width: 80%; border: 0px;" >

This image illustrates the integration platform. The core components provide basic functionality and interfaces. They build the basement for Saft.Addition, which contains real implementations, organized as components as well. Each addition has its own purpose. 

For instance Saft.Addition.ARC2: It uses the foreign ARC2 library to provide a database adapter to use a MySQL database as triple store. To do so, it implements/extends existing classes and interfaces to connect with their ARC2 pendants.

### ... is compatible and open

One of the main goals of Saft is to be open and compatible. For instance:

- it is published under the terms of the [GPL](https://github.com/SaftIng/Saft/blob/master/LICENSE)
- it supports [PSR-7](http://www.php-fig.org/psr/psr-7/) for HTTP-handling (see [REST](https://github.com/SaftIng/Saft.skeleton/tree/master/src/Saft/Skeleton/Rest) API of Saft.skeleton)
- it embraces open standards, like the ones from the W3C or PHP-FIG (PHP Framework Interop Group)
- provides a public REST interface [specification](http://safting.github.io/doc/restinterface/). 
 
Saft is also open for participation and welcomes code, bug reports, translations, ... any help from people, who want to help.


## Short historical overview

The founders of Saft and SaftIng previously worked, some still are working, on Erfurt the PHP/Zend based Semantic Web Framework, which is the foundation e.g. for the collaborative Semantic software OntoWiki and the node for the Distributed Semantic Social Network Node xodx. [k00ni](https://github.com/k00ni) created Enable in 2013/2014 during his study as a lightweight alternative to Erfurt. After half a year, he teamed up with the OntoWiki and Erfurt maintainer [white_gecko](https://github.com/white-gecko) and they decided to establish a fully fledged collection of components to build applications by using Semantic Web and Linked Data technology. They used their experience with Erfurt and code from Enable to start. These two were joined by vitaB, who mostly contributed code to the Store and REST components and by Oliver Skawronek, who layed the ground for a file based triple store.

## What is SaftIng?

SaftIng stands for *Semantic Application Framework Saft Engineering Taskforce* (Saft.Ing), which is a group of developers with a strong background in Semantic Web and Linked Data technology.
