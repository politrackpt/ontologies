---
config:
  layout: elk
---
flowchart TB
    LS("Legislative Session") -- hasLegislature --> Leg("Legislature")
    PG("Parliamentary Group") -- hasParty --> Party("Party")
    PG -- hasLegislature --> Leg
    MP("Member of Parliament") -.-> Person("Person")
    MG("Member of Government") -.-> Person
    Guest("Guest") -.-> Person
    MP -- hasMandate --> Mandate("Mandate")
    Mandate -- hasLegislature --> Leg
    Mandate -- hasParliamentaryGroupMembership --> PGM(Parliamentary Group Membership)
    PGM -- hasParliamentaryGroup --> PG
    Duty(Duty)
    Situation(Situation)
    Mandate -- hasDuty --> Duty
    Mandate -- hasSituation --> Situation

    Ini("Initiative") -- hasAuthor --> MP("Member of Parliament")
    Ini -- hasLegislature --> Leg
    Ini -- hasLegislativeSession --> LS
    Ini -- hasAnnex --> An("Annex")
    Ini -- hasChangeProposal --> CP("Change Proposal")
    CP -- hasAuthor --> MP
    DAR("DAR Publication") -- hasLegislature --> Leg
    DAR -- hasLegislativeSession --> LS
    CP -- hasPublication --> DAR
    Ini -- hasProponent --> MP & CG("Citizen Group") & Com("Commission") & Gov("Government") & RLA("Regional Legislative Assembly") & PG("Parliamentary Group")
    Ini -- originatedFromEU --> EU("European Initiative")
    Ini -- originatedFrom --> Ini
    Ini -- originated --> Ini
    Ini -- hasContent --> Content("Content")
    Ini -- hasPetition --> P("Petition")
    P -- hasLegislature --> Leg
    P -- hasLegislativeSession --> LS
    IT("InitiativeType") -.-> Ini
    Ev(Event)
    Ini -- hasEvent --> Ev

    Ev -- hasJointInitiatives --> Ini("Initiative")
    Ev -- hasAnnex --> An("Annex")
    Ev -- hasPublication --> DAR("DAR Publication")
    Ev -- hasAppeal --> MP("Member of Parliament") & PG("Parliamentary Group")
    Ev -- hasJointActivity --> Act("Activitiy")
    Ev -- hasJointDiscussion --> P("Petition") & PAP("Public Account Proceedings")
    Ev -- hasApprovedDiploma --> D("Diploma")

    Ev -- hasVote --> V("Vote")
    V -- hasAbsent --> MP("Member of Parliament") & PG("Parliamentary Group")
    V -- hasInFavor --> MP & PG
    V -- hasAgainst --> MP & PG
    V -- hasAbstained --> MP & PG
    Ev -- hasIntervention --> I("Intervention")
    I -- hasSpeaker --> Sps("Speakers")
    Sps -- hasSpeaker --> MP & MG("Member of Government")
    Sps -- hasGuest --> Guest("Guest")
    EC("Event Commission") -- hasCommission --> C("Commission")
    EC -- hasSubCommission --> C
    Ev -- hasEventCommission --> EC
    EC -- hasVote --> V
    C -- hasPublication --> DAR("DAR Publication")
    C -- hasLegislature --> Leg("Legislature")
    EC -- hasLegislature --> Leg
    EC -- hasLegislativeSession --> LS("Legislative Session")
    EC -- hasPublication --> DAR
    R("Rapporteur") -- hasMemberOfParliament --> MP
    EC -- hasRapporteur --> R
    EC -- hasRemittance --> Rem("Remittances")
    EC -- hasDocument --> Doc("Document")
    EC -- hasReportPublication --> RP("Report Publication")
    EC -- hasHearing --> RA("Related Activity")
    EC -- hasAudience --> RA