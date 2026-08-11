# ApplAI Project Log from Wednesday July 23rd, 2026

## Perplexity Prompts
* Check: What are the standard keywords ATS are looking for in resumes?

* Give me the most extensive data-model for storing skills, experiences and certificates that can be used to compile ATS compliant resumes and cover letters.   

Comply with international standards such as "HR Open Consortium" or the new TCP standard when possible. Otherwise follow best practice. 
Represent the datamodel in UML format

## Actions done
-> created **myCV folder** with some draft template files for the generation of resumes: [_myCV_Atomic data for jop appliance artefacts](../../04%20MODEL/02%20DATA/CV/myCV/_myCV_Atomic%20data%20for%20jop%20appliance%20artefacts.md)

I am really not sure, whether to store my actual CV data in the TCP standardized JSON format (-> mybe the shorter ... format is better)


## Key Lessons learned
* ATS will scan for skill-related keywords to primarely check whether their job offer matches with resumees. So when they are looking for a "Project Office Manager" they will look for "Project Office Manager" in your CV. SOO bloody simple!

-> So I most probably can afford a certain level of **pragmatism when defining my metaLevel keywords for my markdown formatted skills.yaml and experiece.yaml files**.  

* Next level ATS (only larg companies can afford) will extract skills and experiences on the atomic level where they finally can look for gaps, context, inconsistencies, general sense and other patterns beyond isolated skills and experiences. 

## Single Source Data Format
-> created [Generic DaataModel Requirements](../../04%20MO/02%20DATA/Generic%20DaataModel%20Requirements.md) document. 


--- 

## Decision 

### SourceData = 100% YAML
We have chosen YAML to be THE Standard file-format to store and manage all personal source data. 

### Keep Sources atomic on the file-level
Every Experience and Skill will be stored in its own  YAML file.
Although it might be more difficult to overlook, sort, filter and manage the plethora of such experiences and skill files, the possibility of hyperlinking and compiling them into larger documents (either by hand or by machine and versioning outweight the on time annoyances when creating new items).

Further, on the atomic level, skills and experiences can be added and modified independently from documents where they are used. Tools might be provided to sync these atomic sources with already generated documents - which for Resumees that already have been sent, is not a requirement.

## Keywords
