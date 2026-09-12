# create-polished-cv-pdf

* **name**: create-polished-cv-pdf

* **description**: "Turn a tailored <FileName>-CV.md (from tailor-cv-cover-letter) into a warm, editorial-style 'Kurz CV' named PDF with a monogram, availability banner, and short-CV explanation note, then commit it to the job's GitHub APPLICATION folder. 

Use when the user asks to convert, polish, design, or produce a PDF version of a job-specific CV markdown file, or says things like 'polish job application' or 'make this CV a nice PDF'."

* **metadata:
author: rene.a.baron
version: '2.0'

---

# Create a Polished PDF formatted Job-CV
## When to Use This Skill
Use after a <FileName>-CV.md and <FileName>-Letter.md already exists (typically produced by the tailor-cv-cover-letter skill) and the user wants a designed, recruiter-ready PDF version of it, committed back to the "jobs" named GitHub repo.

## Design direction 
The user explicitly wants this warm, human, and detail-rich, not techy or cold — it should "demonstrate love for style and details." 

The bundled renderer already implements this via:

warm cream/blush palette (terracotta + gold accents, no blue/teal/grey corporate tones), a Playfair Display serif name with an initials monogram badge, italic Lora serif body copy (not a geometric sans), an italic pull-quote treatment for the first sentence of the profile summary, rounded warm "chip" tags for skills instead of gridded tables, and right-aligned accent-colored date columns on experience/education entries. 

Preserve this aesthetic when adjusting the script —
if asked to restyle again, keep it editorial/warm rather than reverting to flat corporate blue/teal.

## Inputs needed
1. The source <FileName>-CV.md file — read it from
JOBS/<FileName>-YYMM/APPLICATION/<FileName>-CV.md
in the jobs repo (default realB12/jobs, confirm if the user names another repo).

If you cannot find the files, stop the process and warn the user!

## Availability date: 
always shown in the header as "Sofort verfügbar ab <date>". Default is the first workday (Mon–Fri) of the month after next, relative to today (e.g. today Sept 7 → Nov 2).

The script computes this automatically; only pass --availability-date "<D>. <Monat> <YYYY>"

explicitly if the user gives a different start date (e.g. one already agreed with an employer).

## Steps
Fetch the <FileName>-CV.md content from GitHub (gh api ... --jq '.content' | base64 -d),
save it locally.

Run the bundled renderer:

bash
python3 skills/create-polished-application-pdfs/scripts/render_cv_pdf.py \
  <local-input.md> "KURZ CV-Rene Baron-<FileName>.pdf" \
  --full-cv-filename "Rene-Baron-CV-Full-Version.pdf"
  
Add --availability-date "2. November 2026" (or the correct date) only when overriding the computed default. 

Fonts (Playfair Display + Lora, multiple weights) are bundled under
assets/fonts/ and registered automatically — no internet font download needed at runtime.

Full ATS compatibility is a nice-to-have, not guaranteed here (chips/tables can confuse some parsers) — mention this tradeoff if asked.

Inspect the rendered PDF page by page before sharing or committing. 

Check specifically for:

Tofu/missing-glyph boxes — only use characters present in Lora/Playfair (plain •, —, –
are safe; avoid exotic Unicode symbols like ◆ ✦ ★ which these fonts don't cover).

Skill chips overflowing the page width, or a chip row barely fitting — the ChipRow flowable wraps automatically at content_width (170mm), but re-check after adding new skill lists.

Entries where the date wasn't pulled into the right-aligned column — split_header_dates() matches a trailing (...) containing a 4-digit year; if a CV uses an unusual date format that doesn't match, extend that regex rather than leaving it inconsistent with other entries.

Awkward page breaks splitting an experience entry's header from its body (the code wraps each entry in KeepTogether, but very long entries can still overflow a page — shorten if needed).

Commit the PDF to 
JOBS/<FileName>-YYMM/APPLICATION/KURZ CV-Rene Baron-<FileName>.pdf 
in the jobs repo via 
gh api --method PUT repos/<owner>/<repo>/contents/<path> with
-f content="$(base64 -w0 <local-pdf>)".
If the file already exists, pass the current sha (fetch via a GET first) so the PUT updates rather than fails. 
URL-encode spaces in the API path (%20) but keep the literal filename (with spaces) as committed — GitHub preserves it.

Also ensure the source <FileName>-CV.md and <FileName>-Letter.md exist in the same APPLICATION/ folder, since APPLICATION/ is the canonical home for all recruiter-facing application documents.

share_file the generated PDF to the user for review.

## Parsing assumptions
```plaintext
The renderer expects the CV markdown structure produced by tailor-cv-cover-letter: 
H1 title,
italic tagline, one contact line, an optional ## Profile/## Profiles link section (folded into
the header monogram/contact block automatically), ## Profil/## Summary, ## Kernkompetenzen/
## Skills (bullets of - **Label**: value, rendered as warm chip tags per category),
## Berufserfahrung/## Ausbildung (repeated ### Company — Role (dates) + italic _location_ +
paragraph, with dates pulled into a right-aligned accent column), and trailing ## Zertifikate/
## Sprachen bullet sections. A generic fallback renders any other ## section as bullets or a
paragraph, so unusual sections degrade gracefully rather than breaking the layout.
```


## Final report to the user
State the output path/filename, the availability date shown, confirm the explanation-note text and
full-CV filename used, and flag any layout adjustments made for that specific CV.