# ApplAI: a personal, AI automated Job Application & Management Solution
<- [ReadMe](README.md)

---
This documents provides 

> **the Full AppAI Project Outline**

In this sense this document is the most up to date **Single Point of entry (SPE) document** for whatever is going on in this ApplAI Project, whereas the [ReadMe](README.md) is just the publicly exposed (GitHub) summary that might not be aligned to this document on purpose (to keep general communication simplified and stable). 

---

## Current Project STATUS = ON HOLD

->  **[Current Project STATUS](#project-status) Description** 

-> **[Next Steps](#next-steps)**


## Vision Statement
Automatically generate a job application resume and cover-letter from the job-offer's URL plus the organisational framework (such as a Git Repo) and tasks (such as sending the resume) for its efficient follow up and management. 

## The Problem to be solved
1. **No central storage repository to compile from**: We are still today spending **hours typing our resumes over and over again** - sometimes from scratch with important **stuff hard to remember** and - even more importantly - to verify.

2. Although LinkedIn or "[HR Open Standards Organisation](GLOSS/H/HR%20Open%20Standards%20Organisation.md) provide extensive standards for how such data should be stored, they are over-complex for ordinary requirements without frameworks and tools available to efficiently work with those standards. 


## Goals
Provide a local GitHub backuped folder with all your resumee relevant data in well structured, atomic Markdown files you will never lose and from where you can generate nice human readable resumes and cover letters as well as data complete, ATS-standards-compliant artefacts to 

* **Auto-apply for different roles by just providing the jog-offer's URL

* **generate ATS-optimized AND HR readable appliance documents** in parallel.

* provide **adapters for (AI-) 3rd party tools** to cover language, cultural, industry and role specific HR and job interview requirements.  

* **keep your CV-data private** and share it only with those how need in a way that data-leaks on receiver-side could be tracked back to the receiver (trust is ok, checking is better).  

* **prevent data-loss** upon integrated GitHub-versioning and Backup File-Synchronization 

* Send reminders to motivate ongoing work review, updates and adding new experiences on a monthly bases. 

* **Stability**: The here implied data-**standards must not be changed over time**


### Open Source
The schema is open source and community-driven. We release everything we do under the MIT license.

## Architecture (draft) 
What we have currently in mind is  

1. a **local GUI-App for Windows** (.NET C# in Visual Studio Code + Exensions)  

2. Using the best **"money for performance" AI-services** in the background (which are reviewed and might change within a month's notice)
 
3. a minimal **Sales-WebApp** for advertisments, purchasing, downloading and servicing the solutionk (most probably a vibe-copiloted Single Page Application (SPA) built with Microsoft .NET Tech in VSC Editor) 

4. a **BackendServer** to dispatch job-requests from all local Apps. 

5. Github Repos for project documentation, sourcecode management, templates, user manuals and tutorials, and backend I/O caching till need for speed and scale will require more dedicates solutions.  

## Design Principles
to keep data-structure close to HR Open's new TCP-standard without dealing with its overall comoplexity we will keep its components such as experiences, skills etc. in separate files and will therefore work on a more atomic level from where resumes will be dynamically compiled from scratch rather than dealt with as whole.   

### Initial Scope
We keep the current architectural scope limted to a local App, english, Windows, Markdown, PDF, "HR Open Standards Resume/CV"-Standard etc. on purpose being confident to rollout for different OS, devices, platforms, languages, AI providers, etc. 

### Architectural Stability and Change Requests
However the goal is not to provide a customizable architecture but to deliver ONE or several ready made boxed and therefore - concerning architecture - non further customizable-solutions. In this sense, input on architectural design and change is still welcome but we reserve the right to decide alone what currently works best for us as we do not like to switch/change our own platform upon change requests. 

Scaling will be done in the background and will remain on our shoulders. 

## Project STATUS

1. Currently the project can **download a job-offer upon the given in URL** and **save it as an image, PDF and a summary markdown-file in an automatically generated GitRepo** from where the files and folders are downloaded to the local machine where the job has been startet. 

2. We have investigated the [HR Open Standards Consortium](GLOSS/H/HR%20Open%20Standards%20Organisation.md) provided [TCP-JSON Standard]() and found it useful as a state of the art and future proof reference for our own data Standard. However we found the "old"  **[JSON Resume](GLOSS/J/JSON%20Resume.md)**-Standard more hands-on, practical and with its established ecosystem (e.g the "[Reactive Resume](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md) ways more readymade applicable and therefore immediately useful. 

3. We have found the [Reactive Resume](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md) Open Source WebApp quite promising  to be used to efficiently create the required [JSON Resume](GLOSS/J/JSON%20Resume.md)-data with a user-friendly, everbody can do GUI (whereas editing JSON directly we consider even for developers too nerdy, errorprown and painstakingly hard when dealing with longer DVs beyond 50 positions).  

## Next Steps
1. Generate and finalize a reference CV with the [Reactive Resume WebApp](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md), export the data in [JSON Resume Format](GLOSS/J/JSON%20Resume.md) and then decide how to integrate it into the Overall [ApplAI Project/Framework](_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) or wether to engage with the [JSON Resume Open  Source](GLOSS/J/JSON%20Resume.md) and compile the missing stuff from there. 

1. Finalize the [**Specs for** the personal CV related **SourceData**]()  according to [The HR Open Standards Resume/CV Project](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/).


# Appendix

## Standards (solid)
Right from the beginning we want to comply with industry standards such  

* using **Markdown (*.md)** for editable and **PDF** for non-editable documents (from where other formats can be generated when required (such as MS-Office docs databases, Excel Sheets, etcs. )  

* using **JSON** format for anything related to structured data.  

* comply with [The HR Open Standards Resume/CV Project](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/) to provide ATS neutrality (where it makes sense, otherwise deviations will be marked). 

* relay on [JSON Resume](GLOSS/J/JSON%20Resume.md) when it comes to apps,  tools and community to be built around the data.


### Why JSON?
We believe that the strengths of the JSON format makes it a good fit for resumes. It's lightweight, easy to use and it's perfect to build tools for!

We also feel that the JSON Schema is mature enough for writing usable semantics. 


