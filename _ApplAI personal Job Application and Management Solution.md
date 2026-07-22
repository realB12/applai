# ApplAI: a personal, AI automated Job Application & Management Solution
<- [ReadMe](README.md)

---
This documents provides 

> **the Full Project Outline**

In this sense this document is the most up to date Single Point of entry (SPE) document for whatever is going on in the Project, whereas the [ReadMe](README.md) is just a summary that might not be aligned on purpose (to keep general communication simplified and stable). 

---

## Vision Statement
Automatically generate a job application from the job-offer's URL and the organisational framework and tasks for its efficient follow up and management. 

## Goals
* **Auto-apply for different roles from a single, locally maintained data-source**.   

* From this source **generate ATS-optimized AND HR readable appliance documents** in parallel.  

* Provide **adapters for (AI-) 3rd party tools** to cover language, cultural, industry and role specific HR and job interview requirements.  

* **Keep your CV-data private** and share it only with those how need in a way that data-leaks on receiver-side could be tracked back to the receiver (trust is ok, checking is better).   

## Standards (solid)
Right from the beginning we want to comply with industry standards such  

* using **Markdown (*.md)** for editable and **PDF** for non-editable documents (from where other formats can be generated when required (such as MS-Office docs databases, Excel Sheets, etcs. )  

* using **JSON** format for anything related to structured data  

* comply with [The HR Open Standards Resume/CV Project](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/) to provide ATS neutrality (where it makes sense, otherwise deviations will be marked). 

## Architecture (draft) 
What we have currently in mind is  

1. a **local GUI-App for Windows** (.NET C# in Visual Studio Code + Exensions)  

2. Using the best **"money for performance" AI-services** in the background (which are reviewed and might change within a month's notice)
 
3. a minimal **Sales-WebApp** for advertisments, purchasing, downloading and servicing the solutionk (most probably a vibe-copiloted Single Page Application (SPA) built with Microsoft .NET Tech in VSC Editor) 

4. a **BackendServer** to dispatch job-requests from all local Apps. 

5. Github Repos for project documentation, sourcecode management, templates, user manuals and tutorials, and backend I/O caching till need for speed and scale will require more dedicates solutions.  

### Initial Scope
We keep the current architectural scope limted to a local App, english, Windows, Markdown, PDF, "HR Open Standards Resume/CV"-Standard etc. on purpose being confident to rollout for different OS, devices, platforms, languages, AI providers, etc. 

### Architectural Stability and Change Requests
However the goal is not to provide a customizable architecture but to deliver ONE or several ready made boxed and therefore - concerning architecture - non further customizable-solutions. In this sense, input on architectural design and change is still welcome but we reserve the right to decide alone what currently works best for us as we do not like to switch/change our own platform upon change requests. 

Scaling will be done in the background and will remain on our shoulders. 

## Current Project Status
Completed a Perplexity Skill that creates a copy and a summary document from a job offer URL. 

## Next Steps (ongoing) 
1. Finalize the [**Specs for** the personal CV related **SourceData**]() to according to [The HR Open Standards Resume/CV Project](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/).




