---
name: job-seeker

description: Find, verify, rank, and curate active senior AI-related roles in the Zug–Lucerne–Obwalden-Zurich region into a dated Markdown job list. Excludes roles older than 30 days and prioritises proximity to Zug, then posting recency.

version: "0.2.0"
author: René Baron
language: en
category: career

keywords:
  - job search
  - job applications  
  - AI
  - LLM
  - generative AI
  - senior roles
  - Switzerland
  - Zug
  - Zurich
  - Lucerne
  - Obwalden

user_profile:
  location: Baar, Switzerland
  target_region: Cantons of Zug, Lucerne, Zurich, Obwalden, Nidwalden
  preferred_radius_from_zug_km: 50
  target_seniority:
    - senior
    - lead
    - architect
    - head
  target_domains:
    - artificial intelligence
    - generative AI
    - large language models
    - RAG
    - AI agents
    - model context protocol
    - AI platform engineering
    - AI governance
    - AI strategy
  non-target_domains: 
    - computer vision
  preferred_work_arrangements:
    - fulltime
    - part-time not less than 60%
  include_exceptional_full_time_roles: true
  core_skills:
    - Project Management
    - Programme Office Management
    - Requirements Engineering
    - Agentic programming
    - Strategic Initiatives
    - CoPilot
    - LLM
    - GIT
    - RAG
    - Prompt and Skill Libraries
    - C#
    - .NET
    - React
    - TypeScript
    - JavaScript
    - PowerShell
    - SQL
    - API integration
    - automation
    - software architecture
    - platform engineering
    - GitHub
    - AI-assisted development
search:
  locations:
    - Zug
    - Baar
    - Cham
    - Rotkreuz
    - Zurich
    - Lucerne
    - Sarnen
    - Staad
  title_keywords:
    - Senior AI Engineer
    - Senior Software Engineer AI
    - Generative AI Engineer
    - AI Platform Engineer
    - AI Architect
    - Head of AI
    - AI Strategy
    - AI Programme Lead
    - AI Project Lead
    - AI Governance
    - AI Consultant
  source_preference:
    - direct employer careers page
    - reputable job board with employer, exact title, location, posting date, and application destination
  require_public_application_url: true
eligibility:
  require_currently_open: true
  exclude_expired_or_closed: true
  maximum_posting_age_days: 99
  require_senior_or_equivalent_level: true
  require_ai_related_role: true
  require_commutable_target_region: true
  deduplicate_by: company and exact job title
  retain_preferred_url: direct employer URL
ranking:
  primary: approximate distance from Zug, nearest first
  secondary: posting date, newest first
  geographic_bands:
    - Zug/Baar/Cham/Rotkreuz
    - Lucerne area
    - Zurich area
    - Obwalden/Nidwalden area

age_calculation:
  method: full calendar days between earliest verified posting date and search date
  if_earliest_date_unavailable: exclude listing
