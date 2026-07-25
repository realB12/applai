# JSON Resume Ecosystem

* [HompePage](https://jsonresume.org/)
* [on GitHub](https://github.com/jsonresume/jsonresume.org)

* [Documentation](https://jsonresume.org/docs)

* [Schema](https://github.com/jsonresume/resume-schema)

* [CLI](https://github.com/jsonresume/resume-cli)

* [HR Open Standards Organisation](../H/HR%20Open%20Standards%20Organisation.md)

* [BLOG](https://jsonresume.org/blog)

---

JSON Resume is an open-source initiative to create a standard, JSON-based schema for resumes. Write your resume once as JSON, then render it with any of hundreds of community themes, host it for free, and export it to HTML, PDF, and more — no lock-in, no proprietary formats.

However, the project seems to be abondend in 2019

With JSON Resume, you can:

* Create a portable, machine-readable resume
* Publish your resume online with a unique URL via the registry
* Render your resume with dozens of community-built themes
* Validate your resume against the JSON Resume schema
* Leverage AI-powered tools to help with your job search

However, it is primarely built for developers who are easy with putting their data into JSON files and compiling from the command line (GUIs are still waiting to be implemented by somebody some day).   

In addition to the JSON schema, the ecosystem includes:

* Themes
* Hosting 
* Tooling
* Command Line Interface (CLI)
* Export utilities
* Chrome extension
* Latex rendering
* Multiple “theme” formatters
* Hosted registry
* YAML, TXT, and QR Codes

In essence you are **hosting your own resume.json file on a GitHub GIST Repo as the single source of truth**, from where the JSON Resume Framework provides serveral tools to generate resume artefacts. 

I can generate it as a PDF in one of the thousand available themes. I used the included editor to develop this resume, which it automatically publishes as a Gist on my GitHub.

JSON Resume also hosts a registry. That is, it automatically generates a web page based on the JSON file. I didn’t have to lift a finger. Here is my resume online. Other great things are in prospect, like vectorizing resumes and using cosine similarity to match them with job listings.

The tools are user-friendly enough, and I’d love to see more people in the registry, but right now it seems to be mostly just developers.