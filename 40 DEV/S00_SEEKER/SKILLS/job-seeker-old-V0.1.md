---
name: job-seeker
description: "Give me an actual list of senior AI realted Jobs in the  Zug/LuzernZurich area"

metadata:
  Author: 'rene.a.baron@gmail.com'
  Version: EXPIRED '1.0'
  Creation date: 'September 14th, 2026'
  Platform: 'Perplexity Computer PRO'
  Perplexity skill base: 'perplexity.ai/computer/skills'
  Local path: 'ApplAI\40 DEV\S00_SEEKER\SKILLS\job-seeker.md'
  HowtoRun: '1. Open Perplexity **Computer** 2. Type 'seek jobs'
 
---

# job-seeker 
<span style="color:red; font-weight:bold">EXPIRED VERSION 0.1 </span>:

## What it does
Find and curate **currently active senior AI-related jobs** in the Zug–Lucerne–Zurich region, prioritising roles within approximately 50 km of Zug. Produce a Markdown file named `CurrentJobs-YYMMDD.md` that is ready for review and job-application workflows.

Provide a numbered list of senior AI realted Jobs in the  Zug/LuzernZurich area as a "CurrentJobs-YYMMDD.md"-named Marddown file with entries formatted as follows: 

**Fist line**: 
* **Companyname**: **JobRole-Title** (as given in the Jobdescription)
**[Age]** (amount of days since the job was postet first time)

**Second Line**:
Summary of JobDescription on max. 10 lines. 

**Last Line**: URL of JobOffer

Example Output in *.md format

1. **Klett**: **Head of AI Projects** (11)  
define AI strategy and lead its implementation
https://www.jobs.ch/en/vacancies/detail/646f7135-87ed-4dc0-9b82-d6a132ca58ad/

1. **Klett**: **Head of AI Projects** (11)  
define AI strategy and lead its implementation
https://www.jobs.ch/en/vacancies/detail/646f7135-87ed-4dc0-9b82-d6a132ca58ad/

Sort the list for the following criteria
1. **Distance**: nearest first
2. **Actuality**: most recent offerst first

## When to Use This Skill
Use this skill only when the user types "search jobs"

### Instructions


## Notes & Edge Cases
* **Exlude JobOffers older than 99 days** from the list. 



