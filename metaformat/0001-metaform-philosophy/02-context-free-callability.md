# 2. Context-Free Callability

## CONTEXT
- APIs have callable methods.
- Objects defined in OOP languages have callable interfaces (from methods).

## DEFINITION
- **Data is callable context-free, if it carries the web location of the origin of its instances, definition of schema (metaheader) to manage them, and optionally authorization data with permissions bound to machine’s identity (ssh public key).**

## TEST CONDITIONS
- Given a data record, can we call update operations or some method call without manually instantiating a client, or manually connecting with API.
- Does reading the data record within REPL of a language instantiate a fully-featured object, with address pointing to the data source, and methods allowing to interact with the source?

