# MFT-1

MFT-1 relies on the polycontext metasymbol "**any context ->** `*`". That is, we simply take `*` (asterisk) in all cases (as default metasymbol). The choice of asterisk is due to its common use to represent _anything or everything_, which is semantically connected to (**LEE Principle**, **[MFT 0000](../0000-philosophy/0000-philosophy.md#i-lee-principle)**).

```
* : Schema reference specification symbol.
```

Additionally, MFT-1 is extended by 3 additional symbols: `-` to specify ID (instead of `@id` in JSON-LD), `+` to specify author keys and permissions, `^` to specify intentionality.

```
- : Data item origin location symbol.
+ : Author keys and permissions embedding symbol.
^ : Author itention specification symbol.
```

Records **must** have `*` field, that specifies the url of schema, and **may** have `-`, `+`, `^` fields, that specify location, authentication and permissions, and author intent urls.

The `-`, `+`, `*` are specified by providing machine-readable URLs, whereas `^` **must** be of one of the values: `.` ("is-fact"), `?` ("is-possibility"), `!` ("is-desired"). Note, that these closely relate to the protocol specification words `HAS`, `MAY`, `MUST`, and can be thought of as such desires and opinions expressed by the author specified in `+`.

This becomes a metaformat relying of four symbols as keys of records: `(-, +, *, ^)`, usable in specifying authorship, permissions, meaning and intent in arbitrary records.

It makes it possible to express things like:

```
{'ice-cream': 'pleasantly experienced as eaten by me',
 '-': 'specific one on specific market',
 '+': 'Neo',
 '*': 'defined-key: ice-cream; defined-value: pleasantly experienced as eaten by me',
 '^': 'wants'}
```

`Neo` wants experience of `{'ice-cream': 'pleasantly experienced as eaten by me'}`, and the specifics of what it means, is detailed in the definition of the schema of the record `*`.

For example, changing the `^` changes the intentionality. Note that formally, the above would expressed as:

```
{'ice-cream': 'pleasantly experienced as eaten by me',
 '-': 'data-origin-url',
 '+': 'auth-perms-url',
 '*': 'schema-url',
 '^': '!'}
```

Submitting such record to a computer or society, we could be providing clues to reasoning (`?`), asking to satisfy a desire (`!`), or providing our beliefs about world's ground facts to it (`.`). Producing such well-defined records, people and systems could express their wills, exchange facts, and hypotheses, compute distances from state to state, and move along together in the timespace.

The metadata can be nested alongside the nested data, as we see further below. For the convenience, we have `metaform` package (`pip install metaform`, currently non-public), which generates MFT-1 prototype for arbitrarily nested JSON-like data.

# The specification
The metaformat is specified by providing ways (symbols and syntax), in which it satisfies the [requirements](../0001-metaform-philosophy/0001-metaform-philosophy.md)).

## 1. Non-Obsolescence

The default metasymbol `*` of MFT-1 provides format via its value URL, with the format (schema) data in machine-human readable specifications. The asterisk appears to be of not any syntactic significance in any currently known formats among JSON, YAML, XML, RDF.

The record with metaformat specification looks entirely like a standard data, except for presence of `*` key, which satisfies non-obsolescence criterion for any formats that do not use `*` key as part of their syntax.

**Examples**

### In Data Packets
#### In JSON
- As `*` key, with value pointing to URL of specifications.

```json
{"*": "https://github.com/wefindx/ooio/wiki/example#test1",
 "field1": "Haiz",
 "field2": {
  "properties": {
    "field3": 12}}}
```

#### In XML
- As `<?_ *="">` attribute at any level, with value pointing to URL of specification.

```xml
<?xml version = "1.0"?>
<record>
   <?_ *="https://github.com/wefindx/ooio/wiki/example#test1"?>
   <field1>Haiz</field1>
   <field2>
       <properties>
           <field3>12</field3>
       </properties>
   </field2>
</record>
```

### In Filesystems
- As `SCANME.md` file, under the `FORMAT` heading, as so:

```
.
├── docs
│   └── index.md
├── README.md
├── SCANME.md   <--
└── src
    ├── core
    │   └── app.py
    ├── main.js
    └── main.py
```
with the content of metaformat specification (in any format -YAML, JSON, XML, etc.) as first code block, like so:

```yaml
# Some heading
```yaml
- '*': ''
  README.md: {'*': ''}
  src:
    - '*': ''
      main.py: {'*': ''}
      main.js: {'*': ''}
      core:
        - '*': ''
          app.py: {'*': ''}
  docs:
    - '*': ''
      index.md: {'*': ''}
```yaml
```

The values at each level provide ability to specify metaformat for each file and directory in the project by providing URLs to schema specifications. To autogenerate SCANME.md, you can globally `pip install metadir`, and type `metadir .` to generate such file.

## 2. Context-free Callability

The callability is implemented by providing `_:actions` key to data, which are bind to methods available in APIs (like [here](https://github.com/mindey/-/wiki/topic#halfbakery)).

For example, if source that contains data, provides some functions to the data, such as API, they can be automatically mapped to properties of the data objects through specifying `_:actions`.

The data lookups are provided by `_:generator` key. Doing requests to data, items generator, that can be specified by `_:emitter` key in the specifications, mapping the `search` function, that allows to generate items from arbitrary query, in such a way that items conform with specification of MFT-1 (i.e., has `-`, `+`, `*`, `^` keys).

## 3. Mergeability

The mergeability is realized by providing the data key-value concepts that represents keys, data value types, and value mesures along with the keys that reference the values, and a specific algorithm for merging them.

The algorithm is currently still under development, but fundamentally, it extracts shared keys from records, normalizes the values based on data type and measure types.

The general consensus type, is to use `#` hash symbol to specify the specific types for concepts. For example, if we have concept of [age](https://github.com/infamily/indb/wiki/age), we have [#float-years](https://github.com/infamily/indb/wiki/age#float-years) as format. Similarly, at another level of abstraction, we may have 'sugar#float-kg' to represent sugar in float-kilograms, or even other level of abstraction, [topic](https://github.com/infamily/indb/wiki/topic) and [#google-plus](https://github.com/infamily/indb/wiki/topic#google-plus) as format.

The formats can be inherited across different wikis, so, for example, if I'm crawling Halfbakery, and someone (e.g., [wefindx/topic#halfbakery](https://github.com/wefindx/ooio/wiki/topic#halfbakery)) already defined related topic type, I can inherit and override it on my [mindey/topic#halfbakery](https://github.com/mindey/-/wiki/topic#halfbakery).

## 4. Structure-Retention

The structure retention is achieved by doing minimal changes to data imported, namely, by just providing `-`, `+`, `*`, `^` keys (minimally, just `*` key to specify the shape, as `*` is enough to define what the other things, e.g., `-`, `+`, `^` has to mean). Most formats, including JSON, XML, YAML, RDF, CSV, etc., allow adding these symbols the specification of data in them.

## 5. Linguistic Renderability

In MFT-1, in conformation with WikiData approach, we use thek keys `aliases` and `descriptions`, to specify the aliases to concepts in their specification documents (wikis). For example:

- [https://github.com/infamily/indb/wiki/body-text](https://github.com/infamily/indb/wiki/body-text)

When using these concepts as the keys in data stored as key-value form, then the data keys become renderable to concept aliases in arbitrary langues.

We also provide a namespace pattern for the dictionaries, specifics for MFT-1 are at [metawiki](https://github.com/mindey/metawiki#metawiki). It allows to create arbitrary concepts on personal wikis, and refer them to `::github-username/term-name`. For example, suppose I want to define my term on my github wiki. I have to create a wiki on the repository named `-` (e.g. [mindey/-](https://github.com/mindey/-)) on my GitHub, then, install  `pip install metawiki`, and then:

```python
>>> import metawiki
>>> metawiki.name_to_url('::mindey/atom')
'https://github.com/mindey/-/wiki/atom'
>>> metawiki.url_to_name('https://github.com/mindey/-/wiki/atom')
'::mindey/atom'
```

However, the namespace doesn't need to be used. All what's needed, is providing the keys (of the key-value pairs), that are somehow referencing URLs containing the term specifications, like this: [https://raw.githubusercontent.com/wiki/mindey/-/atom.md](https://raw.githubusercontent.com/wiki/mindey/-/atom.md). The need for a namespace manager, is due to impossibility to use urls as keys in most databases.

## 6. Algebraic Tractability

This is realized by implementing addition/subtraction, and. The specific definition is still under development, however, the basic rationale, is to do one of the two:

1. **Property-based.** Make the difference function compare comparable types of hierarchical structures. For example, in the case of `{'fruits': {'oranges': 1}} - {'apples': 1, 'oranges': 2}`, compare the comparable types, and ignore the rest, e.g., resulting in `{'fruits': {'oranges': 0}, 'apples': -1}`.
2. **Structure-based.** Make the difference function calculate transformations needed to transform one structure to another. For example, in case of `{'fruits': {'oranges': 1}} - {'apples': 1, 'oranges': 2}`, produce the sequence of actions to transform `{'apples': 1, 'oranges': 2}` into `{'fruits': {'oranges': 1}}`. For example, [move_and_align({'oranges': 2}, to={'fruits'}), align({'apples': 1})].

The specific implementation for MFT-1, is currently under development.

## 7. Purposefulness

This metaformat introduces the fourth symbol (`^`) to designate the purpose of the author, which can be valued in one of three symbols: `.`, `?`, `!`, meaning `fact`, `potentiality`, `desire` by the information source.

For example:

```{'^': '.', 'gravity_constant': 9.81}```

"a <u>fact</u>, that **gravity_constant** is equal to `9.81`"

```{'^': '?', 'gravity_constant': 10.82, 'earth_size': 1.2}```

"a <u>potentiality</u>, that **gravity_constant** be equal to `10.82`, and earth_size is `1.2`"

```{'^': '!', 'gravity_constant': 7.21}```

"a <u>desire</u>, that **gravity_constant** be equal to `7.21`"

The `.` means "fact", by representing ground truth (dot as something that lays on the ground).


## 8. Permissionedness and authenticity

This metaformat introduces the `+` symbol to include the link or content representing permissions, and the authorship information (such as cryptographic signatures).

For example:

```{'^': '!', 'earth_gravity_constant': 7.21, '+': 'SOMEONEs-auth-and-permissions-information'}```

The `SOMEONE` desires the `gravity_constant` be equal to `7.21`, and propose that as a goal to the world's computer to pursue / execute.


## The Merit

Because of the extra information contained in the [example](https://github.com/wefindx/ooio/wiki/example#test1), the data record

```json
{"*": "https://github.com/wefindx/ooio/wiki/example#test1",
 "field1": "Haiz",
 "field2": {
  "properties": {
    "field3": 12}}}
```

becomes understandable, and simplifiable something like:

```json
{CONCEPT("_:username"): FORMAT('_:username#utf8-string') VALUE("Haiz"),
 CONCEPT("_:age"): FORMAT('_:age#float32-years') VALUE("12")}
```

Concepts like [username](https://www.wikidata.org/wiki/Q26403005), and [age](https://www.wikidata.org/wiki/Q185836), are well-defined interlingually translatable concepts. Their formats, such as [utf8-string]() and [float32-years](https://github.com/infamily/indb/wiki/age#float-years) are also well-defined entities with respect to lower level concepts, like `string`, and `years`.

For examples of current working specifications, check out [topics](https://github.com/wefindx/ooio/wiki/topic), [organizations](https://github.com/wefindx/ooio/wiki/organization), [products](https://github.com/wefindx/ooio/wiki/product), [ideas](https://github.com/wefindx/ooio/wiki/idea), [users](https://github.com/wefindx/ooio/wiki/user), etc. The ability for organizations to define concepts and their specifications of schemas, creates the freedom of not having to learn or rely on any specific ontology or vocabulary of [hundreds](https://lov.linkeddata.es/dataset/lov/) of domain-specific vocabularie, and yet be able to formally exchange information!

## Namespaces for Concepts

The words `CONCEPT`, `FORMAT` and `VALUE` in the section above are illustrative purposes, meaning, that the there exists namespace for concepts and formats, which is true in current implementation of MFT-1, because there exists namespace `_` and syntactic element `:` to define them, which are defined as a bidirectional map in package [metawiki](https://github.com/mindey/metawiki#metawiki) (`pip install metawiki`). The `VALUE` may be simply a bitstring (or symbolstring, in case of other than binary alphabets like in case of DNA).

```python
>>> import metawiki
>>> metawiki.name_to_url('_:username#utf8-string')
"https://github.com/infamily/indb/wiki/username#utf8-string"
>>> metawiki.url_to_name('https://www.wikidata.org/wiki/Q26403005')
"WD:Q/26403005"
```

It currently specifies major three namespaces: `_` (GitHub [infamily/indb](https://github.com/infamily/indb/wiki) repository), `IN` (GitHub organization wikis under `ooio` repository, such as [wefindx/ooio](https://github.com/wefindx/ooio/wiki))), and `WD` ([Wikidata](https://www.wikidata.org)). The idea is to create community-based extensible namespace registry addressing concepts and formats online.

The specification of such global namespaces for shortening URLs to the concept definitions and formats is important, if we want to keep metaformat defintions more compact, and use existing formats like YAML, JSON, etc. to define them, because many systems forbid the use of URLs as keys of dictionaries. Simplifying them with such shortcuts allows to use them as keys.

The choice of using wikis and html pages is due to the de-facto way in which people specify concepts on-line (they use wikis), and concepts are a natural place to specify formats, that these concepts appear in different systems, MFT-1 assumes that formats are reachable in machine-readable form on the pages defining concepts via anchors specified after the last `#` (hash) symbol in urls.

For example, [topics](https://github.com/wefindx/ooio/wiki/topic#halfbakery), where the formats of topics can be found, on the same page, that specifies the concept ("topic"), and where other schemas in other systems specifying the same concept can be found. You can read it by installing `pip install metaform`, and then:

```python
import metaform
metaform.get_schema('https://github.com/wefindx/ooio/wiki/topic#halfbakery')
```

Since there are many [vocabularies](https://lov.linkeddata.es/dataset/lov/) and ontologies ([1](http://aber-owl.net/ontology)), the above implies that we will work towards creating the namespaces for each of them, to be able to use simultaneously the terms from multiple ontologies to create new data type specifications.

### A note on Linked Data
The LinkedData format, such as `JSON-LD`, rely on specifying one vocabulary, however, metaformat introduces namespaces for concepts, so, instead of something like:

```json
{
  "@context": "https://json-ld.org/contexts/person.jsonld",
  "@id": "http://dbpedia.org/resource/John_Lennon",
  "name": "John Lennon",
  "born": "1940-10-09",
  "spouse": "http://dbpedia.org/resource/Cynthia_Lennon"
}
```

We can have something like:

```json
{
  "*": "IN:json-ld/person",
  "url": "http://dbpedia.org/resource/John_Lennon",
  "name": "John Lennon",
  "born": "1940-10-09",
  "spouse": "http://dbpedia.org/resource/Cynthia_Lennon"
}
```

The MFT-1 is more "meta" than JSON-LD. For example, you can specify JSON-LD in it (`pip install metaform`):
```python
data = {
  "@context": "https://www.w3.org/ns/activitystreams",
  "@type": "Create",
  "actor": {
    "@type": "Person",
    "@id": "acct:sally@example.org",
    "name": "Sally"
  },
  "object": {
    "@type": "Note",
    "content": "This is a simple note"
  },
  "published": "2015-01-25T12:34:56Z"
}

import metaform
metaform.template(data)

{'@context': {'*': ''},
 '@type': {'*': ''},
 'actor': {'@type': {'*': ''}, '@id': {'*': ''}, 'name': {'*': ''}},
 'object': {'@type': {'*': ''}, 'content': {'*': ''}},
 'published': {'*': ''},
 '*': ''}
```

This decorates the expression with the `{'*': ''}`, allowing to specify every part of it.

Another difference is that while `@context` of JSON-LD is also pointing to a vocabulary that specifies terms from arbitrary ontologies, the `*` of MFT-1 is minimal (uses only one symbol: `*`, rather than `@context`, `@id`, `@type`, and other symbols), making it more readable in deeply nested structures than JSON-LD. MFT-1 does not require full vocabulary - only the terms used in data, supports inclusion within multiple formats (including XML, XLS, and other old formats). In addition, it has extra [features](../0001-metaform-philosophy/0001-metaform-philosophy.md). JSON-LD purports adherence to existing vocabularies, whereas MFT-1 supports free thinking by being simple and allowing to create own vocabularies easier.

### Use case for data normalization

Let's say you have some data. `pip install metaform`.
```
data = {"*": "https://github.com/wefindx/ooio/wiki/example#test2",
 "field1#string": "Haiz",
 "field2": {
  "properties": {
    "field3#float": 12}}}

import metaform

>>> metaform.load(data)
{'*': 'https://github.com/wefindx/ooio/wiki/example#test2',
 'field1': 'Haiz',
 'field2': {'properties': {'field3': 12}}}

>>> _.format('cn')
{'用户名': 'Haiz',
 '负载': {
 '属性': {'年龄': 12}}}
```

### Toy examples of merging datasets.

## 1. Case: 2 sources, one concept.
Let's say our concept is [message](https://github.com/mindey/-/wiki/message), with `source1` and `source2`, where from each of them there is a different schema of the message. Let's say that we have some data sample from source1 ([sample1](https://gist.github.com/mindey/39b83f3fe79e52d1a78b79f147c34205)) and source2 ([sample2](https://gist.github.com/mindey/71709e2192ab13a8f612066d8d4b3ef7)).

So, regardless of what is within these datasets, we use `metaform` to generate metaformats:
```python
import metaform
import requests
template1 = metaform.template(requests.get('https://gist.githubusercontent.com/mindey/39b83f3fe79e52d1a78b79f147c34205/raw/6e61c39b604b3776b8244cedc104761b1105a19f/message-source1-data.json').json())
template1

[{'date': {'*': ''},
  'sender': {'*': ''},
  'recipient': {'*': ''},
  'text': {'*': ''},
  '*': ''}]

template2 = metaform.template(requests.get('https://gist.githubusercontent.com/mindey/71709e2192ab13a8f612066d8d4b3ef7/raw/23e6262c96457e81c58aae32698d074cc2662c5a/message-source2-data.json').json())
template2

[{'time': {'*': ''},
  'results': [{'from': {'*': ''},
    'to': {'*': ''},
    'message': {'*': ''},
    '*': ''}],
  '*': ''}]
```

Next, we use some dictionary to define the meanings for the terms, or use our own. In this case, I'll use multiple terminologies -- Infinity terminology accessible at [indb/wiki](https://github.com/infamily/indb/wiki), namely [_:creation date](https://github.com/infamily/indb/wiki/creation-date), [_:body-text](https://github.com/infamily/indb/wiki/body-text) and [_:message](https://github.com/infamily/indb/wiki/message), Wikidata's terminology for [WD:sender](https://www.wikidata.org/wiki/Q974688), and [WD:receiver](https://www.wikidata.org/wiki/Q1339255), to fill out templates. Additionally, we'll include the formats, to which I want to normalize the values after the anchor sign, as so: `_:creation-date#isodate`, based on what format does the data in the original source occur in, and save them on our personal `github.com/user/-/wiki`, like so: [message#source1](https://github.com/mindey/-/wiki/message#source1) and [message#source2](https://github.com/mindey/-/wiki/message#source2), quoted under ``````yaml ...`````` as quotes immediately after each of the headers (source1, source2).

MFT-1 supports the inheritance of formats, so, if you find that some format in existence, is already satisfying your needs, you can define by inheritance, like so - since the [_:message#version-1](https://github.com/infamily/indb/wiki/message#version-1) of `_:` namespace already has fields `text` and `sender`, we can inherit from it by `_:extends` keyword. In that way, [::mindey/message#source1b](https://github.com/mindey/-/wiki/message#source1b) is equivalent to [::mindey/message#source1](https://github.com/mindey/-/wiki/message#source1).

Then, we have to update the original data records to include references to the schema of source by adding asterisk field, like so:

```yaml
# source 1 data
[
  {"date": "2018-12-18",
   "sender": "Alice",
   "text": "Hello, world.",
   "*": "https://github.com/mindey/-/wiki/message#source1"},
  {"date": "2018-12-19",
   "sender": "Bob",
   "text": "Hi Alice!",
   "*": "https://github.com/mindey/-/wiki/message#source1"}
]

# source 2 data
[
  {"time": 1541637311,
   "results": [{"from": "Max", "message": "Hi Bob!"}],
   "*": "https://github.com/mindey/-/wiki/message#source2"},
  {"time": 1541337311,
   "results": [{"from": "Anna", "message": "Where are you, Bob?"}],
   "*": "https://github.com/mindey/-/wiki/message#source2"}
]
```

Each record now carries an asterisk key, which points to its schema definition, and that is the key. Such data can be sotred in database, for example, [messages-source1](https://gist.github.com/mindey/2cdeecddab20d036b957cd0d306b7153), [messages-source2](https://gist.github.com/mindey/93b4a98b0b4a06cbca475582b44ced53). Such data is said to have metaformat included.

I then can be read and automatically processed (aligned, translated, formatted). For example:

```python
import metaform
data1 = metaform.load('https://gist.githubusercontent.com/mindey/2cdeecddab20d036b957cd0d306b7153/raw/f49fd75eca4124e89e176fc29488e296b7154b8b/message-source1-ndata.json')
data2 = metaform.load('https://gist.githubusercontent.com/mindey/93b4a98b0b4a06cbca475582b44ced53/raw/3515e2f9b9ff4f86525ae17f37c46533bf3b7daf/message-source2-ndata.json')
```

**Formatting**
```python
>>> data1.format()
[{'_:creation-date': datetime.datetime(2018, 12, 18, 0, 0),
  'WD:Q974688': 'Alice',
  'recipient': 'Bob',
  '_:body-text': 'Hello, world.'},
 {'_:creation-date': datetime.datetime(2018, 12, 19, 0, 0),
  'WD:Q974688': 'Bob',
  'recipient': 'Alice',
  '_:body-text': 'Hi Alice!'}]
```

**Translating**
```python
>>> data1.format('cn')
[{'创作日期': datetime.datetime(2018, 12, 18, 0, 0),,
  '通信源': 'Alice',
  '通信端': 'Bob',
  '正文': 'Hello, world.'},
 {'创作日期': datetime.datetime(2018, 12, 19, 0, 0),
  '通信源': 'Bob',
  '通信端': 'Alice',
  '正文': 'Hi Alice!'}]
```

**Aligmentment**

Suppose what you care about, is all objects that are messages (`_:message`). All we have to do is just go over all records, and look for those that are asterisked by concept of message, regardless of format.

```python
# define equivalence class
concept_set = ['::mindey/message#source1', '::mindey/message#source2']
#
sources_set = ['::mindey/message#source1~https://plus.google.com']
```




### Use case for interaction with sources.
# Example with HalfBakery.

### TMP Self-Note
Note: It is not clear if the JSON-LD supports defining the data types on bit strings.

But this is just the tip of the iceberg. Additional [features](../0001-metaform-philosophy/0001-metaform-philosophy.md#metaformat-requirements) provide the ability to make data be part of languages, call methods, and interface with data sources without having to write their specific clients. (Instead, having declarative specifications solve the problem auto-generating clients behind the scenes for variety of formats, not just OpenAPI.)

It blurs the lines between concept, format and schema -- all of them are one, just a hierarchy of concepts with grouped schemas, defined in terms of concepts themselves.


## Application Examples

For example, take this data object as example:

# Source 1
```
{
    "Name": {
        "First": "Neo",
        "Last": "X"
    }
    "*": "schema-location-url",
}
```

# Source 2
```
<root>
  <persons type="list">
    <item type="dict">
      <first_name type="str">Xin</first_name>
      <last_name type="str">N</last_name>
    </item>
  </persons>
  <key name="*" type="str">schema-location-url</key>
</root>
```

## Conjuctures
- Trees imply triplets [just like graph can be decomposed into edges, a key-value tree can be decomposed into triplets: (*object, property, value)]
-


## Full example

```json
{
	"_id" : ObjectId("9b99999667bdbc62e0d8211f"),
	"*" : "https://github.com/wefindx/ooio/wiki/idea#halfbakery",
	"-" : "http://www.halfbakery.com/idea/Blog_202.0",
	"title" : "Blog 2.0",
	"votes" : {
		"negative" : null,
		"positive" : 5
	},
	"body" : "Social media is increasingly evolving, and it provides a variety of advanced viewing rights for content (both the posts and each comment).\r\nUnfortunately, there is no single platform, except potentially -- a personal\nblog -- where where you could write and expect that everyone won't have a problem to see it.\r\nHence, an idea of Blog 2.0.\r\nIn Blog 2.0 you would define your friends even before their registration on your blog, by providing their identities in different social platforms.\r\nThen, no matter which social-login the friend uses to register or log-on to your blog, he or she would immediately be recognized as a particular friend, and only the posts that were supposed to be visible to the user would actually be visible to the user. Moreover, comments would have many visibility options, such as \"only chosen people can see the comment\", or \"only mutual friends on a chosen set of social networks can see the each other's comment\" would also be options available.",
	"author" : {
		"username" : "Inyuki",
		"userlink" : "http://www.halfbakery.com/user/Inyuki",
		"date" : "2015-01-05T00:00:00"
	},
	"category" : "computer",
	"subcategory" : "blog",
	"links" : [ ],
	"annotations" : [
		{
			"text" : "Comment 1.",
			"username" : "user1",
			"date" : "2015-01-05T00:00:00",
			"last_modified" : null,
			"userlink" : "http://www.halfbakery.com/user/user1"
		},
		{
			"text" : "Comment 2.",
			"username" : "Inyuki",
			"date" : "2015-01-05T00:00:00",
			"last_modified" : null,
			"userlink" : "http://www.halfbakery.com/user/Inyuki"
		}
	]
}
```

