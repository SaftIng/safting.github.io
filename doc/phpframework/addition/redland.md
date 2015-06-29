---
layout: doc
title: Redland (librdf)
---

## Installation

### Ubuntu/Debian

* Install PHP5 extension `librdf` via `sudo apt-get install php5-librdf`
* *Sometimes adapting php.ini is neccessary to make sure the redland.so is loaded. See troubleshooting for more info.*

## Troubleshooting

### Missing redland.so (PHP-CLI)

If you get errors about the missing `redland.so` to be loaded, for instance in composer: 

> The requested PHP extension ext-librdf * is missing from your system.

You must adapt the php.ini in `/etc/php5/cli/php.ini` and add in the section `Dynamic Extensions` the following line: `extension=redland.so`

So here is an example how that section could look like afterwards:

```ini
;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;

; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
; For example, on Windows:
;
;   extension=msql.dll
;
; ... or under UNIX:
;
;   extension=msql.so
;
; ... or with a path:
;
;   extension=/path/to/extension/msql.so
;
; If you only provide the name of the extension, PHP will look for it in its
; default extension directory.
;
extension=redland.so
```
