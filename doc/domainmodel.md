# This is the highlevel domain model

```mermaid
classDiagram
 class Association {
    	associationId : UUID
        associationType : associationType
        role : associationRole
        state : state
        consumers : x-nl-okbb-Association
        person : personId or Person
        offering : offeringId
    }
    class `x-nl-okbb-Association` {
    	consumerKey : string = "x-nl-okbb"
	    totalHours : int
        approvedHours: int
	    programOfferingAssociationId : string
	    courseOfferingAssociationId : string
        company: Organisation

        
    }
    class Person {
        personId : UUID
        primaryCode : identifierEntity
        givenName : string
        surnamePrefix : string 
        surname : string
        displayname : string
        activeEnrollment : boolean 
        affiliations : personAffiliations
        mail : string
        languageOfChoice: string[]
		otherCodes: identifierEntity[]
    	consumers : x-nl-okbb-Person
    }

    class `x-nl-okbb-Person` {
    	consumerKey : string = "x-nl-okbb"
        preferredName: string
	    idCheckName : string
    }


    class Offering {
       offeringId : UUID
    }
    class Organization {
        organizationId : uuid-string
        primaryCode : IdentifierEntry
        organizationType : string
        name : string
        description : LanguageTypedString[]
        addresses : Address object[]
        link : uri-string
        logo : uri-string
        otherCodes : IdentifierEntry[]
        parent : organizationId or Organization object
        children : organizationId[] or Organization object[]
        validFrom : date-string
        validTo : date-string
    }
    class `x-nl-okbb-Organization` {
        consumerKey : string = "x-nl-okbb"
		leerbedrijfID : string
    }
    Organization o-- `x-nl-okbb-Organization`
    x-nl-okbb-Association -- Organization

    Association -- Offering 
    Association o-- `x-nl-okbb-Association`
    Association -- Person
    Person o-- `x-nl-okbb-Person`
    

```
