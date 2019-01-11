# Metaformat Philosophy

Metaformat Philosphy introduces [properties](#metaformat-requirements) that we would like data to have when supplemented with it.


## Purpose

The data we create continues the information evolution, which started with the emergence of structures capable of extensive search for stability in the presence of entropy. Metaformat is the data format to create a metastructure that maximizes reusability of data and systems, in order to make them relevant in the future of the evolution (**LEE Principle**, **[MFT 0000](../0000-philosophy/0000-philosophy.md#i-lee-principle)**).

## Formats

Ever since the creation of first software systems, such as life itself, something akin to evolving file formats has emerged, and they had taken very specific shapes, for example, the fact that we are using very specific sequences of symbols like curly braces `{`, `}` (`01111011` and `01111101`) to group larger chunks of code in most programming languages, is quite arbitrary. The fact that life in DNA often uses very specific sequences (such as `AUG` .. `TAG`) as `start` and `stop` codons to group a protein may also be quite arbitrary. However, shapes do change. For example, over the recent years, the use of curly braces to represent data records, such as:

```
{"hello": "world"}
```

had become more popular than angle brackets (`00111100` and `00111110`) with a forward slash (`00101111`):

```
<hello>world</hello>
```

On a higher level, structures had also evolved. Every version of software usually defines its own new format version. For example, every new version of Microsoft Excel may define slightly different file format, that supports more features. Today, when the world moved towards API-driven data exchange, we see this evolution in terms of the changes of API schemas. While each application has its unique functions, at the time of writing, most APIs use the curly braces to represent records within them, and a utilize a higher level standards of organization, such as REST (Representational State Transfer), and OpenAPI (aka Swagger) specifically, enabling to create generic clients.

For the sake of interoperability, people tend to choose to comply with the standards, and the data written in the previous standards becomes obsolete. However, from the scientific (archeological) perspective, much like the text written in languages of other cultures, the format and the very specific shape that the data comes in, carries the information about the circumstances and the nature (the way of thinking) of the information sources that created them. They are the cultural and technological legacy, which, ideally, is left functional, accessible and usable, rather than unusable. Much like most of you would like our biological brain be preserved in functional (even if cryopreserved), accessible form with a non-destructive mind upload process, so as to minimize the risk of information loss.

## Principle

The basic idea is that a metaformat is used to create a header ("metaheader") to bind format and schema specifications to data, and a single **polycontext metasymbol** (a map that specifies in which context what metasymbol is to be used) to bind it to data, and link them with global namespaces of ontologies, schemas, and user identities. For example, the polycontext metasymbol can be defined by providing a map:

<center>
$$
\mathrm{S} (context) \rightarrow

\begin{cases}
    S_1, & context=C_1 \\
    S_2, & context=C_2 \\
    \cdots \\
    S_N, & context=C_N
\end{cases}
$$
</center>

Where, $$C_1 \cdots C_N$$ are format or language contexts, and $$S_1 \cdots S_N$$ are [metasymbols](https://proofwiki.org/wiki/Definition:Metalanguage/Metasymbol), and $$N \in \mathbb{N}$$.

For example if we want to introduce a metasymbol in multiple languages and formats, which may be in conflict with the already-defined symbols and reserved words within the languages and formats, we can introduce a polycontext metasymbol with domain in those languages and formats, for example, $$C = ($$ `XML`, `RDF`, `JSON`, `YAML`, `Python`, `JavaScript`, `Scheme` $$)$$, and codomain with our chosen values for $$S$$, for example $$S = ($$ `__`, `_`, `*`, `*`, `#*`, `{/*S*/}`, `#|*|#` $$)$$, and then use it for arbitrary semantic or syntactic purposes.

## Metaformat Requirements

What follows, is a set of requirements for properties of data with metaheader specification through a polycontext metasymbol. The goal of introducing these properties (or requirements) is to make data understandable and automatically reusable for intended purposes regardless of the original formats that it is in.

## 1. Non-obsolescence
[DETAILED SPECIFICATION](01-non-obsolescence.md)

Ideally, we would have a metaformat, which can define formats, and allow for easy parsing and understanding of any format, no matter how old, and help retain the value of all data, written in any format. <!--See **[NOTE 1]** for some work on that.-->

A universal header for all data records within data sources would be sufficient for describing arbitrarily complex schemas. So, a major purpose of Metaformat is to provide such a general purpose header for information sources (which can be the data records themselves, so the header can be part of the data records (the specifics of including them within each different data type is outside the scope of this document, and is to be specified in specific metaformat specifications)).

## 2. Context-free Callability
[DETAILED SPECIFICATION](02-context-free-callability.)

The data in our world's data sources had not ceased to evolve. The data records within APIs, for example, come with a set of functions that can be called by making a request against the API as data source. People had developed APIs not just for classes, but for material objects like machines, which they tied the data records to representing their state and the control structures listening to those states, enabling the users to treat the machine as mutable record with functions. In object-oriented programming paradigm, there is a specific word for that data type -- an object, as class instance and a control interface (functions that can be called to update the object). While objects are just records with functions, every programming language has its own way of representing them, its own symbol patterns to define them, and these days, one object written in one programming language, is not straightforward to directly use in another language or another context.

We wish to have a format that allows easy embedding of the control interface together with the data object, so that the data object can have and perform functions without the programmer having to explicitly instantiate API clients. (While it is already realized in paradigms like OpenAPI and Graphene, the interfaces remain tied to data source, the idea is the data objects that carry their address in the internet space, should behave like variables in computer memory, always carrying their addresses (pointers) along, so that data programmer does not have to explicitly work with pointers (such as urls) and explicitly instantiate API clients.)

## 3. Mergeability
[DETAILED SPECIFICATION](03-mergeability.md)

Data from variety of data sources comes in all forms and flavors, requiring analysts and app developers to prepare it for analytics or efficient queries by moving it to special databases. There is no reason why the data should not be able to automate that process. In fact, it is quite easy to implement this merging with an upgrade to linked data formats, and that's one of the things that Metaformat is for.

## 4. Structure-retention
[DETAILED SPECIFICATION](04-structure-retention.md)

For the sake of science, data created should stay relevant and accessible in the original form it was created, because the form of the data as it was created, carries scientific value about the moment it was created and the source that had created it.

## 5. Linguistic Renderability
[DETAILED SPECIFICATION](05-linguistic-renderability.md)

Data should be able to present itself in the user's language automatically. For example, data records come from a variety of sources, that had fields in different languages and different conventions, would have to be able to automatically present themselves in desired user's language. <!--See **[NOTE 2]** for some work on that.-->

## 6. Algebraic Tractability
[DETAILED SPECIFICATION](06-algebraic-tractability.md)

The data objects must form an algebra, where objects can be combined in arbitrary ways to form new objects, the sum and difference operations has to be defiend between arbitrary objects of arbitrary internal hierarchy, so that we could define distance between objects, enabling us to solve for transitions (or transformations) required to take a set of objects and turn them into another (desired) set of objects, and perform goal alignments like [process additions](https://www.lesswrong.com/posts/yBGcu4kFzvLHRjZnk/cognitive-bias-of-ai-researchers) (_"Bob is a process, and Alice is processes,... and they collectively are progressing towards some desired convergent state, defined by process addition."_), and encapsulating the wills of the object authors within the objects themselves to auto-resolve the alignments by evolving on the Internet as a shared computer.

## 7. Purposefulness
[DETAILED SPECIFICATION](07-purposefulness.md)

We want to enable intelligence to collectively define and pursue goals. Since goals are just imaginary objects with desired properties, the data objects must make an explicit distinction betwee those that represent reality, and those that are imaginary. This will enable formal definitions of goals through designing imaginary objects, and then minimizing the distance between existing real objects and the imaginary ones. The distinction can work as a tool to define arbitrary objective functions. <!--See **[NOTE 3]** for some work on that.-->

This property enables parties to issue orders, requests, and queries to the world as computer, by allowing to distinguish what's desired from what's thought of, from what's considered to be fact.

## 8. Permissionedness
[DETAILED SPECIFICATION](08-permissionedness.md)

Want to enable the creators of information to give permissions for others to modify it. The inclusion of public keys as properties, and cryptographic signing of changes may allow for having database management systems to grant the rights included within data itself.

---
<!--

### NOTE 1: Subfiles - a work on that.
[.subfiles](https://github.com/mindey/subfiles#readme) -- an experimental work on that. Main idea, was that we can include a dot-file (e.g., `.formats`) within the data source, to map instances, e.g., files in a directory, with their format versions -- a simplified example:

**.formats**

```
[./*.products.csv]
__: https://www.wikidata.org/wiki/Q278425
url: https://www.wikidata.org/wiki/Q42253
currency: https://www.wikidata.org/wiki/Q8142
price: https://www.wikidata.org/wiki/Q160151
name: https://www.wikidata.org/wiki/Q1786779
```

### NOTE 2: OOIO - a work on that.
[ooio](https://github.com/wefindx/ooio) -- an experimental work on that. Main idea, is that the meta-description of object interface can be included in the schema, which is binded to data object. Additionally, the meta-language for desciption of schemas with use of arbitrary set of ontologies is introduced, allowing for automatic merging data records from arbitrary schemas found at arbitrary hierarchical depth (like in GraphQL), as well as rendering in desired languages (like concepts in WikiData), resulting in a convenient format for data analytics (removing the need for ETL), and application building (removing the need for API integrations and object field name translations in the user interfaces).

### NOTE 3:
[asterisk](https://github.com/mindey/asterisk) -- an experimental work on that. Main idea, is that we make a distnction between the imaginary and real objects, and define difference between them.

```
*object - object, that's desired
.object - object, that exists.
```

So, we can say:

```python
>>> reality = Universe({'gravitational constant': 6.67408e-11}, fact=True)
>>> reality
.The Universe ({'gravitational constant': 6.67408e-11})
>>> desirity = Universe({'gravitational constant': 6.69408e-11}, fact=False)
*The Universe ({'gravitational constant': 6.69408e-11})
```

And data itself can be used to easily share and combine intents.
[1](https://github.com/mindey/asterisk/blob/master/docs/2016-09-28_Goals_are_Just_Assets.md)

### A note on notes:

Further, I'll detail these notes, but the hope is to create something, that removes the bottlenecks for solving our greatest challenges from doing science and creating general artificial intelligence, because with the amounts of data we have, there is a huge potential to automate life-saving operations, such as cancer drug and lifestyle change discovery to happen completely automatically, without having to create a specialized startup for each case.


-->

[See MFT-1 specification under development.](../0002-data-object-format/0002-data-object-format.md)
