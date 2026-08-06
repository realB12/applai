# Generic Data Model Requirements

## Single Source Data Format
The Single Source of Resume-relevant data is key, as all resumees, CoverLetters etc. will be generated from this source. Where the generating tools might change, the Datasource does not. It must provide the following characteristica / Requirements: 

* **Keywords must comply with ATS standards**: 
The keywords to be used in SourceFiles must comply with what ATS is normally looking for and therefore should be compliant with the [HR Open Standarts for Resumees](https://learnworkecosystemlibrary.com/initiatives/the-hr-open-standards-resume-cv-project/)    .   

* **Easy to edit:** Every candidate must be able to edit his or her personal data as easy as possible in an easy to handle format in a free accessible form that remains easy, accessible and valid over time and independent from products and services. This is the main reason why we have chosen Markdown (*.md) files to become the file-format to store and manage all personal source data. 

* **Timeless Format and Storage**: You data must be in a format that is still accessible and editiable after decades. With Markdown-files we feel on the save side. Additionally those files are compact, easy to version, backup and easy to convert into other format. 

* **Convertablity**: The raw data needs to be easy to be converted into other fileformat (such as JSON, LJSON, PDF, etc. ) or database formats that will be used to upload them into other CV-Editors, or ATS. We cannot assume (yet) that anybody will build an interface to load our files as is.

* **Compilability**: The raw data needs to be easy be compiled into high-level documents such as resumes etc. When doing so, the compiled artefact should be able to point back to the source of elements it is compiled from. 