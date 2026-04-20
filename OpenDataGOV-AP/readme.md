# OpenDataGOV - AP a Linked Data Application Profile

## Introduction
This file presents the OpenDataGOV - AP, a Linked Data Application Profile [1] - submitted to DCMI 2026 - in review.

[1] T. Cruz, J. Lourenço, M. Curado-Malta, and J. Bispo, "OpenDataGOV-AP: A Linked Data Application Profile for Parliamentary Activities," in Proc. 24th Int. Conf. on Dublin Core and Metadata Applications (DCMI 2026), Seoul, South Korea, 2026. (Under review)

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

### Core
#### Person

| Domain | foaf:Person                   | A person in the context of the Parliament |                                    |             |             |                                                                                        |
|--------|-------------------------------|-------------------------------------------|------------------------------------|-------------|-------------|----------------------------------------------------------------------------------------|
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | Name                          | foaf:name                                 | xsd:string                         | 0-1         |             |                                                                                        |
| DP     | Birthday                      | foaf:birthday                             | xsd:date                           | 0-1         |             |                                                                                        |
| DP     | Gender                        | schema:gender                             | xsd:string                         | 0-1         |             |                                                                                        |
| DP     | Profession                    | schema:jobTitle                           | xsd:string                         | 0-1         |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
| **Domain** | **m4s:Parliamentarian**           | **A member of the Parliament**             |                                    |             |             |                                                                                        |
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
| **Domain** | **ocd:membroGoverno**             | **A member of the Government**                |                                    |             |             |                                                                                        |
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | duty                          | core:duty                                 | xsd:string                         | 0-*         |             | It is preferred to use core:holdsDuty and org:Post when a controlled vocabulary exists |
| OP     | Holds a duty                  | core:holdsDuty                            | org:Post                           | 0-*         |             |                                                                                        |
| OP     | Belongs to a Government       | ocd:rif_governo                           | ocd:governo                        | 1           |             |                                                                                        |
|        |                               |                                           |                                    |             |             |                                                                                        |
| **Domain** | **core:Guest**                    | **a rdfs:subClassOf foaf:Person**             | **A guest that visits the Parliament** |             |             |                                                                                        |
|        | label                         | Term                                      | Range                              | Cardinality | Description | Comments                                                                               |
| DP     | honour                        | core:honour                               | xsd:boolean                        | 0-1         |             | A guest of Honour if true.                                                             |
| DP     | country                       | dbo:country                               | dbo:Country                        | 0-1         |             |                                                                                        |
| DP     | duty                          | core:duty                                 | xsd:string                         | 0-*         |             | It is preferred to use core:holdsDuty and org:Post when a controlled vocabulary exists |
| OP     | Holds a duty                  | core:holdsDuty                            | org:Post                           | 0-*         |             |                                                                                        |
#### Mandate

| **Domain** | **ocd:mandatoCamera**  | **A mandate of a member of the parliament** |               |         |                                            |      |
|------------|------------------------|---------------------------------------------|-------------------|-------------|------------------------------------------------|----------|
|            | label                  | Term                                        | Range             | Cardinality | Description                                    | Comments |
| DP         | Identifier             | core:identifier                             | xsd:string        | 0-1         | The code that uniquely identifies the Mandate. |          |
| DP         | Parliamentary name     | core:parliamentaryName                      | xsd:string        | 1-*         |                                                |          |
| OP         | Holds a duty           | core:holdsDuty                              | org:Post          | 0-*         |                                                |          |
| OP         | Belongs to legislature | core:belongsToLegislature                   | ocd:legislatura   | 1           |                                                |          |
| OP         | Has membership         | core:hasMembership                          | core:Membership   | 1-*         |                                                |          |
| OP         | is in situation        | ocd:tipoProclamazione                       | ocd:proclamazione | 1-*         |                                                |          |

#### Organisational Body
| **Domain** | **ocd:organo**        | **An Organisational Body at the Parliament** |                                  |         |                                                      |      |
|------------|-----------------------|----------------------------------------------|--------------------------------------|-------------|----------------------------------------------------------|----------|
|            | label                 | Term                                         | Range                                | Cardinality | Description                                              | Comments |
| DP         | identifier            | core:identifier                              | xsd:string                           | 1           | The code that uniquely identifies the Organisation Body. |          |
| DP         | description           | dct:description                              | xsd:string                           | 0-1         |                                                          |          |
| DP         | has a name            | foaf:name                                    | xsd:string                           | 0-1         |                                                          |          |
| DP         | has an Acronym        | qudt:acronym                                 | xsd:string                           | 0-1         |                                                          |          |
| OP         | inLegislature         | core:belongsToLegislature                    | ocd:Legislatura                      | 1           |                                                          |          |
|            |                       |                                              |                                      |             |                                                          |          |
|            |                       |                                              |                                      |             |                                                          |          |
| **Domain**     | **core:Commission**       | **rdfs:subClassOf ocd:organo**                   | **A Comission of a Legislature.**         |             |                                                          |          |
|            | label                 | Term                                         | Range                                | Cardinality | Description                                              | Comments |
| DP         | number                | dbo:number                                   | xsd:nonNegativeInteger               | 0-1         | The number of the commission                             |          |
| OP         | publishes in the DAR  | ini:isPublishedInDAR                         | ini:DARPublication                   | 0-*         |                                                          |          |
| OP         | is a sub-comission of | core:isSubComissionOf                        | core:Comission                       | 0-*         |                                                          |          |
| OP         | has sub-comission     | core:hasSubComission                         | core:Comission                       | 0-*         |                                                          |          |
|            |                       |                                              |                                      |             |                                                          |          |
|            |                       |                                              |                                      |             |                                                          |          |
| **Domain**     | **core:WorkingGroup**     | **rdfs:subClassOf ocd:organo**                   | **A Working Group of a Legislature.**     |             |                                                          |          |
|            |                       |                                              |                                      |             |                                                          |          |
|            |                       |                                              |                                      |             |                                                          |          |
| **Domain**     | **core:ARWorkingGroup**   | **rdfs:subClassOf ocd:organo**                   | **An AR Working Group of a Legislature.** |             |                                                          |          |
#### Situation

