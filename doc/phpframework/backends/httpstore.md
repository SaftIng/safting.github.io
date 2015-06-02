---
layout: doc
title: HttpStore
---

## Setup Virtuoso as SPARQL endpoint for HTTP requests

### Setup

To be able to execute both SPARQL SELECT and UPDATE queries, you have to do the following steps.

#### 1. Use Virtuoso 6.1.8 or newer

Only Virtuoso 6.1.8 and higher supports SPARQL UPDATE queries via HTTP. Have no Ubuntu package? Have a look [here for 6.1.8](https://github.com/k00ni/virtuoso-upstream/releases) or [here for 7.x](http://virtuoso.openlinksw.com/dataspace/doc/dav/wiki/Main/VOSDownload).

#### 2. User account for WebDAV

Create a new user via the [Conductor](http://localhost:8890/conductor/) with the following configuration:
- Set username and password (remember it and set it in the test-config.yml in your Saft root folder) 
- **User Enabled** must be checked
- **User Type:** SQL/ODBC and WebDAV
- **Primary Role:** SPARQL_SELECT
- **Account Roles Selected:** SPARQL_SELECT

This user will be used for Digest Authentication.

#### 3. Role adaption for SPARQL user

Edit the existing **SPARQL** user and add **SPARQL_UPDATE** under **Account Roles Selected**.

### Troubleshooting

- If you get **Virtuoso 42000 Error SR186: No permission to execute procedure DB.DBA.SPARUL_DROP with user ID 106, group ID 106** you probably missed **3. Role adaption for SPARQL user**, didn't you?

- If you get HTTP status code 406 in a response, try using GET instead of POST. Furthermore, check value of **Accept** header, maybe it could not be understand by the Virtuoso server.

- If you send a query via HTTP such as ```select ?s ?p ?o (DATATYPE(?o)) as ?otype (LANG(?o)) as ?olang WHERE {<". $resourceUri ."> ?p ?o.}``` to add datatype and language information, with Virtuoso 6.1.8, you will run into the following error: ```Virtuoso 22023 Error SR544: Function __xsd_type() can not find XML Schema datatype that matches SQL datatype UNAME (217)```
It seems they fixed that bug for **Virtuoso 7.1+**. For more information look into this [issue](https://github.com/openlink/virtuoso-opensource/issues/247).