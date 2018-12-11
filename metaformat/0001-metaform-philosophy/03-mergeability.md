# 3. Mergeability

## CONTEXT
- Data defined in different formats, in different languages, different field names, field value types and measures at hierarchically different levels, is hard to merge and align.

## DEFINITION
- **Two or more of data records are fully or partially mergeable if their metaheaders define schemas with fully or partially overlapping concepts and their value types (e.g., distance#float64-meters) mapped to their field names.**

## TEST CONDITIONS
- Suppose you have a data record like this:
```
<person><first_name>Neil</first_name><last_name>Armstrong</last_name><properties><age>15</age></properties></person>
```
and want to merge it with a data record like this:
```
{"name": "Hello", "surname": "Kitty", "age_in_days": 12.5}
```

If each data piece has a metaheader, they can be automatically aligned to produce a list of records (or a table) of desired properties (or fields), regardless of different nesting in each source.