output:
  file_name_pattern: CurrentJobs-YYMMDD.md
  format: markdown
  include_preamble: true
  numbered_list: true
  entry_template: |
    ## 1. **Company name**: **Exact Job Title** (Age)  
    Summary of the responsibilities, relevant technology/domain, seniority signals, work percentage if known, and location; maximum 10 lines.
    [https://example.com/job-offer](https://example.com/job-offer)
quality_checks:
  - Filename matches CurrentJobs-YYMMDD.md
  - Every entry includes company name, exact advertised title, age in days, concise summary, and clickable URL
  - Every role is 99 days old or newer
  - No role is explicitly expired, closed, filled, or archived
  - Ordering is distance first and recency second
  - Each summary is factual, supported, and no more than 10 lines
  - Duplicate listings are removed
  - The direct employer application URL is used where available
final_response:
  include_role_count: true
  report_lucerne_eligibility: true
  cite_research_sources: true
---

# Job Seeker Skill

## Purpose

Find and curate **currently active senior AI-related jobs** in the Zug–Lucerne–Zurich region, prioritising roles within approximately 50 km of Zug. Produce a Markdown file named `CurrentJobs-YYMMDD.md` that is ready for review and job-application workflows.

## User profile

Target candidate:

- Senior AI first, enterprise grade project leader and programme manager (PMO), with a hands-on background as software engineer and application developer based in Baar/Zug, Switzerland.
- Strong hands-on background in C#/.NET, GO, Kubernetes, React, TypeScript, JavaScript, SQL, API integration, automation, software architecture, testing, git, Docker, GitHub, AI-assisted developmentf from vibecoding to agentic engineering of production ready enterprise grade solutions. 
- Interested in AI strategy and implementation, AI programme/project leadership, AI-driven software engineering, agent orchestration, LLM applications, RAG, MCP, AI platform engineering, AI governance, and senior technical consulting.
- Preferred scope: freelance or 80–100% senior roles
- Target geography: Swiss Cantons of Zug, Lucerne, Zurich, Obwalden and Nidwalden; prioritise locations within roughly 50 km of Zug.

## Research process
1. Search the web for currently open senior AI-related roles in Zug, Zurich, Lucerne, Baar, Rotkreuz, Cham, Winterthur, and nearby locations.  

2. Search for titles and variants including:
   - AI Engineer
   - Software Engineer AI
   - Generative AI Engineer
   - AI Platform Engineer
   - AI Architect
   - Head of AI
   - AI Strategy
   - AI Programme Lead
   - AI Project Lead
   - AI Governance
   - AI Consultant
   - AI Trainer
   - AI Process Documentattion
   - AI Requirements
   - AI Analyst
   
3. Prefer direct company careers pages. Use reliable job boards only when they expose a clear employer, exact title, location, application destination, and posting date.

4. Open the individual job page when possible. Do not rely only on search snippets when role details, location, activity status, title, or publication date are uncertain.

5. Include only roles that appear open at the time of research.

6. Exclude any role whose earliest available posting date is more than **30 days** before the search date.

7. Calculate age as full calendar days between the first known publication date and the search date.

8. Do not invent missing facts. If a board does not provide an exact original date, exclude the role unless a trustworthy source can establish it.

9. Do not include roles that are explicitly expired, closed, filled, archived, or otherwise unavailable.

## Relevance criteria
Include a job when all of the following are true:

- It is clearly AI, generative AI, LLM, data/AI platform, AI governance, AI strategy, or AI leadership related.
- It is senior-level, lead-level, staff-level, principal-level, architect-level, head-level, or demonstrably requires substantial professional experience.
- It is located in, or reasonably commutable to Centrals Swiss Cantons Zug, Lucerne, Zurich, Obwalden, Nidwalden.
- It is no more than 30 days old.
- A public job-offer URL is available.

Prioritise roles that leverage the candidate’s C#, .NET, Go, software developement, integration, automation, vibecoding, agentic engineering and technical-leadership strengths.

## Sorting

Sort entries using these keys in order:

1. **Distance from Zug:** nearest first. Use the stated job location; if work is remote, sort according to the listed office/base location.

2. **Actuality:** newest first within the same approximate distance band.

When exact distance is unavailable, use sensible geographic bands, such as Zug/Baar/Cham/Rotkreuz, then Lucerne area, then Zurich area

## Output file

Create exactly one Markdown file named:

```text
CurrentJobs-YYMMDD.md
```

Replace `YYMMDD` with the search date, such as `CurrentJobs-260913.md`.

Start with a short preamble:

```markdown
# Current senior AI roles — Zug / Lucerne / Zurich / Ob- and Nidwalden

Search date: DD Month YYYY  
Sorting: approximate proximity to Zug first; then newest first within each area. Age is calculated from the earliest available posting date. Roles older than 30 days are excluded. Verify the application page before applying.
```

Then provide a numbered Markdown list. Use this exact structure for every role:

```markdown
### + 1. **Company name**: **Exact Job Title** (Age)  
A factual role summary of no more than 10 lines. State the main responsibilities, relevant technologies or domain, essential seniority/experience signals, work percentage if known, and location. Keep it concise and do not add unsupported claims.
[https://example.com/job-offer](https://example.com/job-offer)
```

## Example

```markdown
### + 1. **Grid Dynamics**: **Senior Machine Learning Engineer – LLM Systems** (14)  
Lead end-to-end ML projects involving LLMs, RAG architectures, agents, and AI-safety work. Design evaluation methods, datasets, benchmarks, and metrics; improve model behaviour; and build ML pipelines and evaluation tooling. Requires substantial ML-engineering experience, strong Python and modern ML frameworks, practical LLM experience, and stakeholder communication. Location: Zug; advertised as remote/full-time.
[https://ch.trabajo.org/stellenangebot-4112-991efa40ab06d1d276fe18c9295c2580](https://ch.trabajo.org/stellenangebot-4112-991efa40ab06d1d276fe18c9295c2580)
```

## Quality checks
Before delivering the file, verify:

- The filename follows `CurrentJobs-YYMMDD.md`.
- Every entry has an exact company name, exact advertised title, age in days, summary, and clickable offer URL.
- Every included role is 30 days old or newer.
- No listing is explicitly expired.
- Entries are distance-first, then recency-first.
- Summaries contain no unsupported information and are no more than 10 lines each.
- Duplicate jobs found across multiple boards appear only once; retain the direct employer URL when available.
- The final response briefly states how many roles were included, notes whether Lucerne, Obwalden and Nidwaldenyielded any eligible roles, and cites research sources used.
