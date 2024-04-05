# `srda`: semantically named RDA elements 

**`srda` provides human readable and meaningful lexical equivalents for all RDA elements, defined using common `owl:sameAs` relations.**

**RDA**, [Resource Description and Access](https://www.rdaregistry.info), is a modern metadata standard designed for use in the bibliographic domain. Unfortunaltely, the commission that designed RDA chose not the use **meaningful names** for the RDA elements but **abstract codes** instead. 

## How do you prefer your RDF?

Do you think the following RDF is easy to understand? :

    @prefix rdaw:        <http://rdaregistry.info/Elements/w/> .

    <id/som/work/5882fb21c4a696cc877f59e910c81fca>
      rdf:type <http://rdaregistry.info/Elements/c/C10001> ;
      rdaw:P10223 "Chamber music" ;
      rdaw:P10004 <id/som/d78168> ;
      rdaw:P10053 <id/som/7160833597948a09eb41d51c99eb8de2> ;
      rdaw:P10061 <id/som/6e6568e39715aad83d5dac96464ec33a> ;
      rdaw:P10069 "Delta Ensemble" ;
      rdaw:P10219 "1983" ;
      rdaw:P10220 <id/som/um2532> , <id/som/um914> ;
      rdaw:P10287 "Amsterdams Fonds voor de Kunst" ;
      rdaw:P10353 <https://iso639-3.sil.org/code/eng> .

Or do you consider this equivalent RDF to be more human readable? :

    @prefix srda:        <https://data.digitopia.nl/srda#> .

    <id/som/work/5882fb21c4a696cc877f59e910c81fca>
      rdf:type                   srda:Work ;
      srda:preferredTitleOfWork  "Chamber music" ;
      srda:authorAgent           <id/som/6e6568e39715aad83d5dac96464ec33a> ;
      srda:categoryOfWork        <http://rdaregistry.info/termList/RDATerms/1118> ;
      srda:commissioningAgent    "Amsterdams Fonds voor de Kunst" ;
      srda:composerAgentOfWork   <id/som/7160833597948a09eb41d51c99eb8de2> ;
      srda:dateOfWork            "1983" ;
      srda:dedicateeAgentOfWork  "Delta Ensemble" ;
      srda:languageOfRepresentativeExpression
                                 <https://iso639-3.sil.org/code/eng> ;
      srda:mediumOfPerformanceOfMusicalContentOfRepresentativeExpression 
                                 <id/som/um914> , <id/som/um2532> .
      

For those who prefer the latter, `srda` has been created.

## What is `srda`

Working with the abstract element names as provided by RDA, is inefficient and error prone.

To overcome this, `srda` provides **human readable and meaningful lexical equivalents** for all RDA elements, defined using `owl:sameAs` relations. 

Additionally, `srda` provides all the `rdf:label` properties. 

The element names of `srda` have been automatically derived from the *lexical aliasses* in RDA (excluding the *language suffix*). `srda` is based on the English language, the *lingua franca* of the world of information systems.

`srda` lives at [https://data.digitopia.nl/srda#](https://data.digitopia.nl/srda#) (which is also the **namespace** for `srda`).

## The `srda` repository

This repository ([https://github.com/renevoorburg/srda](https://github.com/renevoorburg/srda)) provides the scripts that are used to create [https://data.digitopia.nl/srda#](https://data.digitopia.nl/srda#). Actually, only [srda_virtuoso.sparql](./srda_virtuoso.sparql) is used, the script [srda_construct.sparql](./srda_construct.sparql) provides an equivalent using a CONSTRUCT query for reference and conveniance.

These queries expect the named graph `<http://rdaregistry.info/Elements/v5.0.19/>` to be available and loaded with all regular official RDA element definitions. These can be downloaded from [https://github.com/RDARegistry/RDA-Vocabularies/releases](https://github.com/RDARegistry/RDA-Vocabularies/releases). Note that the object, datatype, unconstrained and 'rof' definitions should not be loaded. They are not a part of `srda` (adding them would have resulted in conflicting and duplicate element names).

## What about the RDA lexical aliasses?

Indeed, RDA does provide so called *lexical aliases*. Those lexical aliases are even used to create `srda`, so why not use them in your RDF?

The problem with the lexical aliases as provided by the official RDA definitions is multifold:

* The property used to define lexical aliases, `<http://metadataregistry.org/uri/profile/regap/lexicalAlias>` is **not an internet standard**,
* The property is **not defined properly**, looking it up results in a `http-404` error.
* Its **semantics are unclear**.

Using `owl:sameAs`, as `srda` does, fixes these shortcomings. 
