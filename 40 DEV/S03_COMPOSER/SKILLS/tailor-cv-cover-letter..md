# tailor-cv-cover-letter

## What it does
**Reads the job offer** from my realB12/jobs GitHub Repo as /JOBS/<FileName>-YYMM/OFFER/<FileName>.md **and the SuperCV** form /MASTER/SuperCV/supercv.md).

It will asks for a <WORK-START> date before drafting, defaulting to the first workday of the month after next (e.g. today Sept 7 → Nov 2), with your answer worked into both the CV and the cover letter's closing.

Reduces the SuperCV to the 10 most relevant experiences and trims skills to what the offer actually needs, reworking content honestly (no hallucination/overselling/underselling, including flagging seniority or qualification mismatches).

Outputs German-language <FileName>-CV.md and <FileName>-Letter.md into a new JOBS/<FileName>-YYMM/APPLICATION/ folder — a sibling of the /OFFER folder.

Reports back which SuperCV location was used and the work-start date applied.

----

# The "tailor-cv-cover-letter" Skill

## Description
* **Title**: Tailor CV & Cover Letter from Job Offer

* **Name**: tailor-cv-cover-letter

* **Dscription**: "**Generate a job-specific CV and cover letter (in German) from a saved job offer and the user's master CV in their GitHub jobs repo**, then commit both files. 

Use when the user asks to tailor, adapt, rework, or write a CV/Lebenslauf and Motivationsschreiben/cover letter for a specific job offer already archived in their jobs repo, or references a JOBS/<FileName>-YYMM folder. 

Not for initially archiving a job posting (use job-offer-extraction-to-github or scrape-joboffer for that)."

### metadata:
**author**: rene.a.baron
**version**: '1.0'

## When to Use This Skill
Use when the user wants a job-specific CV and cover letter built from an already-archived job offer in their jobs GitHub repo (default realB12/jobs, confirm if the user names a different repo) plus their master CV ("SuperCV"). 

## Trigger phrases: 
1. "create a CV for this job offer", 
2. "tailor my CV/cover letter for <company>", 
3. "compile a cover letter for this application", 
4. a reference to a JOBS/<FileName>-YYMM folder that already has an OFFER subfolder.

## Setup
Use the GitHub CLI via bash with api_credentials=["github"]. Never inspect or print credentials.

<Subfolder-Name> = <FileName>-YYMM (YYMM = current year+month, e.g. July 2026 → 2607).
<FileName> = <Subfolder-Name> with the trailing -YYMM cut off.

If the user did not name a specific <Subfolder-Name>, list JOBS/ in the target repo
(gh api repos/<owner>/<repo>/contents/JOBS) and ask the user which folder to process via ask_user_question — do not guess.

Job offer source: JOBS/<Subfolder-Name>/OFFER/<FileName>.md in the jobs repo. Read it with gh api repos/<owner>/<repo>/contents/<path> --jq '.content' | base64 -d.

Master CV ("SuperCV") source: try MASTER/SuperCV/supercv.md in the jobs repo first. If that 404s, it may live in a different personal repo (e.g. realB12/ApplAi_Generator). Locate it with gh api -X GET "search/code?q=filename:supercv.md+user:<owner>" and read it from wherever it is
found. Tell the user in your final summary which repo/path the SuperCV actually came from if it wasn't the default location.

## Ask for the work-start date
Before drafting, ask the user for <WORK-START> — the date they could start the job — via ask_user_question. Default to the first workday (Mon–Fri) of the month after next, relative to today, and offer it as one option plus a free-text alternative. Example: today = Sept 7 → month after next = November → default <WORK-START> = Nov 2 (first workday of November). Compute this with Python (bash) rather than by hand. Mention <WORK-START> naturally in both the CV (e.g. as
availability near the contact/summary section) and the cover letter's closing paragraphs.

## Build the CV and cover letter
Reduce the SuperCV to the 10 experience entries most relevant to the job offer's actual requirements — pull from "Experience" and, if a better fit exists, "Projects". Do not just take the 10 most recent; rank by topical relevance to the offer's tasks/profile section.

Reduce the Skills section to what the offer genuinely asks for; drop unrelated tooling/domains.

Rewrite the remaining content to fit the offer as closely as possible without hallucinating, overselling, or lying. If there's a seniority or qualification mismatch between the SuperCV and the offer (e.g. a senior/executive background applying to a junior role, or an unfinished degree where the offer wants a completed one), state it honestly in the profile summary and cover letter — explain genuine motivation for the step rather than concealing or inflating it.

Output language: German, unless the user explicitly requests another language.

Keep both documents short and readable for both human recruiters and ATS parsing — concise bullet-style entries over long paragraphs.

Include a source citation line at the bottom of the CV linking back to the original job posting URL (from the offer file's "Quelle"/source line).

## Output location (differs from archiving skills)
Save the two generated files as <FileName>-CV.md and <FileName>-Letter.md into a new
JOBS/<Subfolder-Name>/APPLICATION/ folder — a sibling of OFFER/, not inside it. 

Create this folder implicitly by committing files into that path (GitHub creates folders on first file commit, no separate mkdir step needed).

Commit both files with gh api --method PUT repos/<owner>/<repo>/contents/<path> using
-f message="..." and -f content="$(base64 -w0 <local-file>)". Use one commit per file (as separate PUT calls; the second will chain onto the first commit automatically).

## Cover letter structure
Address it using the contact named in the job offer (e.g. a named recruiter/agency contact) when present, otherwise the hiring company. Include: sender block (name, address, email, phone), date, subject line naming the role and company, salutation, 3–4 short paragraphs (interest/fit, concrete relevant experience highlights, honest positioning if there's a mismatch, availability referencing <WORK-START> and closing), signature, and the source-posting URL at the bottom.

## Final report to the user
Share both files. Note explicitly: the repo/path actually used for the SuperCV if it deviated from the default, the <WORK-START> date used, and a one-line summary of how the CV/skills were narrowed down and why (including any honest mismatch framing applied).