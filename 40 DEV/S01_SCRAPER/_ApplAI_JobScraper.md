# Applai Scraper Prompt :: an Applai Subproject

* [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md)

* [Applai-**scraped JobOffers**](../../../../jobs/_Applai-scraped%20JobOffers.md): the folder that contains all JobOffer-files in *.pdf, *.jpeg and *.md format that will serve as input for the subsequent generation of customized job-application CVs and CustomerLetters. 

## Scope
The [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) technically splits into two parts: 

1. **Scraping**: Generating PDF, MD and JSON files from the job offer's URL 

2. **Building**: (Co-piloted) Selection of relevant job-itmes from a [MasterCV]() and compiling the draft job application artefacts in various formats to be then manually edited towards perfection.  

## Functionality
The first part of [the Applai Solution](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) is **scraping the JobOffer's URL into *.pdf, *.md and *.JSON and *.jpeg formatted files** and loading them first into a joboffer specific **["jobs" named GitHub Repo](https://github.com/realB12/jobs)** and the local Drive ("*C:\me\REPO\jobs\JOBS*" in my case). 

Those files will serve first as a collection of relevant job offers and then, when a job gets your attention, secondly as input for CV and CoverLetter generation. 

## Implementation
This part is realized as a Perplexity Agent Prompt that will just be prompted to do so. 






