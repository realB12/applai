

## Job Offer Extraction to GitHub
### When to Use This Skill
Use this skill when the user wants to archive or convert an online job offer into a set of documents. Trigger signals:

* The user provides a URL to a job offer / job posting / vacancy / listing and a name to file it under.
* The user says something like "save this job", "convert this job", "archive this vacancy under <JobName>-<JobRole>".

The three inputs this skill expects:

* URL — the link to the job offer.

* JobName — the name of the company offering this job.

* JobRole — the role/name of the job as mentioned in the joboffer
This becomes part of the output filenames: <JobName>-<JobRole>.* and the output foldername in the Repo.

If any of these three inputs is missing, ask the user for it before proceeding.

### Instructions
Collect inputs. Confirm you have the job-offer URL, the JobName and the JobRole. Sanitize JobName and JobRole into safe filename parts (keep letters and numbers but replace spaces and other characters with _). Compose the <FileName> variable as <JobName>-<JobRole> (each part sanitized with _, joined by a single hyphen -). All subsequent references to <RoleName> mean this sanitized <JobRole>.

Fetch the job offer. Use fetch_url on the provided URL to retrieve the full posting content. If the page is JavaScript-heavy or blocks direct fetching (empty/partial content, login wall, cookie banner), fall back to browser_task to load the page and extract the visible job-offer text.

Extract and structure the content. From the fetched content, pull out:

Job title

Company / organization

Location (and remote/hybrid/on-site)

Employment type (full-time, part-time, contract, etc.)

Salary / compensation (if listed)

Posting date / application deadline (if listed)

Short role summary

Key responsibilities

Requirements / qualifications

Benefits (if listed)

How to apply / application link

The source URL

Preserve the full original posting text as well — do not drop details.

Build the document. Load the office/pdf skill (load_skill(name="office/pdf")) and follow it to generate a clean, professional PDF. The document layout:

Header: Job title and company as the document title.

Summary section: A structured overview using the fields extracted in step 3 (present as a labeled list or table). Omit fields that were not present in the posting rather than showing "N/A" everywhere.

Full posting section: The complete original job-offer text, preserving headings and lists.

Footer/metadata line: Source URL and the date the PDF was generated.

Save the PDF with the correct filename. Write the PDF to the workspace as <FileName>.pdf (using the sanitized FileName that compiles as <JobName>-<JobRole>).

Export a Markdown file. Write all key data extracted in step 3 to <FileName>.md in the workspace. Use clear Markdown headings and a labeled list/table for the structured fields, followed by the full posting text. Include the source URL.

Use the user-provided screenshot. The user takes the screenshot of the job offer manually — do NOT capture it automatically (never use pplx-tool screenshot_page or browser_task for this).

Assume the job-offer picture is the image attached to the current prompt, or, if none is attached, the most recently provided/prompted image in the conversation.

Save/rename that image to <FileName>.png in the workspace.

If you are not sure which image is the job offer (no image attached to this prompt, ambiguous, or the last image may be unrelated), ask the user to either provide a new picture or confirm that the last one is the correct job-offer screenshot. Do not proceed until confirmed.

Commit the files to the GitHub repo. The target repo is the user's jobs repo (default: realB12/jobs, confirm if the user names a different one). Files go into a new folder under /JOBS following the naming convention <FileName>-YYMM, where YYMM is the current year+month (e.g. July 2026 → 2607). Compute YYMM programmatically — never guess the date.

Use the GitHub CLI via bash with api_credentials=["github"]. Do NOT inspect or print credentials.

Clone (or reuse) the repo, e.g. git clone https://github.com/realB12/jobs.git into the workspace.

Create the folder JOBS/<FileName>-YYMM/ inside the repo.

At the parent level (JOBS/<FileName>-YYMM/), create a _<FileName>-YYMM.md file with the following content: # <JobName>: <RoleName> (YYMM)

Create the subfolder OFFER inside JOBS/<FileName>-YYMM/.

Copy <FileName>.pdf, <FileName>.md, and <FileName>.png into JOBS/<FileName>-YYMM/OFFER/.

Inside JOBS/<FileName>-YYMM/OFFER/, create a _JobOffer.md file with the following content: # <JobName>: JobOffer for <RoleName>

git add, git commit -m "Add job offer <FileName>", and git push to the remote.

Resulting folder tree:

text
JOBS/<FileName>-YYMM/
├── _<FileName>-YYMM.md
└── OFFER/
    ├── <FileName>.pdf
    ├── <FileName>.md
    ├── <FileName>.png
    └── _JobOffer.md
Deliver. Use share_file to send the PDF (and optionally the .md and .png) to the user, with name set to a human-readable title. Confirm the generated files (<FileName>.pdf, <FileName>.md, <FileName>.png, plus the _<FileName>-YYMM.md and _JobOffer.md markers) and the GitHub folder path (JOBS/<FileName>-YYMM/OFFER/) that were created.

Prompt to sync. After the push succeeds, ask the user to synchronize their remote repo with their local repo (e.g. git pull) so they can inspect the generated output on their local workstation.

Notes & Edge Cases
Non-English postings: Keep the job offer in its original language. Do not translate unless the user asks.

Multiple offers on one page: If the URL contains several listings, ask the user which one, or default to the primary/first offer and note this.

Paywalled or login-required pages: If content cannot be retrieved even via browser_task, tell the user and ask them to paste the job text directly.

Filename collisions: If <FileName>.pdf/.md/.png already exist in the workspace, append a numeric suffix rather than overwriting silently.

YYMM date format: YY is the two-digit year, MM the two-digit month. Always compute it from the current date programmatically (e.g. date +%y%m), never hardcode.

GitHub push failures: If the push is rejected (e.g. remote ahead), pull/rebase and retry once; if it still fails, report the error to the user rather than force-pushing.

Screenshot source: Screenshots are always provided by the user, never captured automatically. If no suitable image is available, ask the user to supply one before continuing; do not attempt to generate or capture it.

### Examples

#### Example 1
User: "Save the following job on https://example.com/jobs/12345 with Jobname = HotelPlan and Role = Head of AI Strategy"
→ Fetch the page, extract the offer, produce HotelPlan-Head_of_AI_Strategy.pdf, HotelPlan-Head_of_AI_Strategy.md, and HotelPlan-Head_of_AI_Strategy.png, push them into JOBS/HotelPlan-Head_of_AI_Strategy-2607/OFFER/ in the realB12/jobs repo, share the files, then ask the user to sync their local repo.

#### Example 2
User: "Save this posting from Hotelplan named Head of AI Strategy" (with a URL, in July 2026)
→ Same flow; files land in JOBS/HotelPlan-Head_of_AI_Strategy-2607/OFFER/ and the user is prompted to git pull.


