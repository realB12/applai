# Job Application Generation Skill

## When to Use This Skill
Use this skill when the user says something like "generate Job-Application": 

This skill expects just one input:

* The **subfolder-name** such as "KLETT-Projektmitarbeit_operative_KI-Projekte-2608" that must exit in the https://github.com/realB12/jobs/tree/main/JOBS path. 

If the inputs is missing, ask the user for it before proceeding.

If the subfolder cannot be found tell the user so and ask for a different sub-folder name. 

## Instructions
The target repo is the user's jobs repo (default: realB12/jobs, confirm if the user names a different one). All required Files are in /JOBS folder followed by the given in sub-folder name (that again follows the naming convention <FileName>-YYMM, where YYMM is the current year+month (e.g. July 2026 → 2607). 

Create a <FileName> variable by cutting of the -YYMM part of the given in sub-folder name (<Subfolder-Name> = <FileName>-YYMM)

Use the GitHub CLI via bash with api_credentials=["github"]. Do NOT inspect or print credentials.

Get now the <FileName>.md from the JOBS/<FileName>-YYMM/OFFER folder. This files makes the JOB-OFFER. 

Then get /MASTER/SuperCV/supercv.md. This file makes the SUPER-CV. 

When you have both files: 

Reduce the SUPER-CV to 10 Experiences you think that are most relevant for the given in  JOB-OFFER. Reduce the Skills to what is really required for the job. 
Rework the remmaining JOB-OFFER to make it the best possible fit to the JOB-OFFER without halluzinations, overselling nor lying. Keep it short, but still readable by average recruiters and machines. 

Language of the resulting output is German

When done, write what you have into a <FileName>-CV.md file and store it in the same location from where you have read the JOB-OFFER file. 

When done compile a Cover Letter for this job-application and save it as <FileName>-Letter.md in the same location from where you have read the JOB-OFFER file. 



## Notes & Edge Cases
YYMM date format: YY is the two-digit year, MM the two-digit month. Always compute it from the current date programmatically (e.g. date +%y%m), never hardcode.

GitHub push failures: If the push is rejected (e.g. remote ahead), pull/rebase and retry once; if it still fails, report the error to the user rather than force-pushing.


## Examples

### Example 1
User: "generate Job-Application"
→ execute the skill and come back with the suggested <FileName>-CV.md and <FileName>-Letter.md 

