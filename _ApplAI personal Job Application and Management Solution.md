# ApplAI: a personal, AI automated Job Application & Management Solution for Job-Seekers  

<- [ReadMe](README.md)

* 
---
This documents provides 

> **the Full AppAI Project Outline for Project Workers**

In this sense, this document is the most up to date **Single Point of entry (SPE) document** for **whatever is going on in this ApplAI-PROJECT**, whereas the [ReadMe](README.md) is just the publicly exposed (GitHub) summary describing the final product and therefore might not be aligned to this document!

---

## Current Project STATUS = SPECIFICATIONS

->  **[Current Project STATUS](#project-status) Description** 

-> **[Next Steps](#next-steps)**


## Vision Statement
Automatically **generate a job application resumee and an associated cover-letter** from the job-offer's URL plus the organisational framework (e.g. associated Git Repo) and tasks (e.g "sending the resume") for its efficient follow up and learning from it for next applications.

### Vision realisation
Technically the overall project is broken down into the following components that will be developed in separate projects. 

1. [ApplAI JobScraper](40%20DEV/S01_SCRAPER/_ApplAI_JobScraper.md): creates *.jpeg, *.pdf, *.md and *.json files upon the the job-offer's URL and stores them in a privately owned GitHub-Repo. Those files will serve first as a collection of relevant job offers and when a job gets your attention as input for the following CV and CoverLetter generation. This part is **realized as a Perplexity Agent Prompt** that is just prompted to do so. 

2. [Applai Generator](40%20DEV/S02_GENERATOR/_Applai%20Generator%20DEV.md) compiles a job-offer specific Resumee.md and CoverLetter.md from a given in  MasterResume.json (that contains ALL skills and expertises) and a JobOffer description file with a focus on matching the generated content to what is required by the job offer. The MasterResumee.json is edited and exported with the [Reactive Resume](../../JobSuche/06_TOOLS/R/Reactive%20Resume/_Reactive%20Resume.md) application that is again based on the [JSON Resume](90%20EVAL/JSON%20Resume/JSON%20Resume.md) de facto standard for resumee data.

## The Problem to be solved
1. **No private storage repository to compile from**: We are still today spending **hours typing our resumes over and over again** into (online-)systems we do not control and where we are never sure where our most private data is going to. And even when we could re-use such data  we forget them over the years or have cancelled the membership or lost the crendentials to login abain. 

2. Although LinkedIn or "[HR Open Standards Organisation](GLOSS/H/HR%20Open%20Standards%20Organisation.md) provide extensive standards for how such resume related data should be stored, they are built for the employer side and therefore are too complex for ordinary job seers requirements and currently do not provide frameworks nor tools to to efficiently work with those standards. 

## Project Goals
Provide a local, GitHub-backuped folder with all your resumee relevant data stored in well structured, atomic Markdown files you will never loose and from where you can generate nice human readable resumes and cover letters, as well as data-complete, ATS-standards-compliant artefacts to 

* **Auto-apply for different job roles** by just providing the job-offer's URL

* **generate ATS-optimized AND HR readable appliance documents** in parallel.

* provide **adapters for (AI-) 3rd party tools** to cover language, cultural, industry and role specific HR and job interview requirements.  

* **keep your CV-data private** and share it only with those how need in a way that data-leaks on receiver-side could be tracked back to the receiver (trust is ok, checking is better).  

* **prevent data-loss** upon integrated GitHub-versioning and Backup File-Synchronization 

* Send reminders to motivate ongoing work review, updates and adding new experiences on a monthly bases. 

* **Stability**: The here implied data-**standards must not be changed over time**


### Open Source
the here provided data-schema and tools are and will remain open source and community-driven. We release everything we do under the MIT license.

## Architecture (draft) 
What we currently have in mind is  

1. a **local GUI-App for Windows** (.NET C# in Visual Studio Code + Exensions)  

2. Using the best **"money for performance" AI-services** in the background (which are regularely reviewed for performance, stability, costs and data security and might change or switched to prepared alternatives within a month's notice)
 
3. a minimal **Sales-WebApp** for advertisements, purchasing, downloading and servicing the solution (most probably a vibe-copiloted Single Page Application (SPA) built with Microsoft .NET Tech in VSC Editor) 

4. a **BackendServer** to dispatch job-requests from all local ApplAI-Apps. 

5. Github Repos for project documentation, sourcecode management, templates, user manuals and tutorials, and backend I/O caching till need for speed and scale will require more dedicates solutions.  

## Design Principles
to keep data-structure close to [HR Open's new TCP-standard]() reduced to what we reall need (and therefore not dealing with its full complexity), we will keep the job-data components such as job-experiences, skills etc. in separate files and will therefore work on a more atomic level from where resumes will be dynamically compiled from scratch rather than having ALL data in a single file.

### Initial Scope and Evolutionary Steps
We keep the current architectural scope limted to a local App, english, Windows, Markdown, PDF, "HR Open Standards Resume/CV"-Standard etc. on purpose. However, we are confident than when the first prototype finds acceptance to rollout for different OS, devices, platforms, languages, AI providers, etc. 

### Architectural Stability and Change Requests
However, the goal is NOT to provide a monolythic, customizable everything fits to everyone architecture, but to deliver initially ONE and in the futrue several customized ready made boxed and therefore - concerning architecture - non further customizable-solutions. In this sense, input on architectural design and change is always welcome, but we reserve the right to decide alone, what currently works best for us,  as we do not like to switch/change our own platform upon change requests. 

Scaling of the backend will be done in the background and will remain on our shoulders - technically and financially. 

### YAML over JSON (-> [D002](09%20DECISIONS/000-010/D002_YAML%20over%20JSON.md))
To keep the final CV-Data in YAML format is more consise, easier to read and to edit and finally is less error-prone than JSON when working MANUALLY on it.

Many tools currently are available to translate YAML into JSON and vice versa. 

## Project STATUS

1. Currently the project can **download a job-offer upon the given in URL** and **save it as an (screenshot-)image, PDF and a summary markdown-file in an automatically generated, job-offer specific GitRepo** from where the files and folders are then automatically downloaded to the local machine from where the ApplAI-App was launched. Find [Implementation Details on this ApplAI_SCRAPER called project] -> [_ApplAI JobScraper](40%20DEV/S01_SCRAPER/ApplAI_JobScraper.md)

2. We have investigated the [HR Open Standards Consortium](GLOSS/H/HR%20Open%20Standards%20Organisation.md) provided [TCP-JSON Standard]() and found it useful as a state of the art and future proof reference for our own data standard.   
However we found the "old"  **[JSON Resume](GLOSS/J/JSON%20Resume.md)**-Standard more hands-on, practical and with its established ecosystem (e.g the "[Reactive Resume](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md) ways more readymade, applicable and therefore immediately useful. 

3. We have found the **[Reactive Resume](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md)** Open Source WebApp quite promising  to be used to efficiently create the required [JSON Resume](GLOSS/J/JSON%20Resume.md)-data with a user-friendly, everbody can do GUI (whereas editing JSON directly we consider even for developers too nerdy, errorprown and painstakingly hard when dealing with longer DVs beyond 50 positions).  

4. An alternative Resume-Generator called [resume-ng](https://github.com/bn3t/resume-ng(example on https://github.com/bn3t/resume-ng) I have considered as a valid and pragmatic alternative that generates really nice output. However I do not trust its stability over time, as it seems to be just for personal use for its  developer (no other contributors on the project). 

5. Found YAML format a better than JSON
![Y A M Lvs J S O N](./zPIC/YAMLvsJSON.png): its easier to edit manually, more readable and less error-prone than JSON. Many tools are available to translate YAML into JSON and vice versa. 


## Next Steps
1. **Generate and finalize a reference CV** with the [Reactive Resume WebApp](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md), export the data in [JSON Resume Format](GLOSS/J/JSON%20Resume.md) and then decide how to integrate it into the Overall [ApplAI Project/Framework](_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) or wether to engage with the [JSON Resume Open  Source](GLOSS/J/JSON%20Resume.md) and compile the missing stuff from there. 

2. Finalize the [**Specs for** the personal CV related **SourceData**]()  according to [The HR Open Standards Resume/CV Project](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/).


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

### Why YAML?
Whereas JSON is the de facto standard or WebApps, YAML is easier to read and edit MANUALLY. Wehre we will use JSON for machine2machine conversations, we will use YAML for everything visible and editable to the human eye. 

