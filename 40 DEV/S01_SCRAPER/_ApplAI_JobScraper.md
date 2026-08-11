# ApplAI :: JobScraper Subproject 

## Scope
The Overall Applai-solution technically splits into two parts: 

1. Scraping and 
2. Building

### Scraping
The first part of the ApplAI solution is **scraping the JobOffer's URL into  PDF, MD and JSON formatted files** and loading them first into a joboffer specific **[jobs GitHub Repo](https://github.com/realB12/jobs)** and from there downloading it to the local C:-Drive ("*C:\me\REPO\jobs\JOBS*" in my case)

so that the following AppSteps (->  can work against those rather than the native job offer URL. 

This part is realized as a Perplexity Agent that is just prompted to do so. 