| **Domain** | **ocd:proclamazione**    | **A Situation of a document**     |         |         |                                       |      |
|------------|--------------------------|-----------------------------------|-------------|-------------|-------------------------------------------|----------|
|            | label                    | Term                              | Range       | Cardinality | Description                               | Comments |
| DP         | date-range               | dct:date                          | xsd:literal | 0-1         | A range or a single date if it is ongoing |          |
|            |                          |                                   |             |             |                                           |          |
| **Domain**     | **core:Withdrawal**          | **rdfs:subClassOf ocd:proclamazione** |             |             |                                           |          |
|            |                          |                                   |             |             |                                           |          |
| **Domain**     | **core:Incumbent**           | **rdfs:subClassOf ocd:proclamazione** |             |             |                                           |          |
|            |                          |                                   |             |             |                                           |          |
| **Domain**     | **core:PermantentIncumbent** | **rdfs:subClassOf ocd:proclamazione** |             |             |                                           |          |
|            |                          |                                   |             |             |                                           |          |
| **Domain**     | **core:TemporaryIncumbent**  | **rdfs:subClassOf ocd:proclamazione** |             |             |                                           |          |
|            |                          |                                   |             |             |                                           |          |
| **Domain**     | **core:Deceased**            | **rdfs:subClassOf ocd:proclamazione** |             |             |                                           |          |

#### Post

| **Domain** | **org:Post**       |                      |         |         |                                       |      |
|------------|--------------------|--------------------------|-------------|-------------|-------------------------------------------|----------|
|            | label              | Term                     | Range       | Cardinality | Description                               | Comments |
| DP         | A date-range       | dct:date                 | xsd:literal | 0-1         | A range or a single date if it is ongoing |          |
|            |                    |                          |             |             |                                           |          |
| Domain     | core:PAR           | rdfs:subClassOf org:Post |             |             |                                           |          |
|            |                    |                          |             |             |                                           |          |
| Domain     | core:VicePAR       | rdfs:subClassOf org:Post |             |             |                                           |          |
|            |                    |                          |             |             |                                           |          |
| Domain     | core:Secretary     | rdfs:subClassOf org:Post |             |             |                                           |          |
|            |                    |                          |             |             |                                           |          |
| Domain     | core:ViceSecretary | rdfs:subClassOf org:Post |             |             |                                           |          |

#### Party

| **Domain** | **core:Party** | **a rdfs:subClassOf org:Organization** | **A political party** |         |      |         | 
|------------|----------------|----------------------------------------|-----------------------|-------------|----------|-------------|
|            | label          | Term                                   | Range                 | Cardinality | Comments | Description |
| DP         | name           | foaf:name                              | xsd:string            | 1           |          |             |
| DP         | acronym        | qudt:acronym                           | xsd:string            | 1           |          |             |

#### Parliamentary Group

| **Domain** | **core:parliamentaryGroup** | **skos:broadMatch ocd:gruppoParlamentare**             | **A parlamentary group of a party** |  |                                   |      |
|------------|-----------------------------|--------------------------------------------|-----------------|-------------------------------------|--------------------------------------------|----------|
|            | label                       | Term                                       | Range           | Cardinality                         | Description                                | Comments |
| DP         | date-range                  | dct:date                                   | xsd:literal     | 0-1                                 | A range or a single date if it is ongoing. |          |
| OP         | is of party                 | core:isOfParty                             | ini:Party       | 1                                   |                                            |          |
| OP         | belongs to legislature      | core:belongsToLegislature                  | ocd:legislatura | 1                                   |                                            |          |

#### Government
| **Domain** | **ocd:governo** | **A Government of the Country** |                        |         |                                                  |      |
|------------|-----------------|---------------------------------|----------------------------|-------------|------------------------------------------------------|----------|
|            | label           | Term                            | Range                      | Cardinality | Description                                          | Comments |
| DP         | number          | dbo:number                      | xsd:nonNegativeInteger<br> | 0-1         | translation from the roman numeral to arabic numeral |          |

