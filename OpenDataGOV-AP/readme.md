# OpenDataGOV -AP a Linked Data Application Profile

## Introduction
This file presents the OpenDataGOV -AP, a Linked Data Application Profile [1] - submitted to DCMI 2026 - in review.

[1] T. Cruz, J. Lourenço, M. Curado-Malta, and J. Bispo, "OpenDataGOV-AP: A Linked Data Application Profile for Parliamentary Activities," in Proc. 24th Int. Conf. on Dublin Core and Metadata Applications (DCMI 2026), Seoul, South Korea, 2026.

## Prefixes
| Name                                           | Prefix | URI                                            |
|------------------------------------------------|--------|------------------------------------------------|
| Friend Of A Friend                             | foaf   | http://xmlns.com/foaf/0.1/                     |
| XML schema                                     | xsd    | http://www.w3.org/2001/XMLSchema#              |
| Dublin Core Terms                              | dct    | http://purl.org/dc/terms/                      |
| Schema                                         | schema | https://schema.org/                            |
| Quantity, Unit, Dimension and Type             | qudt   | http://qudt.org/schema/qudt/                   |
| dbpedia ontology                               | dbo    | http://dbpedia.org/ontology/                   |
| Map for Scrutiny                               | m4s    | http://purl.org/map4scrutiny-core#             |
| Ontologia della Camera dei deputati            | ocd    | http://dati.camera.it/ocd/                     |
| Bibliographic Ontology                         | bibo   | http://purl.org/ontology/bibo/                 |
| Simple Event Model Ontology                    | sem    | http://semanticweb.cs.vu.nl/2009/11/sem/       |
| PROV Ontology                                  | prov   | https://www.w3.org/ns/prov-o                   |
| Time Ontology                                  | time   | https://www.w3.org/2006/time                   |
| Simple Knowledge Organization System           | skos   | http://www.w3.org/2004/02/skos/core#           |
| Organization Ontology                          | org    | http://www.w3.org/ns/org#                      |
| Parliamentary Core                             | core   | http://purl.org/polis/ar/core#                 |
| Parlimentary Initiatives                       | ini    | http://purl.org/polis/ar/initiatives#          |
| Biographical data of the Members of Parliament | bio    | http://purl.org/polis/ar/biographical-profile# |
| Activities of the Members of the Parliament    | mpact  | http://purl.org/polis/ar/mp-activities#        |
| UK Parliament Election Ontology                | pe     | http://parliament.uk/ontologies/election/      |


## The Terms
| Domain | foaf:Person                   | A person in the context of the Parliament |                                    |             |             |                                                                                        |
|--------|-------------------------------|-------------------------------------------|------------------------------------|-------------|-------------|----------------------------------------------------------------------------------------|
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | Name                          | foaf:name                                 | xsd:string                         | 0-1         |             |                                                                                        |
| DP     | Birthday                      | foaf:birthday                             | xsd:date                           | 0-1         |             |                                                                                        |
| DP     | Gender                        | schema:gender                             | xsd:string                         | 0-1         |             |                                                                                        |
| DP     | Profession                    | schema:jobTitle                           | xsd:string                         | 0-1         |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
| Domain | m4s:Parliamentarian           | A member of the Parliament                |                                    |             |             |                                                                                        |
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | Identifier                    | core:identifier                           | xsd:uri                            | 1           |             |                                                                                        |
| OP     | Participated in legislature   | core:belongsToLegislature                 | ocd:legislatura                    | 1-*         |             |                                                                                        |
| OP     | Served a mandate              | ocd:rif_mandatoCamera                     | ocd:mandatoCamera                  | 1-*         |             |                                                                                        |
| OP     | Has an habilitation           | bio:hasHabilitation                       | bio:Habilitation                   | 0-*         |             |                                                                                        |
| OP     | Has an award                  | dbo:award                                 | dbo:Award                          | 0-*         |             |                                                                                        |
| OP     | Has a Title                   | bio:hasTitle                              | bio:Title                          | 0-*         |             |                                                                                        |
| OP     | Published                     | bio:authorOf                              | bio:PublishedWork                  | 0-*         |             |                                                                                        |
| OP     | Performs a role               | bio:hasRole                               | bio:Role                           | 0-*         |             |                                                                                        |
| OP     | Has a membership              | core:hasMembership                        | core:Membership                    | 0-*         |             |                                                                                        |
| OP     | was rapporteur in             | mpact:wasRapporteurIn                     | ----                               | 0-*         |             | Range not specified for more flexibility                                               |
| OP     | did youth parliament activity | mpact:didYouthParliamentActivity          | mpact:YouthParliamentActivity      | 0-*         |             |                                                                                        |
| OP     | did requisition               | mpact:didRequisition                      | ocd:richiestaParere                | 0-*         |             |                                                                                        |
| OP     | did commission activity       | mpact:didCommissionActivity               | mpact:CommissionActivity           | 0-*         |             |                                                                                        |
| OP     | did parliamentary activity    | mpact:didParliamentaryActivity            | mpact:ParliamentaryActivity        | 0-*         |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
| Domain | ocd:membroGoverno             | A member of the Government                |                                    |             |             |                                                                                        |
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | duty                          | core:duty                                 | xsd:string                         | 0-*         |             | It is preferred to use core:holdsDuty and org:Post when a controlled vocabulary exists |
| OP     | Holds a duty                  | core:holdsDuty                            | org:Post                           | 0-*         |             |                                                                                        |
| OP     | Belongs to a Government       | ocd:rif_governo                           | ocd:governo                        | 1           |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
| Domain | core:Guest                    | a rdfs:subClassOf foaf:Person             | A guest that visits the Parliament |             |             |                                                                                        |
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | honour                        | core:honour                               | xsd:boolean                        | 0-1         |             | A guest of Honour if true.                                                             |
| DP     | country                       | dbo:country                               | dbo:Country                        | 0-1         |             |                                                                                        |
| DP     | duty                          | core:duty                                 | xsd:string                         | 0-*         |             | It is preferred to use core:holdsDuty and org:Post when a controlled vocabulary exists |
| OP     | Holds a duty                  | core:holdsDuty                            | org:Post                           | 0-*         |             |                                                                                        |

