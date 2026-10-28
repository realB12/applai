---
name: job-scraper
description: "Archive an online job offer as PDF, Markdown, and a screenshot image into the user's jobs-named GitHub repo. Always opens by asking the user for the job-offer URL, the company name, the job role, and to paste a screenshot of the posting. Trigger on 'scrape joboffer'"
metadata:
  Author: 'rene.a.baron@gmail.com'
  Version: '2.0'
  Creation date: 'September 13th, 2026'
  Platform: 'Perplexity Computer PRO'
  Perplexity skill base: 'perplexity.ai/computer/skills'
  Local path: 'ApplAI\40 DEV\S01_SCRAPER\SKILLS\job-scraper.md'
  HowtoRun: '1. Open Perplexity **Computer** 2. **paste a screenshot** of the job-offer into the prompt. 3. Then type scrape joboffer'
---

# job-scraper (personal Perplexity Skill)

## What it does
It immediately asks you (rather than assuming from context) for 

1. the **joboffer's URL** (you copy/paste from your browser), 

2. the **company name** that shall be used for the scraped files' name but not for content, 

3. the **job role** for naming the scraped files

4. When no Screenshot is recognized you will be asked to insert it. 

The scraping will only continue when all 4 input-pieces are complete.

It then scraped the content of the such recognized joboffer at the given in URL and saves it in *.md and *.pdf-format together with the provided Screenshot into a new created folder in the realB12/jobs GitHub Repo as follows: 
then runs the same fetch → PDF/Markdown/screenshot build → GitHub commit workflow into realB12/jobs that we just used, 

The process includes a 404-with-trailing-suffix fallback solution to cover pages that can only be reached when logged in. 

### Output
The Skill will create the following folders and files on https://github.com/realB12/jobs: 

```plaintext
jobs/
└── JOBS/
   └── COMPANY-ROLE-YYMM/
        ├── OFFER/
        │   ├── _JobOffer.md
        │   ├── COMPANY-ROLE-YYMM.md
        │   ├── COMPANY-ROLE-YYMM.pdf
        │   └── COMPANY-ROLE-YYMM.png
        └── _COMPANY-ROLE-YYMM-LOG.md
```

## When to Use This Skill
Use this skill only when the user types "scrape joboffer" after having posted an screenshot/image of the JobOffer to be scaped into the below defined GitHub hosted files. 

### Instructions
Always ask first. Regardless of what the user's message already contains, open with a single ask_user_question call (4 questions, one per input, free_text_only: true except the screenshot question) requesting:

1. The **job-offer URL**: referred to as <URL> when creating filenames

2. The **company name**: referred to as <COMPANY> when creating file-names

3. The **job role**: referred to as <ROLE> when creating file-names

4. When not already given in just before the "scrape joboffer" command was inserted: A pasted **screenshot** of the job-offer page (allow_attachments: true). Tell the user the screenshot must be pasted/attached by them — never captured automatically.

Determine <YYMM>. Use the posting date if available (YY = two-digit year, MM = two-digit month of when the job was posted); otherwise use today's date. Compute this programmatically, never hardcode.

If the user already answered some of these in their triggering message, you may pre-fill those specific questions as already answered and only ask for what's missing — but always still ask for the screenshot unless an image is already attached to the current message.

Sanitize and compose filenames. Sanitize <COMPANY> and <ROLE> (keep letters/numbers, replace spaces and other characters with _). Compose <FileName> as <COMPANY>-<ROLE>-<YYMM> (hyphen-joined, each part underscore-sanitized), where YYMM = Current Year and Month like for instance "2608" for August 2026. 

Fetch the job offer. Fetch the URL for the full posting content. If it 404s or looks wrong, try the same URL with any trailing path segment (e.g. /with) stripped before giving up — job board links sometimes carry an extra suffix that breaks resolution. If the page is JavaScript-heavy or blocks direct fetching, fall back to a browser-based fetch of the visible job-offer text.

Extract and structure the content. Pull out: job title, company/organization, location (remote/hybrid/on-site), employment type, salary/compensation, posting date/deadline, role summary, responsibilities, requirements, benefits, contact/how-to-apply, and the source URL. 

Preserve the full original posting text — do not drop details. Check the user's pasted screenshot for any fields visible there but missing from the fetched text (e.g. salary estimates, contact details) and include them too.

Build the PDF. Load office/pdf and follow it: header with job title + company as extraced from the JobOffer, a structured summary table from step 4 (omit fields not present), the full posting text with original headings/lists, and a footer with source URL + generation date. Save as <FileName>.pdf.

Export Markdown. Write the same structured fields plus full posting text to <FileName>.md, with the source URL.

Save the screenshot. Save the user-pasted image as <FileName>.png (convert to real PNG if it arrived as JPEG).

Commit to GitHub. Target repo defaults to realB12/jobs (confirm if the user names a different one). Using bash with api_credentials=["github"]:

Clone/reuse the repo.

Create JOBS/<FileName> Folder

Copy MASTER/COMPANY-ROLE-YYMM/COMPANY-ROLE-YYMM-LOG.md to this new created JOBS/<FileName> folder and rename the file as _<FileName>-LOG.md

Create JOBS/<FileName>/OFFER/ folder containing <FileName>.pdf, <FileName>.md, <FileName>.png. 

Then copy MASTER\COMPANY-ROLE-YYMM\OFFER\_JobOffer.md to the JOBS/<FileName>/OFFER/ folder

git add, commit as Add job offer <FileName>, and push. If push is rejected, force-push.

Deliver. share_file the PDF, the .md and .png, confirm the GitHub folder path created, then ask the user to sync their local repo (git pull).

## Notes & Edge Cases
Keep the posting in its original language; do not translate unless asked.

If the URL has multiple listings take the one that is demontraded by the given in picture. When still nor sure, ask which one or default to the primary listing.

If the page can't be retrieved even via browser fallback, tell the user and ask them to paste the job text directly.

If <FileName>.pdf/.md/.png already exist in the workspace, overwrite.

Never skip step 1's upfront question, even if this looks like a repeat of a prior job-offer request — the screenshot in particular must always be freshly confirmed or requested.
