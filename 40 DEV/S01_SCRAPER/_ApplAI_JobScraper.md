# Applai Scraper Prompt :: an Applai Subproject

* [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md)

* [Applai-**scraped JobOffers**](../../../../jobs/_Applai-scraped%20JobOffers.md): the folder that contains all JobOffer-files in *.pdf, *.jpeg and *.md format that will serve as input for the subsequent generation of customized job-application CVs and CustomerLetters. 


## Summary
1. Open a new Perplexity-Prompt
1. Add a screenshot from the JobOffer
2. type "Scrape_JobOffer"
4. Follow the instructions
5. When done, sync your local ["jobs" name JobOffers Repo](../../../../jobs/JOBS/_JobOffers.md)
6. When done you should have the job-offer in *.md, *.pdf and *.jpeg format in your [C:\me\REPO\jobs\JOBS](../../../../jobs/JOBS/_JobOffers.md)-folder

## Scope
The [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) technically splits into two parts: 

1. **Scraping**: Generating PDF, MD and JSON files from the job offer's URL 

2. **Building**: (Co-piloted) Selection of relevant job-itmes from a [MasterCV]() and compiling the draft job application artefacts in various formats to be then manually edited towards perfection.  

## Functionality
The first part of [the Applai Solution](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) is **scraping the JobOffer's URL into *.pdf, *.md and *.JSON and *.jpeg formatted files** and loading them first into a joboffer specific **["jobs" named GitHub Repo](https://github.com/realB12/jobs)** and the local Drive ("*C:\me\REPO\jobs\JOBS*" in my case). 

Those files will serve first as a collection of relevant job offers and then, when a job gets your attention, secondly as input for CV and CoverLetter generation. 

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





