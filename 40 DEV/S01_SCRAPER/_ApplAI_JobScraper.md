# Applai_Scraper :: JobScraper Subproject 

* [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md)

## Scope
The [**Overall Applai Solution**](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) technically splits into two parts: 

1. **Scraping**: Generating PDF, MD and JSON files from the job offer's URL 
2. **Building**: Selecting the relevant sections from a MasterCV and compiling the draft job application artefacts in various formas to be manually edited for perfection.  

### Scraping
The first part of [the Applai Solution](../../_ApplAI%20personal%20Job%20Application%20and%20Management%20Solution.md) is **scraping the JobOffer's URL into  PDF, MD and JSON formatted files** and loading them first into a joboffer specific **[jobs GitHub Repo](https://github.com/realB12/jobs)** and from there downloading it to the local C:-Drive ("*C:\me\REPO\jobs\JOBS*" in my case)

so that the following AppSteps (->  can work against those rather than the native job offer URL. 

This part is realized as a Perplexity Agent that is just prompted to do so. 