#### Constutency
| **Domain** | **pe:ConstituencyArea** | **An electoral region** |        |         |      |         |
|------------|-------------------------|-------------------------|------------|-------------|----------|-------------|
|            | label                   | Term                    | Range      | Cardinality | Comments | Description |
| DP         | identifier              | core:identifier         | xsd:string | 1           |          |             |
| DP         | name                    | foaf:name               | xsd:string | 1           |          |             |

### Initiatives
#### Initiative


| **Domain** | **ini:Initiative**                | **subclassOf: ocd:Atto**         | **An Initiative in the context of the Parliament**                                                                          | ****        | **** | **** | ****                                                                                           |
|------------|-----------------------------------|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------------|------|------|------------------------------------------------------------------------------------------------|
|            | label                             | Term                             | Range                                                                                                                       | Cardinality | VES  | SES  | Description                                                                                    |
| DP         | identifier                        | core:identifier                  | xsd:string                                                                                                                  | 1           |      |      | The code that uniquely identifies the Initiative.                                              |
| DP         | title                             | dct:title                        | xsd:string                                                                                                                  | 1           |      |      | The title of the initiative.                                                                   |
| DP         | number                            | dbo:number                       | xsd:nonNegativeInteger                                                                                                      | 1           |      |      | The number of the initiative. Uniquely identifies the initiative according to its type.        |
| DP         | text substitution details         | ini:textSubstitutionDetails      | xsd:string                                                                                                                  | 0-1         |      |      | Gives details regarding a substitution of the text                                             |
| OP         | belongs to legislature            | core:belongsToLegislature        | ocd:legislatura                                                                                                             | 1           |      |      | The legislature in which the initiative was introduced.                                        |
| OP         | belongs to legislative session    | core:belongsToLegislativeSession | ocd:sessioneLegislatura                                                                                                     | 1           |      |      | The legislative session in which the initiative was introduced.                                |
| OP         | was authored by mp                | ini:hasAuthor                    | m4s:Parliamentarian                                                                                                         | 0-*         |      |      | MPs responsible for authoring this initiative.                                                 |
| OP         | was proposed by proponent         | ini:hasProponent                 | m4s:Parliamentarian, ini:ParliamentaryGroup, ocd:governo, ini:Commission, ini:RegionalLegislativeAssembly, ini:CitizenGroup | 0-*         |      |      | whom proposed the initiative. The allowed proponents may vary by type of initiative.           |
| OP         | has event                         | ini:hasEvent                     | ini:Event                                                                                                                   | 0-*         |      |      | The events that have happened during the initiative lifecycle.                                 |
| OP         | has annex                         | ini:hasAnnex                     | bibo:Document                                                                                                               | 0-*         |      |      | The documents in annex to the initiative.                                                      |
| OP         | grew out of initiative            | ini:grewOutOf                    | ini:Initiative, ini:EuropeanInitiative                                                                                      | 0-*         |      |      | Other initiatives that lead to the creation of the initiative.                                 |
| OP         | led to initiative                 | ini:ledTo                        | ini:Initiative                                                                                                              | 0-*         |      |      | Other initiatives that were created because of the initiative.                                 |
| OP         | received a change proposal        | ini:receivedChangeProposal       | ini:ChangeProposal                                                                                                          | 0-*         |      |      | Change proposals made to the initiative.                                                       |
| OP         | has related petition              | ini:hasRelatedPetition           | ini:Petition                                                                                                                | 0-*         |      |      | Petitions associated with the initiative.                                                      |
| OP         | has content                       | ini:hasContent                   | bibo:Document                                                                                                               | 0-1         |      |      | The initiative content, as a document, containing the full text and the url link to access it. |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:ConstitutionalRevisionProject** | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:DeliberationProject**           | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:LawProject**                    | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:LawProposal**             | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:ParliamentaryAppreciation**     | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:ParliamentaryInquiry**          | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:PopularReferendumInitiative**   | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:Ratification**                 | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:ResolutionProposal**            | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:ResolutionProject**             | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |
|            |                                   |                                  |                                                                                                                             |             |      |      |                                                                                                |
| **Domain**     | **ini:RulesOfProcedureProject**       | **a rdf:subClassOf: ini:Initiative** |                                                                                                                             |             |      |      |                                                                                                |

#### European Initiative


| **Domain** | **ini:EuropeanInitiative** | **subclassOf: ocd:Atto** | ****       | **An European Initiative** | ****        | ****     |
|------------|----------------------------|--------------------------|------------|----------------------------|-------------|----------|
|            | label                      | Term                     | Range      | Cardinality                | Description | Comments |
| DP         | url                        | schema:url               | xsd:string | 1                          |             |          |

#### Change Proposal

