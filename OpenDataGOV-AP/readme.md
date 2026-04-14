# OpenDataGOV -AP a Linked Data Application Profile

## Introduction
This file presents the OpenDataGOV -AP, a Linked Data Application Profile [1] - submitted to DCMI 2026 - in review.

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
| **Domain**     | ini:DARSeries2       | rdfs:subClassOf ini:DARPublication     |
|            |                      |                                        |
| **Domain**     | ini:DARSeparata      | rdfs:subClassOf ini:DARPublication     |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2A      | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2B      | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2C      | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2D      | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2E      | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries1A      | rdfs:subClassOf ini:DARSeries1         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2CRC    | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2CGOPOE | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2SCOE   | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2CCEI   | rdfs:subClassOf ini:DARSeries2         |
|            |                      |                                        |
| **Domain**     | ini:DARSeries2SOE    | rdfs:subClassOf ini:DARSeries2         |


