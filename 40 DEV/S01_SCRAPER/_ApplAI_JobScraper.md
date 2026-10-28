# Applai Scraper Skill 

**Links**: 

* [**Overall, End2End Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md)

* [**JobOffer Folder**](../../../../jobs/_Applai-scraped%20JobOffers.md): the folder that contains all JobOffer-files in *.pdf, *.jpeg and *.md format that will serve as input for the subsequent generation of customized job-application CVs and CustomerLetters. 

* [Composer](../S03_COMPOSER/_ApplAI%20Composer.md): generating Short-CV and CoverLetter from JobOffer and SuperCV.  

---

> Mit dem Perplexit Scraper Skill **wird eine StellenAnzeige durch die Angabe ihrer URL im .md, .pdf und .jpeg Format ins lokale und remote /JOBS/Company-Role-YYMM/OFFER GitHub Repository kopiert**. 

## How to do it 
1. Open a new **Perplexity-Prompt**
2. **Copy a screenshot** from the JobOffer to the Prompt
3. type "**Scrape JobOffer**"
4. **Follow the instructions**
5. Finally **sync** your local ["jobs" name JobOffers Repo](../../../../jobs/JOBS/_JobOffers.md) to have the job-offer in *.md, *.pdf and *.jpeg format in your [C:\me\REPO\jobs\JOBS\Company-Role-YYMM\OFFER](../../../../jobs/JOBS/_JobOffers.md)-folder

-> These instructions are part of the Overll [JobSuche-Guide](../../../../JobSuche/_JobSuche.md)

## Scope
The [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) technically splits into two parts: 

1. **Scraping**: Generating PDF, MD and JSON files from the job offer's URL into local and remot /JOB Repo. 

2. **Composing**: Compiling AI customized Resume and Cover Letter in readymade *.pdf formats. 

## How it works
Although it would have been possible to fully automate the process from giving in the job-Offer URL till sending the such generated application files (Short-CV, Application Letter (for the Recruiter and the SuperCV for ATS) am still keeping the following steps in separate Skills that are launched individually. 

### 1. Scanning
If JobOffers just need to be remembered without being sure yet, whether you are going to apply, collect them in a [**Trello-List** ](https://trello.com/b/STBTePxM/jobs)

### 2. Scraping
Open a new Perplexity/Computer-Session, insert a Screenshot from the Joboffer, type "scrape job" and follow the instructions.   

This archives the JobOffer in .pdf, .md, .JSON and .jpeg format  files in your your remot **["jobs" named GitHub Repo](https://github.com/realB12/jobs)**. 

In a second step you may GitHub-sync it with your local repo on *C:\me\REPO\jobs\JOBS*. 

The goal of this step is to have the original job-offer archived so that you always will have a reference whatfor you have applied - even when, or in case when the online job-offer is gone. 

These archived files will remind you for appliance and then will erver as input files for the next composing step.

-> [**JobScraper** Implementation Details](_ApplAI_JobScraper.md) 
  
### 3. Composing
AI generate a draft, customized Kurz-CV and Cover Letter from the given in JobOffer-file and the [_Reactive Resume](../../../../JobSuche/06_TOOLS/R/Reactive%20Resume/_Reactive%20Resume.md) generated [SuperCV](../S02_GENERATOR/VSC/data/SuperCV/_SuperCVs.md)

The such generated files are in *.md format for manual editing

### 4. Polish
Generate the final, *.pdf-files from the now final content *.md files together with a standardized Log-File that tracks the interaction with the company

### 5. Dispatching
Uploading the generated files (Kurz-CV, Cover Letter und SuperCV) to the job application site or via e-Mail. Add the Sending date to the Log and update its Status to "SENT". 

## Implementation
This part is realized as a **"job-offer-extraction-to-github" named Perplexity Skill** that will just be prompted to do so. 

-> **[Job Offer Extraction to GitHub" Perplexity Skill](SKILLS/Job%20Offer%20Extraction%20to%20GitHub.md)**

## Usage
Open Perplexity with your Account

**Just type "Scrape_JobOffer"** into a new Perplexity COMPUTER prompt (GitHub File writing requires COMPUTER to know your GitHub Credentials)  

---

> "Save the following job on https://example.com/jobs/12345 with Jobname = HotelPlan and Role = Head of AI Strategy"
→ Fetch the page, extract the offer, produce HotelPlan-Head_of_AI_Strategy.pdf, HotelPlan-Head_of_AI_Strategy.md, and HotelPlan-Head_of_AI_Strategy.png, push them into JOBS/HotelPlan-Head_of_AI_Strategy-2607/OFFER/ in the realB12/jobs repo, share the files, then ask the user to sync their local repo.

---

## Old Prompts
> open https://www.jobs.ch/de/job-empfehlungen/?jobid=646f7135-87ed-4dc0-9b82-d6a132ca58ad
On this page you find a job offer in German
Generate an *.md file that just contains the job offer without menu, advertising etc.