| **Domain** | **ini:ChangeProposal**                | **A change in a proposal** | ****                    | ****        | ****                                                                                 | ****                                                                                                                                                                                                                                   |
|------------|---------------------------------------|----------------------------|-------------------------|-------------|--------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            | label                                 | Term                       | Range                   | Cardinality | Description                                                                          | Comments                                                                                                                                                                                                                               |
| DP         | identifier                            | core:identifier            | xsd:string              | 1           | The code that uniquely identifies the change.                                        |                                                                                                                                                                                                                                        |
| DP         | type                                  | ini:changeProposalType     | xsd:string              | 0-1         | The type of change proposal.                                                         | Examples seen consisted only of the same type ("Change Proposal"). Since there is no defined controlled vocabulary, this property exists as a data property instead of subclasses.                                                     |
| DP         | Proponent                             | ini:proponent              | xsd:string              | 0-*         | A field indicating which type of group proposed the amendment to the proposal.       | This term is used when the data does not specify which group or individual proposed the amendment. When the proposer is known, we should refer to them as “proposed by a parliamentary group” or “proposed by a member of parliament.” |
| OP         | Published in the DAR                  | ini:isPublishedInDAR       | ini:DARPublication      | 0-*         | The DAR publication where the amendment of the proposal was published.               |                                                                                                                                                                                                                                        |
| OP         | Proposed by parliamentary Group       | ini:isProposedBy           | core:ParliamentaryGroup | 0-*         | A field indicating which parliamentary group proposed the amendment to the proposal. |                                                                                                                                                                                                                                        |
| OP         | Proposed by a member of the parliament | ini:isProposedBy           | m4s:Parliamentarian     | 0-*         | A field indicating which MP proposed the amendment to the proposal.                  |                                                                                                                                                                                                                                        |
#### DAR Publication
| **Domain** | **ini:DARPublication**                             | **a rdfs:subClassOf ocd:pubblicistica** | **A publication in the Oficial journal of the country for laws.** | ****        | ****                          | ****                                                                                 | ****         |
|------------|----------------------------------------------------|-----------------------------------------|-------------------------------------------------------------------|-------------|-------------------------------|--------------------------------------------------------------------------------------|--------------|
|            | label                                              | Term                                    | Range                                                             | Cardinality | VES                           | Description                                                                          | Comments     |
| DP         | number                                             | dbo:number                              | xsd:nonNegativeInteger                                            | 1           |                               | The number of the publication.                                                       |              |
| DP         | code                                               | dbo:code                                | xsd:string                                                        | 1           | A,B,C,D,H,I,K,L,M,O,Q,R,S,T,V | The code of the type of publication.                                                 |              |
| DP         | publish date                                       | dct:date                                | xsd:date                                                          | 1           |                               | The date of the publication.                                                         |              |
| DP         | pages in the DAR corresponding to this publication | schema:pagination                       | xsd:string                                                        | 1           |                               | The range of the pages where the publication is.                                     | number range |
| DP         | pages' identifier                                  | ini:pagesIdentifier                     | xsd:string                                                        | 1           |                               | The code that uniquely identifies the pages for a particular publication in the DAR. |              |
| DP         | url to the DAR publication                         | schema:url                              | xsd:string                                                        | 1           |                               | The link to the web resource containing the publication.                             |              |
| DP         | supplement to the publication                      | ini:publicationSupplement               | xsd:string                                                        | 0-1         |                               | Supplement to the publication.                                                       |              |
| DP         | final page of the supplement                       | ini:publicationSupplementFinalPage      | xsd:string                                                        | 0-1         |                               | Indicates the final page of the supplement                                           |              |
| DP         | observation                                        | ini:observation                         | xsd:string                                                        | 0-1         |                               | An observation regarding the publication.                                            |              |
| OP         | published during legislature                       | core:belongsToLegislature               | ocd:legislatura                                                   | 1           |                               | The legislature in which the publication was published.                              |              |
| OP         | published during legislative session               | core:belongsToLegislativeSession        | ocd:sessioneLegislatura                                           | 1           |                               | The legislative session in which the publication was published.                      |              |

| **Domain** | **ini:DARSeries1**   | **rdfs:subClassOf ini:DARPublication** |
|------------|----------------------|----------------------------------------|
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2**       | **rdfs:subClassOf ini:DARPublication**     |
|            |                      |                                        |
| **Domain**     | **ini:DARSeparata**      | **rdfs:subClassOf ini:DARPublication**     |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2A**      | **rdfs:subClassOf ini:DARSeries2**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2B**      | **rdfs:subClassOf ini:DARSeries2**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2C**      | **rdfs:subClassOf ini:DARSeries2**       |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2D**      | **rdfs:subClassOf ini:DARSeries2**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2E**      | **rdfs:subClassOf ini:DARSeries2**     |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries1A**      | **rdfs:subClassOf ini:DARSeries1**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2CRC**    | **rdfs:subClassOf ini:DARSeries2**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2CGOPOE** | **rdfs:subClassOf ini:DARSeries2**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2SCOE**   | **rdfs:subClassOf ini:DARSeries2**        |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2CCEI**   | **rdfs:subClassOf ini:DARSeries2**         |
|            |                      |                                        |
| **Domain**     | **ini:DARSeries2SOE**    | **rdfs:subClassOf ini:DARSeries2**         |

