## REPORT ON GALAXY TRAINING NETWORK (GTN) SMORGASBORD COURSE.

### OBJECTIVES.
1. To learn skills to comfortably manuever through the galaxy platform.
2. To be able to create and use workflows for scientific data analysis.
3. To learn about various tools and their implementation in the workflows to achieve a desired results.
4. To learn different data visualization techniques.

### INTRODUCTION.
Galaxy is an open, web-based platform foe accesible, reproducible and transparent computational research.
It includes scientific workflows, data and analysis persistence and publishing platform that aims to make computational biology accesible
to research scientists that do not have computer programming or system administration.
Its data intergration supports data uploads from user's computer by URL, and directly from online resources such as UCSC Genome Browser,
InterMine and BioMart supporting a range of widely used biological data formats and translation between those formats.
Galaxy was originally written for biological data analysis, particularly genomics.
The set of available tools have been expanded over the years to cover gene expression, genome assembly, proteomics, epigenomics, 
transcriptomics and other disciplines in life sciences.
Although it was initially developed for genomic research , it is largely domain agonistic and now is used as a 
a general bioinformatics management workflow.
The GTN Smorgasbord Course was aimed to create awarness and give an introductory training to what the Galaxy platform has to offer.

### HOW TO ACCESS THE COURSE.
In order to undertake the course you need to first create an account in one of the three galaxy servers i.e 
[american/main](UseGalaxy.org), [european](UseGalaxy.eu) or [australian](UseGalaxy.org.au) server.
It is recommended you choose an server near you.
I personally recommend the european instance for Kenyans as it is in good proximity and provides a wider range of tools.
Here is a [link](https://shiltemann.github.io/global-galaxy-course/workshop) to redirect you to the course material.
It includes slides, videos and both written and video tutorials.

### MY TAKE-AWAY FROM THE COURSE 

##### Introductory lesson
Galaxy interface has 3 main parts : on the right is your current history, left are the available tools and
in the central panel displays the homepage, tool forms, your analysis results and inspection of data.
Data to start your analysis can be uploaded or gotten from the get data section.
To inspect your data you click on the eye icon and it appears on the central panel.
Galaxy supports many file formats.

The **filter tool** can filter data on columns using simple expressions.
**Intersect tool** looks for intersecting sections between two or more datasets and is useful in getteing overlapping genes.
**Concatenate** is a tool that combines two or more datasets head to tail.
For visualization of BED files IGB, IGV or UCSC main can be used.
The first two are applications hence one has to install while the latter is an online link.

You can create a workflow from your analysis to reuse it in a simliar task.
Workflows capture all the tools and parameter settings needed to perform an analysis.
Its creation is done by **extract workflow** found from your current history.
Unwanted steps can be filtered out and workflow created.
Workflows can be edited or created from scratch using the workflow editor.

##### Quality control
**FastQC** tool provides a simple way to quality control raw sequence data by a modular set of analyses hence giving 
a quick impression of problems in relation to data before further steps.
Generally the quality of the sequences drops at the end of the sequences.
Sequences must be treated to reduce bias in downstream analysis.
Quality treatments include cutting, trimming and masking sequences from low quality score regions, beginning and end of sequence 
and removing adapters.








