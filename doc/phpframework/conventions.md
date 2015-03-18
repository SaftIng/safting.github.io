---
layout: doc
title: PHP Naming and Coding Conventions
---

Within the _Saft_ project we have some conventions which should help us during the development process.

## Coding Standard and Coding Style

Within the PHP code we are following the _PHP Standard Recommendation_ (PSR) for [_Basic Coding Standard_ (PSR-1)](http://www.php-fig.org/psr/psr-1/) and for [_Coding Style Guide_ (PSR-2)](http://www.php-fig.org/psr/psr-2/).
If you are seeing violations to those standards (e.g. by checking the code with codesniffer) please correct them and commit them in a separate commit containing the words "fix coding standard" or "fix coding style" in the git commit message.
Such commits should contain pure coding standard resp. coding style changes and should not be mixed with functional changes.

## Naming conventions

Naming in _Saft_ is relevant in different contexts. There are the general names, which are used throughout this documentation and for the repos on github. There are names used for the composer packages and we have to handle the namespaces in the PHP-code as well as class names for interface, abstract classes and implementations.

### general names

All packages within the _Saft_ project are prefixed by `Saft`. The name of the package and its subpackages are separated by a dot, e.g. `Saft.store` (the store interface and co) and `Saft.store.virtuoso` (the store implementation using virtuoso backend).
Theses names are used for the git repositories as github and for the general communication.

> **Alternative Proposal** create a flat naming schema here, e.g. `Saft.redland`, because in this case redland implements interfaces from `Saft.store` as well as `Saft.rdf` and `Saft.data`.

> **Alternative Proposal** reflect the namespace scheme here and use `Saft.backend.redland` resp. `Saft.backend.virtuoso`, while one has to look into the packages to see which parts the backend actually is implementing

### composer names

The composer packages have to align with the [suggestions made in the composer documentation](https://getcomposer.org/doc/02-libraries.md#every-project-is-a-package). Thus we can't use our general names. The composer packages should have names like `saft/saft-rdf`. All lower case, and using the dash `-` as word separator (instead of the `.`).

### PHP namespaces

All namespaces in the _Saft_ project start with the PHP-namespace `\Saft\` under this namespace all classes in the subpackages are followed by the subpackage name, e.g `\Saft\Rdf\` (string with an upper case letter).

> For backends this is still under discussion. If you are developing your own backend your are safe if your are putting it under your own namespace. For backend implementations distributed under the `\Saft\` namespace one possibility is to use `\Saft\backend\<name of the implementation>` or if you are only implementing a specific interface `\Saft\<interface>\<name of the implementation>` e.g. `\Saft\Store\Virtuoso`.

* \Saft\
    * Rdf\
    * Store\
    * Data\
    * Backend\
        * _Name of the implementation_\
            * Rdf\
            * Store\
            * Data\

vs

* \Saft\
    * Rdf\
        * _Name of the implementation_\
    * Store\
        * _Name of the implementation_\
    * Data\
        * _Name of the implementation_\

The later would be harder to be managed on filesystem level.

### PHP Interfaces, Abstract Classes and Implementation

_Currently under discussion_
