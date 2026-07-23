# ApplAI Project Log from Wednesday July 23rd, 2026

## Prompts
* What are the standard keywords ATS are looking for in resumes

* Give me the most extensive data-model for storing skills, experiences and certificates that can be used to compile ATS compliant resumes and cover letters.   
Comply with international standards such as "HR Open Consortium" or the new TCP standard when possible. Otherwise follow best practice. 
Represent the datamodel in UML format

## Actions done
-> created myCV folder with some draft template files for the generation of resumes: [_myCV_Atomic data for jop appliance artefacts](../../04%20MODEL/02%20DATA/CV/myCV/_myCV_Atomic%20data%20for%20jop%20appliance%20artefacts.md)



## Key Lessons learned
* ATS will scan for skill-related keywords to primarelycheck whether teir job offer matches with resumees. So when they are looking for  a "Project Office Manager" they will look for "Project Office Manager" in your CV. SOO bloody simple!

-> So I can afford a certain level of **pragmatisem when defining my MetaLevel keywords for my mardown formatted skills.md and experiece.md files**.  

* Next level ATS will try to find to extract skills and experiences on the atomic level where they finally can look for gaps, context, inconsistencies, general sense and other patterns beyond isolated skills and experiences. 

## Single Source Data Format
One of the key modules is the Single Source of Resume-relevant data from which all Resumes, CoverLetters etc. shall be generated. It must provide the following characteristica / Requirements: 

* **Keywords must comply with ATS standards**: 
The keywords to be used in SourceFiles must comply with what ATS is normally looking for and therefore should be compliant with the [HR Open Standarts for Resumees](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/)    .   

* **Easy to edit:** Every candidate must be able to edit his or her personal data as easy as possible in an easy to handle format in a free accessible form that remains easy, accessible and valid over time and independent from products and services. This is the main reason why we have chosen Markdown (*.md) files to become the file-format to store and manage all personal source data. 

* **Timeless Format and Storage**: You data must be in a format that is still accessible and editiable after decades. With Markdown-files we feel on the save side. Additionally those files are compact, easy to version, backup and easy to convert into other format. 

* **Convertablity**: The raw data needs to be easy to be converted into other fileformat (such as JSON, LJSON, PDF, etc. ) or database formats that will be used to upload them into other CV-Editors, or ATS. We cannot assume (yet) that anybody will build an interface to load our files as is.

* **Compilability**: The raw data needs to be easy be compiled into high-level documents such as resumes etc. When doing so, the compiled artefact should be able to point back to the source of elements it is compiled from. 


--- 

## Decision 

### SourceData = 100% Markddown
We have chosen Markdown (*.md) files to become THE Standard file-format to store and manage all personal source data. 

### Keep Sources atomic on the file-level
Every Experience and Skill will be stored in its own (Markdown) file. 
Although this might it more difficult to overlook, sort, filter and manage the plethora of experiences and skill, he possibility of hyperlinking and compiling them into larger documents (eiter by hand or my machine and versioning outweight the annoyances.

Further, on the atomic level skills and experiences can be added and modified independently from documents where they are used. Tools might be provided to sync sources with already generated documents - which for Resumes that already have been sent, is not a requirement.


## Keywords
When building the common