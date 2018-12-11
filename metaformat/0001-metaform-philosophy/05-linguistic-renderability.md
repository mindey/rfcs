# 5. Linguistic Renderability

## CONTEXT
- We may have records with unrecognizable fields in abbreviations or foreign languages.

## DEFINITION
- **Data is linguistically renderable, if all of its fields are mapped to concept IDs, that have aliases in human languages, such as English, Chinese, etc.**

## TEST CONDITIONS
- Given a record, like , like `{"Q141": 1, "L112" 2}`, does the metaheader provide enough information to automatically render it to a target language, such as , like `{"Dog": 1, "Puppies":  2}`.
