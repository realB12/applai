# ApplAI: a personal, AI-automated Job-Application & Management Solution for Job-Seekers  

<- [ReadMe](README.md)

* [**generischer Bewerbungs Prozess**](../../JobSuche/60_OPS/5_Bewerben/BewerbungsProzess.md)

---
This documents provides 

> **the Full AppAI Project Outline for Project Workers & Stakeholders**

This document represents the **Single Point of entry (SPE) document** for **whatever is going on in this ApplAI-PROJECT**, whereas the [ReadMe](README.md) is just the publicly exposed (GitHub) summary describing the final product and therefore might not be 100% aligned with this document!

---

## Current Project STATUS = IMPLEMENTATION 60%


->  **[Current Project STATUS](#project-status) Description** 

-> **[Next Steps](#next-steps)**



## Vision Statement
Automatically **generate a job application resumee and an associated cover-letter** from the job-offer's URL plus the organisational framework (e.g. associated Git Repo) and tasks (e.g "sending the resume") for its efficient follow up and learning from it for next applications.

Currently for personal/individual use. With [AutoApply](10%20PRODUCT/AutoApply/_AutoApply.md) offered as a full ServiceInterface in the future.  

## Implementation approach
Although it would have been possible to fully automate the process from giving in the job-Offer URL till sending the such generated application files (Short-CV, Application Letter (for the Recruiter) and the SuperCV for ATS), we keep the following steps as separate Perplexity skills to be manually launched in sequence. This allows partial generation (for cost savings when not going the full circle yet) and manual customization of the final output in between the process. 

Those **process steps** are 

1. [**Scanning**](#1-scanning)
2. [**Scraping**](#2-scraping)
3. [**Composing**](#3-composing)
4. [**Polishing**](#4-polishing)
5. [**Dispatching**](#5-dispatching)

### 1. Scanning
If JobOffers just need to be remembered without being sure yet, whether you are going to apply, collect them in a [**Trello-List** ](https://trello.com/b/STBTePxM/jobs) - which technically is OUTSIDE the Apply-Solution-Context. 

### 2. Scraping
Open a new Perplexity/Computer-Session, insert a Screenshot from the Joboffer, type "**scrape job**" and follow the instructions.   

This archives the JobOffer in .pdf, .md, .JSON and .jpeg format  files in your your remote **["jobs" named GitHub Repo](https://github.com/realB12/jobs)**. 

In a second step you may GitHub-sync it with your local repo on *C:\me\REPO\jobs\JOBS*. 

The goal of this step is to have the original job-offer permanently archived and under your control for future reference for what you have applied. 

These archived files will remind you for pending applications using these files as input for the next composing step.

-> [**JobScraper** Implementation Details](_ApplAI_JobScraper.md) 
  
### 3. Composing
AI generate a draft, customized "Short-CV" and "Cover Letter" from the given in JobOffer-file and the [_Reactive Resume](../../../../JobSuche/06_TOOLS/R/Reactive%20Resume/_Reactive%20Resume.md) generated [SuperCV](../S02_GENERATOR/VSC/data/SuperCV/_SuperCVs.md)

The such generated files are in *.md format for manual editing towards content-wise completion. 

> 1. Open a new **Perplexity-Prompt**
> 2. type "**Scrape JobOffer**"
> 3. **Follow the instructions**
> 5. Finally **Git-sync** your local ["jobs" name JobOffers Repo](../../../../jobs/JOBS/_JobOffers.md) to find the generated files in *.md format for manual editing in your *\JOBS\Company-Role-YYMM\APPLICATION*-folder. 

-> [**Composer Implementation Details** ](40%20DEV/S03_COMPOSER/_ApplAI%20Composer.md)

### 4. Polishing
Generate the final, *.pdf-files from the now (manually) finalized content files together with a standardized Log-File that tracks the interaction with the company

### 5. Dispatching
(Manually) uploading the generated files (Kurz-CV, Cover Letter und SuperCV) to the job application site or via e-Mail. Add the Sending date to the Log and update its Status to "SENT". 

---

## The Problem to be solved

1. **No private storage repository to compile from**: We are still today spending **hours typing our resumes over and over again** into (online-)systems we do not control, and where we are never sure, where our most private data is going to. And even when we could re-use such data, we often forget them over the years in employment or have cancelled the membership or lost the crendentials to login again to the platforms where we have created our last job application files. 

2. Although LinkedIn or "[HR Open Standards Organisation](GLOSS/H/HR%20Open%20Standards%20Organisation.md) provide extensive standards for how such resume-related data should be stored, they are built for the employer side and therefore are too complex for ordinary job seeker requirements and currently do not provide frameworks nor tools to to efficiently work with those standards. 

## Project Goals
Provide a local, GitHub-backuped folder with all your resumee relevant data stored in well structured, atomic Markdown files you will never loose and from where you can generate nice human readable resumes and cover letters, as well as data-complete, ATS-standards-compliant Short-CVs and Cover Letters to 

* **Auto-apply for different job roles** by just providing the job-offer's URL

* **generate ATS-optimized AND Recruiter-readable appliance documents** in parallel.

* provide **adapters for 3rd party (AI-) tools** to cover language, cultural, industry and role specific HR and job interview requirements.  

* **keep your MasterCV-data private** and share it only with those who needs them in a way, that data-leaks on receiver-side could be tracked back to the receiver (trust is ok, checking is better).  

* **prevent data-loss** upon integrated GitHub-versioning and Backup File-Synchronization of such created documents.

* Send reminders to motivate ongoing work reviews, updates and adding new experiences on a monthly bases. 

* **Stability**: The here implied data-**standards must not be changed over time**


### Open Source
the herein provided data-schema and tools are and will remain open source and community-driven. We release everything we do under the MIT license.

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
A first Short-CV, Cover-Letter and SuperCV have been sent to a real job-offerer waiting for feedback with the current tools at hand. 

Currently integration the [ApplAI JobScraper](40%20DEV/S01_SCRAPER/_ApplAI_JobScraper.md) and [ApplAI Composer](40%20DEV/S03_COMPOSER/_ApplAI%20Composer.md) into an all embracing **"APPLICATOR" named Sub-Project** for end2end automation.  

### New business idea: Job-Application Self-Service for Companies
We are currently thinking about a public WebService where experts who are open for work may upload their SuperCV once, so that RECRUITERS and COMPANIES then can give in their JobOffer-URLs to compile the potential candiate's AI-customized job-application documents permissenles by themselves whenever they want. 

Life **example**: On LinkedIn I am sharing a link to my personal Homepage, where a recruiter, who has stumbles over my name, can without my permission nor attention just drops his job-offer's URL and his eMail and within seconds will get my CUSTOMIZED Short-CV and CoverLetter demonstrating best fit or not directly into his inbox. 

So it is no longer the job-seeker looking for companies to apply, but companies self-generating customized job-appliances for persons they just got aware for being potential candidates: upon public contributions in terms of workshops given, podcasts, shared code, excellent social media contributions, articles, projects or ad hoc wherever interesting people are met. 

The key idea behind this is, that for the best match, the probability that a company finds promising candidates upon their currently active real world contributions and impact with much higher precision for a real match, than by waiting for a dream candiate guessing in the wild where to apply and who might never get your (young) company onto his or her radar. 

As a side effect the company might test serveral open positions against the same candiate or might just test their job-offer-content whether it will trigger the "right" response with specific "target" candiates in mind offering this service on their homepage. 

Implementation details include 
1. the possibility to **offer different agents for different roles** (so on my homepage I have an agent for "engineer" and another for "CTO". 
2. Letting me know about the process or not  
3. Fix Payments for every CV generated
etc. 


### GENERATOR stopped
I have put all current App-Development activities on hold. And this stop might be permanent in a sense, that when this project is continued - it **will - most probably - be relaunched from scratch and therefore this project will be "continued" under a different name**.

This stop is a cummulation of reasons: Functional and Technological 

1. The functionality I wanted to build into Applai because I felt, that it was missing, has now been directly built into the [Reactive Resume application](https://rxresu.me/) (Thany you Amruth](https://amruthpillai.com/), for that. So the question that come up from this is, whether it is **better to support Amruth with HIS application rather than building my own** upon his foundation.   

2. One of the main reasons why i have started this project at all, was **getting my feet wet with AI in terms of agentic-AI driven vibecoding the app from scratch** - where the first prompted output has honestly suprised in terms of speed, quality and costs. It was usefull from day. one. Minimalistic on purpose, but useful. However, adding new features and getting the few things right, AI has gotten wrong has become anoying with me working on increasingly longer specs  I was no longer sure, whether they still are suporting vibecoding or is has become more vibcoding confusing with every line I was adding to the specs to make the vibe-code finally doing what I wanted to have. This brought me to the conclusion that for larger project, a monolythic approach might not really be the best approach when when new functionality needs to be added after the first realease and certain functionality does not need to be in full but can mature over next cycles. Further I have never been sure, whether next iterations have impacted code that was already good. And always going through the diffs for an application that is not really yours has become a broing headaque. 

This is the reason why I am currently working on an overall concept for how AI generate component based applications that can evolve from a manually prebuilt secure, best practice, not AI vibecoded, stabe core framework that is built and supported by strong community and then built from there with AI assistance. 


### Was was working when I have left
1. The project can **download a job-offer upon the given in URL** and **save it as an (screenshot-)image, PDF and a summary markdown-file in an automatically generated, job-offer specific GitRepo** from where the files and folders are then automatically downloaded to the local machine from where the ApplAI-App was launched. Find [Implementation Details on this ApplAI_SCRAPER called project] -> [_ApplAI JobScraper](40%20DEV/S01_SCRAPER/ApplAI_JobScraper.md)

2. We have investigated the [HR Open Standards Consortium](GLOSS/H/HR%20Open%20Standards%20Organisation.md) provided [TCP-JSON Standard]() and found it useful as a state of the art and future proof reference for our own data standard.   
However we found the "old"  **[JSON Resume](GLOSS/J/JSON%20Resume.md)**-Standard more hands-on, practical and with its established ecosystem (e.g the "[Reactive Resume](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md) ways more readymade, applicable and therefore immediately useful. 

3. We have found the **[Reactive Resume](../../PRIV/_KEY/Assets/Products/Software/R/Reactive%20Resume%20Credentials.md)** Open Source WebApp quite promising  to be used to efficiently create the required [JSON Resume](GLOSS/J/JSON%20Resume.md)-data with a user-friendly, everbody can do GUI (whereas editing JSON directly we consider even for developers too nerdy, errorprown and painstakingly hard when dealing with longer DVs beyond 50 positions).  

4. An alternative Resume-Generator called [resume-ng](https://github.com/bn3t/resume-ng(example on https://github.com/bn3t/resume-ng) I have considered as a valid and pragmatic alternative that generates really nice output. However **I do not trust its stability** over time, as it seems to be just for personal use for its  developer (no other contributors on the project). 

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