#### Regional Legislative Assembly
| Domain | ini:RegionalLegislativeAssembly | A regional assembly, like the regionl assembly of Catalunya |           |             |                                                                                        |          |
|--------|---------------------------------|-------------------------------------------------------------|-----------|-------------|----------------------------------------------------------------------------------------|----------|
|        | label                           | Term                                                        | Range     | Cardinality | Description                                                                            | Comments |
| OP     | location                        | sem:hasPlace                                                | sem:Place | 0-1         | The location of the Regional Assembly. This term should be linked to a Wikidata entry. |          |

#### Document
| Domain | bibo:Document       |                  |            |             |                                          |          |
|--------|---------------------|------------------|------------|-------------|------------------------------------------|----------|
|        | label               | Term             | Range      | Cardinality | Description                              | Comments |
| DP     | type                | ini:documentType | xsd:string | 0-1         | The type of document.                    |          |
| DP     | title               | dct:title        | xsd:string | 0-1         | The title of the document                |          |
| DP     | date                | dct:date         | xsd:date   | 0-1         | The date of the document                 |          |
| DP     | url to the resource | schema:url       | xsd:string | 0-1         | The URL link to the file of the document |          |
| DP     | Text                | bibo:content     | xsd:string | 0-1         | The text content of the document         |          |
| DP     | identifier          | core:identifier  | xsd:string | 0-1         | The identifier of the document           |          |

| Domain | bibo:Legislation |                 |            |             |                                   |          |
|--------|------------------|-----------------|------------|-------------|-----------------------------------|----------|
|        | label            | Term            | Range      | Cardinality | Description                       | Comments |
| DP     | identifier       | core:identifier | xsd:string | 0-1         | The identifier of the legislation |          |

#### Event
| Domain | ini:Event        |                                  |                                              |             |                                                                                            |
|--------|------------------|----------------------------------|----------------------------------------------|-------------|--------------------------------------------------------------------------------------------|
|        | label            | Term                             | Range                                        | Cardinality | Description                                                                                |
| DP     | identifier       | core:identifier                  | xsd:string                                   | 1           | The code that uniquely identifies the Event.                                               |
| DP     | type id          | ini:typeId                       | xsd:string                                   | 1           | The identifier of the type of event.                                                       |
| DP     | type             | ini:eventType                    | xml:string                                   | 1           | The type of event.                                                                         |
| DP     | date             | dct:date                         | xsd:date                                     | 1           | The date in which the event occurred.                                                      |
| DP     | code             | dbo:code                         | xsd:string                                   | 1           | The code of the event.                                                                     |
| DP     | observation      | ini:observation                  | xsd:string                                   | 0-1         | Observation regarding the event.                                                           |
| OP     | approves diploma | ini:approvesDiploma              | bibo:Legislation                             | 0-*         | The diplomas approved during this event                                                    |
| OP     | has discussion   | ini:hasDiscussion                | ocd:discussione                              | 0-1         | The discussions that happened during this event.                                           |
| OP     | joint initiative | ini:happensJointlyWithInitiative | ini:Initiative                               | 0-*         | Initiatives that had the same event happening jointly with the initiative from this event. |
| OP     | joint petition   | ini:discussedJointlyWith         | ini:Petition                                 | 0-*         | Petitions that were discussed during the event.                                            |
| OP     | has annex        | ini:hasAnnex                     | bibo:Document                                | 0-*         | Documents annexed to the event.                                                            |
| OP     | has vote         | ini:hasVote                      | ocd:votazione                                | 0-*         | A vote on the initiative.                                                                  |
| OP     | received appeal  | ini:receivedAppeal               | m4s:Parliamentarian, core:ParliamentaryGroup | 0-*         | Defines who appealed the initiative during this event.                                     |
| OP     | is published in  | ini:isPublishedInDAR             | ini:DARPublication                           | 0-*         | Publications in the DAR related to this event.                                             |
| OP     | has activity     | ini:hasActivity                  | prov:Activity                                | 0-*         | The activities that happened during the event.       |

#### Discussion

| Domain | ocd:discussione  |                    |                |             |                                                                                |                                                      |
|--------|------------------|--------------------|----------------|-------------|--------------------------------------------------------------------------------|------------------------------------------------------|
|        |                  | Term               | Range          | Cardinality | Description                                                                    | Comments                                             |
| DP     | date-range       | dct:date           | xsd:date       | 1           | The date in which the plenary reunion occurred, where the discussion happened  | This date range should also encompass the hour range |
| DP     | summary          | dct:abstract       | xsd:string     | 0-1         | The summary and overall theme of the discussion.                               | Older datasets do not have this information.         |
| OP     | has intervention | ocd:rif_intervento | ocd:intervento | 0-*         | The interventions that happened during the discussion.                         | Older datasets do not have this information.         |

#### Intervention

