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

For backend implementations distributed under the `\Saft\` namespace you should use `\Saft\Backend\<name of the implementation>` e.g. `\Saft\Backend\Virtuoso\…`.
If you are developing your own backend your are safe if you are putting it under your own namespace.

The namespace structure should be reflected on the filesystem level.

* `\Saft\`
    * `Rdf\`
    * `Data\`
    * `Store\`
    * `Sparql\`
    * `Addition\`
        * _Name of the implementation_`\`
            * `Rdf\`
            * `Data\`
            * `Store\`
            * _Custom Subpackages_`\`
            * …

### PHP Interfaces, Abstract Classes and Implementation

_Currently under discussion_

If we have a concept (e.g. `Statement`, `Store`) we want to support with _Saft_ we are implementing it as follows:
The Structure is expressed in an `interface`, method which are common to all or some defined set of implementations of the concept are implemented in an `abstract class`. If we also want to provide some basic implementation of the interface we should try to keep the system requirements as low as possible and only use standard PHP functions.

The `abstract class` should try to make as view assumptions about the implementations and should only communicate with the implemantation via methods, which are implemented by the implementation.

The naming of those items is as follows, using the example of the

- `Statement`: `interface Statement`,
- `abstract class AbstractStatement implements Statement` and
- `class StatementImpl extends AbstractStatement`.

Or looking at the `Store` it should be

- `interface Store`,
- `abstract class AbstractSparqlStore implements Store` vs. `abstract class AbstractTriplePatternStore implements StoreInterface` and e.g.
- `class ArrayStoreImpl extends AbstractTriplePatternStore`.

## Test Cases

If you write test cases for Saft, please follow these conventions:

- TestCases: Group test functions together, if they test the same function
- TestCases: Alphabetical order of groups of test functions.
- Alphabetical order for use-statements.

These improve readability and make it easier to find tests for a certain method. If the method are spread out over the whole document, its very hard to keep track, what cases for the method were tested and which not. That will be even more difficult, if that is not your code.
