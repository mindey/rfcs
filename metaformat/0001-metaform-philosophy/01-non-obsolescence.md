# 1. Non-obsolescence

## CONTEXT
- Formats like *XML, XLS, XML-RPC, SOAP* are being deprecated by app developers in favor of *JSON, XLSX, REST, OpenAPI*.
- And they evolve (YAML, Graphene, etc.)
- One day, we might have something else altogether.

## DEFINITION
- **Non-obsolescence is the feature of data making old formats reusable as if they were new, without transforming them to new formats.**
- **It has to do with representability of the functionality of old data.**

## TEST CONDITIONS
- Suppose you have data like `<hello>world</hello>`. It is non-obsolescent, if there exists a header, that tells, how it can be understood as a functional map, so that it can be translated to other formats, like `{"hello": "world"}`.
- In this case, it could be a header, such as `<?xml version="1.0" encoding="UTF-8"?>` telling the reader how to read it.

**NOTE:** While file extensions were originally used to represent data formats, they proved to be insufficient as generic formats evolved. One of the primary goals for metaformat is to create such a metaheader – a universal generalized header for all I/O needs of objects (old and new) with such header.
