---
layout: doc
title: saft.store
---

_saft.store_ consists of the _StoreInterface_ with the abstract implementations _AbstractStatementPatternStore_ and _AbstractSparqlStore_.

[StoreInterface](https://github.com/AKSW/StoreInterface/blob/develop/src/Store/StoreInterface.php): is a declaration of functions that a Store must have.

[AbstractStatementPatternStore](https://github.com/AKSW/StoreInterface/blob/develop/src/Store/AbstractPatternFragmentTripleStore.php): Predefined Pattern-Statement Store. The Triple-methods need to be implemented in the specific statement-store. The query method is defined in the abstract class and reroute to the triple-methods.

[AbstractSparqlStore](https://github.com/AKSW/StoreInterface/blob/develop/src/Store/AbstractSparqlTripleStore.php): Predefined abstract sparql-Store. All Triple methods reroute to the query-method. In the specific sparql-Store those no longer have to be implemented, but only the Query method / SPARQL interpreter itself.