| **Domain** | **ocd:intervento**  | ****                 | ****               | ****        | ****                                                      | ****                                                                                                                                                                                   |
|------------|---------------------|----------------------|--------------------|-------------|-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|            | label               | Term                 | Range              | Cardinality | Description                                               | Comments                                                                                                                                                                               |
| DP         | identifier          | core:identifier      | xsd:string         | 1           |                                                           |                                                                                                                                                                                        |
| DP         | video               | schema:url           | xsd:string         | 0-1         | The video containing the intervention                     |                                                                                                                                                                                        |
| OP         | is published in DAR | ini:isPublishedInDAR | ini:DARPublication | 0-1         | The publication of the intervention transcript in the DAR |                                                                                                                                                                                        |
| OP         | hasSpeaker          | ini:hasSpeaker       | foaf:Person        | 0-1         | The MP, MG or Guest who made the intervention             | To increase reusability without being overly restrictive, the range is defined as foaf:Person, allowing different parliaments to reuse this and accommodate a wider range of speakers. |

#### Comission Event
| **Domain** | **ini:CommissionEvent**                       |                               |                 |         |                                                                         |      |
|------------|-----------------------------------------------|-----------------------------------|---------------------|-------------|-----------------------------------------------------------------------------|----------|
|            | label                                         | Term                              | Range               | Cardinality | Description                                                                 | Comments |
| DP         | observation                                   | ini:observation                   | xsd:string          | 0-1         | An observation regarding the commission event.                              |          |
| DP         | competent                                     | ini:competent                     | xsd:boolean         | 0-1         | Indicates whether the Commission is competent in the matter.                |          |
| DP         | Entry date                                    | ini:entryDate                     | xsd:date            | 0-1         | the date in which the initiative was given entry to the commission.         |          |
| DP         | distribution date                             | ini:distributionDate              | xsd:date            | 0-1         | Date of the distribution between the commissions.                           |          |
| DP         | Extended                                      | ini:extended                      | xsd:boolean         | 0-1         | indicates whether the deadline has been extended.                           |          |
| DP         | Date of the scheduled discussion              | ini:scheduledDiscussionDate       | xsd:date            | 0-1         | The date of the scheduled discussion.                                       |          |
| DP         | Date of request to schedule a plenary         | ini:requestSchedulePlenaryDate    | xsd:date            | 0-1         | The date of the request made to schedule a plenary.                         |          |
| DP         | Awaits Plenary Schedule                       | ini:awaitsPlenarySchedule         | xsd:boolean         | 0-1         | Indicates if it is waiting a plenary schedule                               |          |
| DP         | public appreciation date range                | ini:publicAppreciationDate        | xsd:date            | 0-1         | Defines the start and end dates for the public review of a commission event |          |
| DP         | opinion requested                             | ini:opinionRequested              | xsd:boolean         | 0-1         | Indicates if there are opinion requests                                     |          |
| DP         | opinion received                              | ini:opinionReceived               | xsd:boolean         | 0-1         | Indicates if there are opinions received                                    |          |
| DP         | date subcommission distribution               | ini:subCommissionDistributionDate | xsd:date            | 0-1         | Date of the distribution to subcommissions.                                 |          |
| DP         | indicates the reason for the negative opinion | ini:negativeOpinionReason         | xsd:string          | 0-1         | The reason as to why a negative opinion was given by the commission.        |          |
| DP         | date of the reason for the negative opinion   | ini:negativeOpinionReasonDate     | xsd:date            | 0-1         | The date when the reason for a negative opinion was given.                  |          |
| OP         | attributed to commission                      | ini:attributedToCommission        | core:Commission     | 1-*         | The commission who was attributed the commission event.                     |          |
| OP         | has audition                                  | ini:hasAudition                   | mpact:Audition      | 0-*         |                                                                             |          |
| OP         | has hearing                                   | ini:hasHearing                    | mpact:Hearing       | 0-*         |                                                                             |          |
| OP         | is published in DAR                           | ini:isPublishedInDAR              | ini:DARPublication  | 0-*         | Publications in the DAR related to this commission event.                   |          |
| OP         | has vote                                      | ini:hasVote                       | ocd:votazione       | 0-1         | A vote particular to this commission.                                       |          |
| OP         | has transmission                              | ini:hasTransmission               | ini:Transmission    | 0-*         |                                                                             |          |
| OP         | has rapporteur                                | ini:hasRapporteur                 | m4s:Parliamentarian | 0-*         | The rapporteur of a presented document in the commission event              |          |
| OP         | published report                              | ini:hasPublishedReport            | ini:DARPublication  | 0-*         | The report published in the DAR by the commission                           |          |
| OP         | creates document                              | ini:createsDocument               | bibo:Document       | 0-*         | Associated documents                                                        |          |
| OP         | has subCommission                             | ini:hasSubCommission              | core:Commission     | 0-*         |                                                                             |          |

