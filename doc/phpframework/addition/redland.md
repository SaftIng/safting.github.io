---
layout: doc
title: Redland (librdf)
---

## Requirements 

Requires the php extensions `redland` which is provided by the package `php5-librdf` in [debian](https://packages.debian.org/stable/php5-librdf) and [ubuntu](http://packages.ubuntu.com/trusty/php5-librdf).

## Installation

### Ubuntu/Debian

* Install PHP5 extension `librdf` via `sudo apt-get install php5-librdf`

### Configure

Adapting php.ini is neccessary to make sure the redland.so is loaded. You must adapt the php.ini in `/etc/php5/cli/php.ini` and add in the section `Dynamic Extensions` the following: `extension=redland.so`

Same procedure for `/etc/php5/apache2/php.ini`. Restart apache2 service after you are done.

Further information about the redland php bindings are available at: [http://librdf.org/docs/php.html](http://librdf.org/docs/php.html)
