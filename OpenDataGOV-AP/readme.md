# OpenDataGOV Linked Data Application Profile

## Introduction
This file presents the Linked Data Application Profile [1]

[1] T. Cruz, J. Lourenço, M. Curado-Malta, and J. Bispo, "OpenDataGOV-AP: A Linked Data Application Profile for Parliamentary Activities," in Proc. 24th Int. Conf. on Dublin Core and Metadata Applications (DCMI 2026), Seoul, South Korea, 2026.

## Prefixes
 Name                                             | Prefix | URI                                                              |
|--------------------------------------------------|--------|------------------------------------------------------------------|
| Friend Of A Friend                               | foaf   | http://xmlns.com/foaf/0.1/                                       |
| XML schema                                       | xsd    | http://www.w3.org/2001/XMLSchema#                                |
| Dublin Core Terms                                | dct    | http://purl.org/dc/terms/                                        |
| Schema                                           | schema | https://schema.org/                                              |
| Quantity, Unit, Dimension and Type               | qudt   | http://qudt.org/schema/qudt/                                     |
| dbpedia ontology                                 | dbo    | http://dbpedia.org/ontology/                                     |
| Map for Scrutiny                                 | m4s    | https://purl.org/map4scrutiny-core#                              |
| Ontologia della Camera dei deputati              | ocd    | http://dati.camera.it/ocd/                                       |
| Bibliographic Ontology                           | bibo   | https://www.dublincore.org/specifications/bibo/bibo/bibo.rdf.xml |
| Academic Institution Internal Structure Ontology | aiiso  | https://vocab.org/aiiso/                                         |
| Simple Event Model Ontology                      | sem    | http://semanticweb.cs.vu.nl/2009/11/sem/                         |
| PROV Ontology                                    | prov   | https://www.w3.org/ns/prov-o                                     |
| Open Graph protocol                              | og     | http://ogp.me/ns#                                                |
| Time Ontology                                    | time   | https://www.w3.org/2006/time                                     |
| European Legislation Identifier Ontology         | eli    | http://data.europa.eu/eli/ontology#                              |
| Organization Ontology                            | org    | http://www.w3.org/ns/org#                                        |
| Parliamentary Core                               | core   | http://purl.org/polis/ar/core#                                   |
| Parlimentary Initiatives                         | ini    | http://purl.org/polis/ar/initiatives#                            |
| Biographical data of the Members of Parliament   | bio    | http://purl.org/polis/ar/biographical-profile#                   |
| Activities of the Members of the Parliament      | mpact  | http://purl.org/polis/ar/mp-activities#                          |

## The Terms
| Domain | foaf:Person                 |                               |                 |             |     |     |                            |
|--------|-----------------------------|-------------------------------|-----------------|-------------|-----|-----|----------------------------|
|        | label                       | Term                          | Range           | Cardinanity | VES | SES | Comments                   |
| DP     | name                        | foaf:name                     | xml:string      | 0-1         |     |     |                            |
|        |                             |                               |                 |             |     |     |                            |
| Domain | MP                          | a rdfs:subClassOf foaf:Person |                 |             |     |     |                            |
|        | label                       | Term                          | Range           | Cardinanity | VES | SES | Comments                   |
| DP     | identifier                  |                               | xml:uri         | 1           |     |     |                            |
| OP     | participated in legislature |                               | ini:Legislature | 1-*         |     |     |                            |
| OP     | has mandate                 |                               | ini:Mandate     | 1-*         |     |     |                            |
|        |                             |                               |                 |             |     |     |                            |
|        |                             |                               |                 |             |     |     |                            |
| Domain | MG                          | a rdfs:subClassOf foaf:Person |                 |             |     |     |                            |
|        | label                       | Term                          | Range           | Cardinanity | VES | SES | Comments                   |
| OP     | duty in the government      |                               | ini:Duty        | 1           |     |     |                            |
| OP     | belongs to government       |                               | ini:Government  | 1           |     |     |                            |
|        |                             |                               |                 |             |     |     |                            |
| Domain | Guest                       | a rdfs:subClassOf foaf:Person |                 |             |     |     |                            |
|        | label                       | Term                          | Range           | Cardinanity | VES | SES | Comments                   |
| DP     | honour                      |                               | xml:boolean     | 1           |     |     | A guest of Hounor if true. |
| DP     | country                     |                               | xml:uri         | 1           |     |     |                            |
| OP     | duty                        |                               | ini:Duty        | 0-1         |     |     |                            |

| Domain | ini:Mandate                 |                               |                  |             |     |     |                            |
|--------|-----------------------------|-------------------------------|------------------|-------------|-----|-----|----------------------------|
|        | label                       | Term                          | Range            | Cardinanity | VES | SES | Comments                   |
| DP     | identifier                  |                               | xml:string       | 0-1         |     |     |                            |
| DP     | parliamentary name          |                               | xml:string       | 1           |     |     |                            |
| OP     | is valid during legislature |                               | ini:Legislature  | 1           |     |     |                            |
| OP     | member of PG                |                               | ini:PGMembership | 1-*         |     |     |                            |
| OP     | is in situation             |                               | ini:Situation    | 1-*         |     |     |                            |
| OP     | has duty                    |                               | ini:Duty         | 0-*         |     |     |                            |
| OP     | participated in legislature |                               | ini:Legislature  | 1-*         |     |     |                            |
| OP     | has mandate                 |                               | ini:Mandate      | 1-*         |     |     |                            |
