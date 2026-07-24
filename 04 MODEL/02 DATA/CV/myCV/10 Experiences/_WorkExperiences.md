# Work Experience Data Scheme

* [**TCP Schema definitions**](../../../xSTANDARDS/adhoc/Experiences_JSONScheme.md) in JSON-format

## Filename

> YYMMCnn_ORG_Titel

Where

1. **YYMMCnn** = **ID** as described below. 
2. **ORG** = Name of Organisation as defined below.
3. **Titel** = Short Description ("Titel") of the Experience as defined below.

## Schema

1. **ID**: Unique ID like for example **2606PP01** that is created as described above for FileName Creation: 

    * **YYMM**: Year and Month when experience has started. E.g. **2512** = December 2025

    * **C**: Experience Type  

    * **PC** = payed contract work  

    * **PP** = private project, initiative resulting in sellable products, service or providing tangible value  

    * **DB** = de Bono work (pitching, drafting, prototypes for getting the contract)
    
    * **nn**: unique number to list tasks happening the same month

in TPC referred to as "experienceType" 

2. **Title**: Official Job/Position Titel given when executing the job (refers to TCP "title")

2. **Short**: short description of experience with max. 80 characters. Will be used in FileName generation and will be displayed in the Resume. Use the "Description" field for more extensive description and comments. 

3. **Description**: end2end solo-creation of a Perlexity co-piloted extended Workout Timer Web- and MobileApp with currently 78 paying users.   

4. **Start**: YYMMDD   (TCP -> "start")

5. **End**: YYMMDD    (TCP -> "end")

6. **Descriptions**:
    * **Summary**: Led design and implementation of full-stack applications and workflow automation across customer and internal platforms.
    
    * **Duties**: Developed React and TypeScript frontends, .NET services, automation scripts, APIs, and CI/CD workflows.

    * **SkillsAndAccomplishments**: Delivered measurable efficiency gains through automation, improved release quality, and reduced manual operations

    * **plainTextATS**: Senior Full-Stack Engineer responsible for designing and implementing React, TypeScript, and .NET applications; building API integrations; automating workflows; and delivering measurable process improvements.

7. **Rresponsibilities**
    * **text**: Designed and maintained full-stack business applications using React TypeScript, and .NET.
    **category**: "engineering"  
    **importance**: 0.95 
     **order**: 1

    * **text**: GroupLeading a Team of 5
    **category**: "group-lead"  
    **importance**: 0.95 
     **order**: 1

8. **Achievements**
    * **statement**: Reduced manual processing time for document-driven workflows by 65% through automated parsing and validation pipelines.
        * **action**: Built automated parsing and validation pipelines
        * **result**: Reduced manual processing time by 65%
        * **impactAreas**: "time", "quality", "efficiency"
 
     * **statement**: increased employee satisfaction within team for 75% through personal leadership and established motivation program
     
        * **action**: indroduced tools, structures and processings to gain more time for interpersonal communication and proactive helping and coaching
        * **result**: team satisfaction increased 75%. Team is considered "best" team in the company
        * **impactAreas**: "motivation", "health", "efficiency"

8. **Projects**
    * **name**: Workflow Automation Platform
        * **Role**: Technical Lead
        * **Description**: Unified intake, validation, and processing for internal operations workflows
        * **RepositoryUrl**: https://github.com/example/workflow-platform
        * **Confidential**: "false"
        * **SkillsUsed**:
            * "TypeScript"
            * "Mongo DB"

    * **name**: Workflow Automation Platform2
        * **Role**: Technical Lead
        * **Description**: Unified intake, validation, and processing for internal operations workflows
        * **RepositoryUrl**: https://github.com/example/workflow-platform
        * **Confidential**: "false"
        * **SkillsUsed**:
            * "TypeScript"
            * "Mongo DB"

"competenciesDemonstrated": [
    {
      "competencyName": "Problem Solving",
      "taxonomy": "internal-competency",
      "proficiencyLevel": "advanced",
      "demonstratedBy": ["achievement", "project"],
      "confidenceScore": 0.86
    },
    {
      "competencyName": "Technical Leadership",
      "taxonomy": "internal-competency",
      "proficiencyLevel": "advanced",
      "demonstratedBy": ["responsibility", "project"],
      "confidenceScore": 0.84
    }
  ],
  
7. **ManDays**: amount of full manydays. When from - till are 90 days but assignement was just 50% MD will just be 45. 

8. **Type**: (TCP -> "experienceType")
    * **employment**
    
9. **Status**:   

    * **active** = work Experience, Skill etc. still present and recently applied. (TCP -> status)

10. **RoleLevel**: (TCP -> "roleLevel")

    * **senior**

11. **EmploymentRelationship**:  (TCP = "employmentRelationship")
    * **"full_time"**

11. **WorkArrangement**:  (TCP = "workArrangement")
    * **"hybrid"**
    
12. **EmploymentType**:  (TCP = "employmentType")
    * **"full_time"**  

13. **Organization**:  (TCP = "organization")
    * **Name**: **Example Systems AG**
    * **LegalName**: **Example Systems AG**
    * **Website**: **https://example.com**
    * **Industry**:
        *  **Taxonomy**: **internal-industry**
        *  **Term**: **Software**
    * **CountryCode**:  (TCP = "countryCode")
        * **"CH"** 
    
14. **Locations**: (TCP = "locations")
    * **city**: Zug,
      **formatted**: Zug, Switzerland,
      **countryCode**: CH,
      **type**: "worksite", 
      **isPrimary**: "true"
      
    * **city**: Seoul,
      **formatted**: Seoul, North-Korea,
      **countryCode**: 
      **type**: "remote", 
      **isPrimary**: "false"

15. **Workload**: 
    * **hoursPerWeek**: 42.5
    * **ftePercent**: 100

* **git**: reference to experience related GitHub-SPE-page such as https://github.com/realB12/FluXTimerPRJ that might serve as a SinglePointOfEntry-Document (SPE) of a full (project) documentation set. 