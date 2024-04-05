# srda: Semantically named RDA elements 

**Srda provides human readable and meaningful lexical equivalents for all RDA elements, defined using owl:sameAs relations.**

RDA, Resource Description and Access, is a modern metadata standard for use in the bibliographic domain. Unfortunaltely, the commission that designed RDA decided not the use meaningful names for the RDA elements but abstract codes. Politically, that is very correct since it doesn't favor any national language. 

An argument was that applications using RDA would display the local `rdfs:label`s in stead of the actual element names. That is true, but this argument might have also been used in favor of human readable element names.

Reality is that working with the current abstract names is very inefficient and error prone. Frustrating.

Probably to overcome this, RDA also provides so called **lexical aliasses**. However the approach applied by the RDA commission there doesn't follow internet practices and standards and uses a non standard and badly defined property. This is where srda comes to help.

## What is srda

Srda provides human readable and meaningful lexical equivalents for all RDA elements, defined using owl:sameAs relations. These element names in srda are derived from the lexical aliasses in RDA, excluding the language suffix. Srda is based on the English language, the lingua franca of the world of information systems.

srda lives at [https://data.digitopia.nl/srda#](https://data.digitopia.nl/srda#).

## The srda repository

This repository provides the scripts that are used to create [https://data.digitopia.nl/srda#](https://data.digitopia.nl/srda#). Actually only [srda_virtuoso.sparql](./srda_virtuoso.sparql) is used, the script [srda_virtuoso.sparql](./srda_virtuoso.sparql) in an equivalent using a CONSTRUCT query.







