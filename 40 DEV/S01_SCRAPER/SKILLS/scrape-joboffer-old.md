---
name: scrape-joboffer
description: "Archive an online job offer/vacancy/listing as PDF, Markdown, and a screenshot image, then commit them to the user's jobs GitHub repo. Always opens by asking the user for the job-offer URL, the company name, the job role, and to paste a screenshot of the posting. Trigger on 'Scrape_JobOffer', 'scrape this job offer', or requests to save/archive/convert a job posting."
metadata:
  author: rene.a.baron
  version: '1.0'
---

# Scrape JobOffer

## When to Use This Skill

Use this skill when the user invokes it by name ("Scrape_JobOffer", "run Scrape JobOffer") or asks to save, archive, convert, or turn a job posting/listing/vacancy into files, and has not already supplied all four inputs below in the same message.

## Instructions

1. **Always ask first.** Regardless of what the user's message already contains, open with a single `ask_user_question` call (4 questions, one per input, `free_text_only: true` except the screenshot question) requesting:
   - The job-offer URL.
   - The company name (this becomes `JobName`).
   - The job role as stated in the posting (this becomes `JobRole`).
   - A pasted screenshot of the job-offer page (`allow_attachments: true`). Tell the user the screenshot must be pasted/attached by them — never captured automatically.

   If the user already answered some of these in their triggering message, you may pre-fill those specific questions as already answered and only ask for what's missing — but always still ask for the screenshot unless an image is already attached to the current message.

2. **Sanitize and compose filenames.** Sanitize `JobName` and `JobRole` (keep letters/numbers, replace spaces and other characters with `_`). Compose `<FileName>` as `<JobName>-<JobRole>` (hyphen-joined, each part underscore-sanitized).

3. **Fetch the job offer.** Fetch the URL for the full posting content. If it 404s or looks wrong, try the same URL with any trailing path segment (e.g. `/with`) stripped before giving up — job board links sometimes carry an extra suffix that breaks resolution. If the page is JavaScript-heavy or blocks direct fetching, fall back to a browser-based fetch of the visible job-offer text.

4. **Extract and structure the content.** Pull out: job title, company/organization, location (remote/hybrid/on-site), employment type, salary/compensation, posting date/deadline, role summary, responsibilities, requirements, benefits, contact/how-to-apply, and the source URL. Preserve the full original posting text — do not drop details. Check the user's pasted screenshot for any fields visible there but missing from the fetched text (e.g. salary estimates, contact details) and include them too.

5. **Build the PDF.** Load `office/pdf` and follow it: header with job title + company, a structured summary table from step 4 (omit fields not present), the full posting text with original headings/lists, and a footer with source URL + generation date. Save as `<FileName>.pdf`.

6. **Export Markdown.** Write the same structured fields plus full posting text to `<FileName>.md`, with the source URL.

7. **Save the screenshot.** Save the user-pasted image as `<FileName>.png` (convert to real PNG if it arrived as JPEG).

8. **Determine YYMM.** Use the posting date if available (YY = two-digit year, MM = two-digit month of when the job was posted); otherwise use today's date. Compute this programmatically, never hardcode.

9. **Commit to GitHub.** Target repo defaults to `realB12/jobs` (confirm if the user names a different one). Using `bash` with `api_credentials=["github"]`:
   - Clone/reuse the repo.
   - Create `JOBS/<FileName>-YYMM/` with a `_<FileName>-YYMM.md` containing `# <JobName>: <JobRole> (YYMM)`.
   - Create `JOBS/<FileName>-YYMM/OFFER/` containing `<FileName>.pdf`, `<FileName>.md`, `<FileName>.png`, and a `_JobOffer.md` containing `# <JobName>: JobOffer for <JobRole>`.
   - `git add`, commit as `Add job offer <FileName>`, and push. If push is rejected, pull/rebase and retry once; otherwise report the failure — never force-push.

10. **Deliver.** `share_file` the PDF (and optionally the .md/.png), confirm the GitHub folder path created, then ask the user to sync their local repo (`git pull`).

## Notes & Edge Cases

- Keep the posting in its original language; do not translate unless asked.
- If the URL has multiple listings, ask which one, or default to the primary listing and note this.
- If the page can't be retrieved even via browser fallback, tell the user and ask them to paste the job text directly.
- If `<FileName>.pdf/.md/.png` already exist in the workspace, append a numeric suffix rather than overwriting.
- Never skip step 1's upfront question, even if this looks like a repeat of a prior job-offer request — the screenshot in particular must always be freshly confirmed or requested.
