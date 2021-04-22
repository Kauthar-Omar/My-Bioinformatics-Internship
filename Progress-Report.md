## REPORT ON INTERNSHIP PROGRESS SO FAR.

### INTRODUCTION

At the beginning of this internship I outlined a [roadmap](https://github.com/Kauthar-Omar/My-Bioinformatics-Internship/blob/main/Roadmap.md) on
accesssment of my progress during the duration of my internship.
Being more than halfway through the internship they are achievements made, updates on goals to be achieved and interest developed as a result of the
exposure gained during the stay.
This report is an update of my progress in the duration of my stay.
A real time summary of my progress is available on github on my internship repository under [projects](https://github.com/Kauthar-Omar/My-Bioinformatics-Internship/projects/1)

### PROGRESS UPDATE

The following were the skills I planned to have learnt and progress made in each individual one so far:

#### 1. Linux

I can now comfortably navigate through the command line using skills learnt from introduction to linux undertaken in week1.
These skills include: commands that help in navigating through, creating, copying and deleting files and directories,pipes and filters, loops, pattern matching (grep,find) and file permissions.
Aditionally I undertook an online course in bash scripting to build on my bash skills.
This course built on my skills learnt in week 1 and introduced new skills such as: symlinks, substitutions using sed, file processing using awk and enviromental variables.
I also discovered some linux shortcuts through the course.
In terms of practise I often find myself using bash scripting on the command line hence putting my skills to practise and continously discovery new usages of learnt commands to
accomplish tasks.
I have however found myself biased to using loops in python rather than bash, seldomly using commands awk and hardly using symlinks and enviromental variables.

#### 2. Python Programming

Having some prior knowledge in python the introductory lesson was a reminder, practise on usage and learning of new commands experience.
As opposed to my norm of coding using pycharm I was introduced to jupyter notebooks and got quite accustomed to notebooks.
The topics covered included: basic data types and operations, string manipulation, lists, tuples, dictionaries, loops/control statements, functions, file
handling,scripting and modules.
Additional material on visualizations and biopython was provided in notebooks and carpentries to follow through in order to advance our coding skills in python.
I built up on my plotting knowledge by introducing myself to plotnine through the carpentries and discovering how to get plots with good aesthetics as in R
using python.
Discoverying the use of regular expressions in manipulating genomic data I embarked on learning the module and practizing it through exercises.
I noticed object oriented programming put into use while following end to end analysis using qiime in making of a manifest file and rose my curiosity of how
else it is utilized in genomic data analysis and improving my understanding of it.
I also embarked on a journey of learning biopython having dedicated a week to purely learning its usage,practising and finding replacements for obselete commands.
Biopython being a broad topic, I tested myself on the skill set covered and am looking forward to continue learning the tool set progressively.
In python I experienced challenges in understanding lamda, writing modules and differentiating them with stand alone scripts.

#### 3. R
I successfully followed through and completed and introductory short course to R where basic fundamentals of R programming were learnt.
This included creating and manipulating variables,vectors, lists and dataframes in R, reading data from files in R, querying and manipulating data from files
using dedicated packages in R.
Additionally plotting and achieving plots of good aesthetics using ggplot2 was introduced.
My learnt skill were put into practise when collaboratively working on the Dada2 pipeline in the 16S accreditation process and also building of my R skill set during testing and debugging of the pipeline.

#### 4. Reproducibility in bioinformatic tools and workflows.
* Documentation tools - Notebooks
  - Jupyter notebooks

  I often find myself using jupyter notebooks especially when coding in python hence putting this documentation technique to use.

  - R markdown

  Looking foward to implementing this technique on a MiSeq data Dada2 pipeline I developed.

* Version control tools
  - Git and Github

I continously continue to learn more about git and github with every interaction with the platform depending on the tailored need of the nature of the task.
I encourage myself to push and pull my files and codes instead of making direct inputs on github.
I recently started using git on the commandline as opposed to my prior practise of directly making inputs from github and the experience is progressing well.

* Software tools i.e managers and containers

I am yet to venture into the functionality of containerization and would like to start with either docker or singularity depending on the task requirements.

#### 5. Hpc and cloud computing.
The hpc was introduced in 2 lectures starting with the basic commands used in navigating through it loading and using different modules on the platform
The accreditation process embarked shortly after its introduction hence leading to its frequent use both from the commandline and Rstudio giving me good
practise.
I continously use it in running my analysis pipelines due to speed hence being time efficient.
Additionally I have started learning some job scheduling commands on slurm to check on my jobs and other jobs on the hpc when running an assembly pipeline.
I am looking forward to build on slurm job scheduling and be proficient in it.

#### 6.Introduction to selected concepts in Bioinformatics.
The selected concepts include:
- Biological databases.

This covered the types/categories of databases, sequence formats available in the databases and how to access and how to navigate through the selected databases.

- Sequencing Technologies

The evolution of sequencing technologies over time was covered and overview of their working principals of some of the technologies.
These concepts were numerous hence need to be revisited for a comprehensive understanding.

- Alignment

The different concepts of sequence alignment covered were mainly in reference with next-generation sequencing(ngs).
These included types of alignment, primary approaches to alignment, aligners i.e the tools, alignment outputs, alignment viewers and workflows.
This concept has had a great contribution to the de novo assembly pipeline currently working on as is the working background of the pipeline.

- Phylogenetics

This included the terms used in phylogenetics, concepts associated with phylogenetic trees and dna for taxonomy i.e some concepts of moleculer phylogenetics.
I am not yet well conversant with tree building methods and algorithms associated with the methods.

#### 7. Understanding and development of genomic pipelines and workflows
My first pipeline to explore was Dada 2 pipeline using MiSeq data with the official Dada 2 tutorial as a guide.
I also undertook a snakemake workflow tutorial which I run on cloud via Gitpod.
I was however not able to complete the analysis pipeline implemented in snakemake but look forward to revisting it.
Basic nextflow scripting was introduced and nextflow being workflow language of choice in the 16s accreditation process.
Material for self paced learning was availed to build on the introductory lesson and I got a chance to practise my nextflow skill set by assisting in the
merging step of the qiime pipeline and converting it into a nextflow script where I experienced challenges in conversion to a nextflow script but
with assistance pulled through.
I however find it necessary to continue learning and practising nextflow in order to be conversant with it and address challenges I experience while using it.
Moreover I also collaboratively worked on the Dada 2 pipeline for the 16s accreditation process building on the skills I acquires while following
through the Dada2 tutorial mentioned above and learning.
I am currently working on denovo assembly pipeline available [here](https://github.com/Kauthar-Omar/De_novo_assembly.git).
I am excited to explore more pipelines and possibly implement them in a workflow language as part of the miniproject I will undertake.

#### 8. Galaxy.
I participated in the  GTN Smörgåsbord: A Global Galaxy Training Event with the aim of learning how to use the galaxy platform for my future bioinformatics needs.
The GTN training was very insightful and various skills on maneuvering through galaxy, creating workflows from history, using various bioinformatics tools, accessing available workflows from shared data and troubleshooting errors experienced.
An introduction to different bioinformatics workflows was covered.
I encountered challenges in understanding Single-cell RNA-Seq Analysis.
In general it was a good self teaching experience and the beggining to expand knowledge on galaxy.
A detailed encounter of skills learnt, my experience and challenges experienced are available
on the [Galaxy_Report](https://github.com/Kauthar-Omar/My-Bioinformatics-Internship/blob/main/Galaxy_Report.md).

#### 9. Additional positive progress
In addition to the skills mentioned above the internship has been a good forum to build up on and cultivate some positive scientific cultures.
These include:
- The reading and analyzing of scientific papers through journal club hence even instilling progression of the culture independently.
- Attending scientific forums and webinars.
- Undertaking online courses to build on skill set.

### CONCLUSION
My experience here at ICIPE is and has been a continous skill set development process and a good exposure in the bioinformatics niche.
The peak of my internship so far has been the accreditation process as it gave me a good bioinformatics problem solving environment to applying
and build on learnt skills.
I have found keen interest in pipeline development to analyse genomic data and deduce solutions to address challenges of food security and health.
I am looking forward to achieve the following prior to the completion of the internship:
- Undertake and complete a mini project
- Address challenges outlined in each skill in the progress update section
- Understand containerization in bioinformatics and use one of the container systems.