#### Transmission
| **Domain** | **ini:Transmission** |                  |        |         |         |      |
|------------|----------------------|----------------------|------------|-------------|-------------|----------|
|            | label                | Term                 | Range      | Cardinality | Description | Comments |
| DP         | type                 | ini:transmissionType | xsd:string | 1           |             |          |
| DP         | date                 | dct:date             | xsd:date   | 0-1         |             |          |
| DP         | document date        | dct:created          | xsd:date   | 0-1         |             |          |

### Biographic Profile
#### Award
| **Domain** | **dbo:award** | ****            | ****       | ****        | ****                                                              | ****     |
|------------|---------------|-----------------|------------|-------------|-------------------------------------------------------------------|----------|
|            | label         | Term            | Range      | Cardinality | Description                                                       | Comments |
| DP         | Identifier    | core:identifier | xsd:string | 1           | The code that uniquely identifies the award.                      |          |
| DP         | name          | foaf:name       | xsd:string | 1           | The name of the award.                                            |          |
| DP         | Position      | dbo:number      | xsd:int    | 1           | the position of the award in the list of awards during the years. |          |

#### Published Work
| **Domain** | **bio:PublishedWork** | **a rdfs:subClassOf bibo:Document** |                    |         |                                             |      |
|------------|-----------------------|-------------------------------------|------------------------|-------------|-------------------------------------------------|----------|
|            | label                 | Term                                | Range                  | Cardinality | Description                                     | Comments |
| DP         | identifier            | core:identifier                     | xsd:string             | 1           | The code that uniquely identifies the Document. |          |
| DP         | name                  | foaf:name                           | xsd:string             | 1           |                                                 |          |
| DP         | position              | dbo:number                          | xsd:nonNegativeInteger | 1           |                                                 |          |

#### Habilitation

| **Domain** | **bio:Habilitation** |                     |                    |         |                                                 |      |
|------------|----------------------|-------------------------|------------------------|-------------|-----------------------------------------------------|----------|
|            | label                | Term                    | Range                  | Cardinality | Description                                         | Comments |
| DP         | identifier           | core:identifier         | xsd:string             | 1           | The code that uniquely identifies the Habilitation. |          |
| DP         | name                 | foaf:name               | xsd:string             | 1           |                                                     |          |
| OP         | type                 | bio:isHabilitationLevel | bio:HabilitationLevel  | 0-1         |                                                     |          |
| OP         | status               | bio:habilitationStatus  | bio:HabilitationStatus | 0-1         |                                                     |          |

#### Habilitation Level

| **Domain** | **bio:HabilitationLevel** |                                     |         |         |  |         |      |
|------------|---------------------------|-----------------------------------------|-------------|-------------|------|-------------|----------|
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:PrimarySchool**         | **a rdfs:subClassOf bio:HabilitationLevel** |             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 9    |             |          |
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:MiddleSchool**          | **a rdfs:subClassOf bio:HabilitationLevel** |             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 10   |             |          |
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:EarlyHighSchoo**l       | **a rdfs:subClassOf bio:HabilitationLevel** |             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 11   |             |          |
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:HighSchool**            |**a rdfs:subClassOf bio:HabilitationLevel** |             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 12   |             |          |
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:HigherEducation**       | a rdfs:subClassOf bio:HabilitationLevel |             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 13   |             |          |
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:Bachelor**              |** a rdfs:subClassOf bio:HabilitationLevel **|             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 14   |             |          |
|            |                           |                                         |             |             |      |             |          |
| **Domain**     | **bio:Master**                | **a rdfs:subClassOf bio:HabilitationLevel** |             |             |      |             |          |
|            | label                     | Term                                    | Range       | Cardinanity | VES  | Description | Comments |
|            | level                     | dbo:number                              | xsd:integer | 1           | 15   |             |          |

#### Habilitation Status
| **Domain** | **bio:HabilitationStatus** |                                           |
|------------|----------------------------|-----------------------------------------------|
|            |                            |                                               |
| **Domain**     | **bio:C**                    | **a owl:NamedIndividual, bio:HabilitationStatus** |
|            |                            |                                               |
| **Domain**     | **bio:F**                      | **a owl:NamedIndividual, bio:HabilitationStatus** |



#### Role
| **Domain** | **bio:Role**  |               |                    |         |                                         |      |
|------------|---------------|-------------------|------------------------|-------------|---------------------------------------------|----------|
|            | label         | Term              | Range                  | Cardinality | Description                                 | Comments |
| DP         | identifier    | core:identifier   | xsd:string             | 1           | The code that uniquely identifies the Role. |          |
| DP         | name          | foaf:name         | xsd:string             | 1           |                                             |          |
| DP         | position      | dbo:number        | xsd:nonNegativeInteger | 1           |                                             |          |
| DP         | hasDoneBefore | bio:hasDoneBefore | xsd:boolean            | 0-1         |                                             |          |

