---
layout: doc
title: Test Environment
---

# Test Environment

For seting up the test environment you have to

1. install [phpunit](https://phpunit.de/) (it should come with `composer install`)
2. copy `test-config.yml.dist` to `test-config.yml` in the saft root directory
3. install all requirements of the [shipped back-ends](backends#shipped-back-endss)

Now you should be able to run the test suite with a simple

    phpunit

in the saft root directory.
After running the test suite you will find a code coverage report in `<saft root>/gen/coverage/`.
