# OpenDataGOV Linked Data Application Profile

## Introduction
This file presents the Linked Data Application Profile

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
