---
layout: doc
title: Conventions
---

Within the _Saft_ project we have some conventions which should help us during the development process.

## Coding Standard and Coding Style

Within the PHP code we are following the _PHP Standard Recommendation_ (PSR) for [_Basic Coding Standard_ (PSR-1)](http://www.php-fig.org/psr/psr-1/) and for [_Coding Style Guide_ (PSR-2)](http://www.php-fig.org/psr/psr-2/).
If you are seeing violations to those standards (e.g. by checking the code with codesniffer) please correct them and commit them in a separate commit containing the words "fix coding standard" or "fix coding style" in the git commit message.
Such commits should contain pure coding standard resp. coding style changes and should not be mixed with functional changes.

## Naming conventions

### general names

All packages within the _Saft_ project are prefixed by `Saft`. The name of the package and its subpackages are separated by a dot, e.g. `Saft.store` (the store interface and co) and `Saft.store.virtuoso` (the store implementation using virtuoso backend).
Theses names are used for the git repositories as github and for the general communication.

### composer names

The composer packages should have names like `saft/saft-rdf`. All lower case, and using the dash `-` as word separator. This convention should align with the [suggestions made in the composer documentation](https://getcomposer.org/doc/02-libraries.md#every-project-is-a-package).