#### Title
| **Domain**  | **bio:Title**            |                    |         |                                          |      |
|---------------|-----------------|------------------------|-------------|----------------------------------------------|----------|
| label         | Term            | Range                  | Cardinality | Description                                  | Comments |
| identifier    | core:identifier | xsd:string             | 1           | The code that uniquely identifies the Title. |          |
| name          | foaf:name       | xsd:string             | 1           |                                              |          |
| position      | dbo:number      | xsd:nonNegativeInteger | 1           |                                              |          |

### MP-Activity
#### Requisition
| **Domain** | **ocd:richiestaParere** |                                  |                         |             |                                                                                       |          
|------------|-------------------------|----------------------------------|-------------------------|-------------|---------------------------------------------------------------------------------------|----------|
|            | label                   | Term                             | Range                   | Cardinality | Description                                                                           | Comments |
| DP         | identifer               | core:identifier                  | xsd:string              | 1           | The code that uniquely identifies the Requisition.                                    |          |
| DP         | number                  | dbo:number                       | xsd:nonNegativeInteger  | 1           |                                                                                       |          |
| DP         | subject                 | dct:subject                      | xsd:string              | 1           | The subject of the requisition                                                        |          |
| DP         | date                    | dct:date                         | xsd:date                | 1           |                                                                                       |          |
| OP         | legislature             | core:belongsToLegislature        | ocd:legislatura         | 1           |                                                                                       |          |
| OP         | legislativeSession      | core:belongsToLegislativeSession | ocd:sessioneLegislatura | 1           |                                                                                       |          |
| OP         | public entity type      | mpact:toPublicEntityType         | mpact:PublicEntityType  | 0-1         | Indicates the public entity type where an MP made a requisition (request or inquiry). |          |

| **Domain** | **mpact:Request** | **a rdfs:subClassOf ocd:richiestaParere** |
|------------|-------------------|-------------------------------------------|

| **Domain** | **mpact:Inquiry** | **a rdfs:subClassOf ocd:richiestaParere** |
|------------|-------------------|-------------------------------------------|

#### Public Entity Type
| **Domain** | **mpact:PublicEntityType** | **a rdfs:subClassOf prov:Agent** |
|------------|----------------------------|----------------------------------|

| **Domain** | **mpact:AC** | **a NamedIndividual, mpact:PublicEntityType** |  **Administração Central** |
|------------|--------------|---------------------------------------------|---------------------------------|

| **Domain**     | **mpact:AL**     | a NamedIndividual, mpact:PublicEntityType     |     Administração Local       |
|------------|--------------|---------------------------------------------|---------------------------------|

| **Domain**     | **mpact:AR**     | a NamedIndividual, mpact:PublicEntityType     |    Assembleia da República   |  
|------------|--------------|---------------------------------------------|---------------------------------|

| **Domain**     | **mpact:EI**     | a NamedIndividual, mpact:PublicEntityType       | Entidades Independentes   |    
|------------|--------------|---------------------------------------------|--------------------------------|

| **Domain**     | **mpact:RA**     | **a NamedIndividual, mpact:PublicEntityType**    |   **Regiões Autónomas**         |
|------------|--------------|---------------------------------------------|---------------------------------|

#### Parliamentary Activity
**Domain** `ocd:richiestaParere`

|  | Label | Term | Range | Cardinality | Description | Comments |
|--------|-------|------|-------|-------------|-------------|----------|
| DP | identifier | core:identifier | xsd:string | 1 | The code that uniquely identifies the Requisition. | |
| DP | number | dbo:number | xsd:nonNegativeInteger | 1 | | |
| DP | subject | dct:subject | xsd:string | 1 | The subject of the requisition | |
| DP | date | dct:date | xsd:date | 1 | | |
| OP | legislature | core:belongsToLegislature | ocd:legislatura | 1 | | |
| OP | legislativeSession | core:belongsToLegislativeSession | ocd:sessioneLegislatura | 1 | | |
| OP | public entity type | mpact:toPublicEntityType | mpact:PublicEntityType | 0-1 | Indicates the public entity type where an MP made a requisition. | |

 
| **Domain** | **mpact:AGP** | **a rdfs:subClassOf mpact:ParliamentaryActivity** |  **Atividade do Grupo Parlamentar de Amizade** |

| **Domain**     | **mpact:CER**     | a rdfs:subClassOf mpact:ParliamentaryActivity     |      **Cerimónias**         |

| **Domain**     | **mpact:DEB**     | a rdfs:subClassOf mpact:ParliamentaryActivity     |      **Debates Diversos** |
|------------|--------------|---------------------------------------------|---------------------------------|
| **Domain**     | **mpact:DES**     | a rdfs:subClassOf mpact:ParliamentaryActivity     |     **Deslocação**  |
|------------|--------------|---------------------------------------------|---------------------------------|
| **Domain**     | **mpact:DPO**     | a rdfs:subClassOf mpact:ParliamentaryActivity     |     **Declarações Políticas**  |
|------------|--------------|---------------------------------------------|---------------------------------|
| **Domain**     | **mpact:DPR**     | a rdfs:subClassOf mpact:ParliamentaryActivity     |      **Deslocações do Presidente da República**  |
|------------|--------------|---------------------------------------------|---------------------------------|


