---
layout: doc
title: Implementation Conventions
---

## General

### Handling and storing of constructor parameters

That convention affects all implementations of a Saft interface. If you pass a parameter to the constructor and want to save later on, it must be stored in a *private* property. Saft interfaces do not specify how to initialize a class, because of that, you can not be sure to be able to re-use certain properties, if you create a subclass of such a class. Sure, you can look into the class you wanna create a subclass from, but there has to be a standard way, if you can rely on the usage of such properties or not. We decided, that you can *not*.

#### Example

Here is some example code:

```php
class Foo 
{
  private $bar;
  public function __construct($bar)
  {
    $this->bar = $bar;
  }
}
```

