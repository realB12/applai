# CV Data Collection
---

* [HR Open Standards Organisation](../../../GLOSS/H/HR%20Open%20Standards%20Organisation.md)

* [JSON Resume](../../../GLOSS/J/JSON%20Resume.md)

---
This folder contains the **DATA Schemas for representing everything [CV](../../01%20ENTITY/C/CV.md) related**. 


>  **it’s silly to worry about formatting when your resume will be parsed into an Applicant Tracking System (ATS) anyway.**

> **There should be a global resume template, and you should be able to transmit it as JSON directly into the ATS.**

## Goals
The goal of this datacollection is to serve a lasting (must not change ofer time) **personal source of work related history data** (experiences, employments, employers, artefacts, evidence, ...) from which human readable, nicely formatted and compressed to the essential resumes and cover letters as well as fully complete, ATS compliant records can be compiled. 

## Standards
Whenever possible the data structure shall comply with Resume JSON de facto Standard for the Job-Seeking side. , but with an **additional evidence-and-targeting layer** that will be required to generate ATS-friendly resumes and tailored cover letters without losing provenance or verification detail. 


### The HR Open Standards -> an overkill for Job-Seekers
**[The HR Open Standards / TCP" concepts](../../../GLOSS/H/HR%20Open%20Standards%20Organisation.md)**, resp. its "HR Open’s LER-RS/TCP standard", however, **is primarely aimed to the employer side** focusing on ATS interoperability. However **for our job-seeking needs [The HR Open Standards / TCP" concepts](../../../GLOSS/H/HR%20Open%20Standards%20Organisation.md) is unnecessarily complex and currently seems to be not that stable and internationally accepted as it should be to fully relay on it**.  

-> https://www.hropenstandards.org/standards-downloads

-> https://viragconsulting.blog/2025/04/02/my-json-resume/

## Design principles
The model should treat a person’s career record as a master profile that can produce many resumee variants, job-specific skill subsets, and narrative outputs, instead of storing only one static CV. 

TCP is explicitly positioned to ber more than a resumee standard and supports portable, structured records containing work roles, competencies, certifications, badges, narratives, and training records.

For ATS compliance, we keep dates, organizations, locations, titles, competencies, credentials, and plain-text narrative blocks as first-class structured objects, while separating verification metadata from display text. 

HR Open’s recent work also stresses composite resume building, narrative inclusion, and open API compatibility, which supports this separation well.




