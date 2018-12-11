# 8. Permissionedness
(and authenticity)

## CONTEXT
- We generally want proof of authorship that created the object.
- Sometimes we receive data, and want to update it in the source.
- The source may have policies. It is great if these policies can be defined in a standard way by authors, for example, with respect to SSH keys on the user’s machine.

## DEFINITION
- **Data has authenticity and permissiodness, if it includes cryptographic signatures of its authors, and supports a standard way of inclusion of management permissions (read/update/delete) for other authors to modify it from other systems in the source; and the DBMS that supports metaformat, obeys the specifications with respect to records (e.g., enforces the permissions and requirements for signing transactions).**

##TEST CONDITIONS
- Does the author of the data object, have a standard way to include the identities (e.g., ssh public keys) of the machines, and the standard is followed by major DBMS, so that data records imported or created in the DMBS that follow metaformat, automatically grant access and management permissions on individual objects to the machines with corresponding private keys.
- (Note: This can be readily implemented by a daemon process on PostgreSQL database, because it supports SSH-key-based authentication, permissions to the granularity of a single row/record, so, for example, if the record inserted has a set of public keys with permissions defined, these permissions and access roles can be updated in the DBMS.)
