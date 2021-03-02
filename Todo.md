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
Filtering criteria also improve scores. 
**Cutadapt** tool automates adapter trimmimg. 
Paired-end analysis can occur and the quality checked by fastQC. 
The reports from the both ends are aggregate by **MultiQC** on the FastQC reports.

##### Mapping
Before mapping occurs quality control is important. 
Read mapping is the process to align the reads on a reference genomes aligning each read in the set of reads on the reference genome. 
There are over 60 different mappers **Bowtie2** being one of such tools. 
After mapping the checking statistics is important before proceding with analysis to get possible errors. 
The output of Bowtie2 is usually a BAM file hence its statistics are checked by **Samtools stats - generate statistics for BAM dataset**.
The last step of mapping is vizualizing mapped reads and can be done using pre installed IGV or JBrowse from galaxy.
**JBrowse** instances are websites hosted online that provide an interface to browse genomics data. 
 Mapping algorithms of choice depends on your data.
 
 ##### Assembly
Genome assembly ideally is the process of joining together DNA sequencing fragments into longer pieces upto chromosome lengths. 
**Nanoplot** tool is used to check quality of nanopore reads before assembly. 
The long nanopre reads are assembled with the **Flye** tool which has 5 output files.
The assembly can be visualized by **BandagImage** tool.
Assembly can be polished by mapping the more accurate short reads to the assembly and create an alignment file.
In this case short illumina reads are first mapped with **Map with BWA-MEM** tool,
then the short reads are compared to the assembly, and a polished assembly file created using **pilon**.
**Fasta Statistics** is run on both polished and unpolished assemblies to see how they compare.
The assembly can then be annoted with **Prokka** or **GeSeq**, the latter is found in Chlorobox not directly in galaxy and visualized by JBrowse.

##### RNA-Seq data analysis and R
The most common aims of RNA-Seq is to profile gene expression by identifying genes or molecular pathways
that are differentially expressed (DE) between two or more biological conditions.
Quality control is the first step followed by mapping which is done using **RNA STAR** tool.
The quality of the maps are also checked by MultiQC.
The library strandedness is the determined using **Infer Experiment** but before that make sure your file is in the right format for input
by converting it to BED using **Convert GTF to BED12** tool.
The number of reads per annotated gene are counted with **featureCounts** tool and quality checked.

Determination of differntially expressed features is done using **DESeq2** which results into 3 outputs : 
a table with the normalized counts for each gene (rows) in the samples (columns),a graphical summary of the results which is useful to
evaluate the quality of the experiment and a summary file with key values for each gene.
Extraction of the most differentially expressed genes is done by **Filter data on any column using simple expressions**  to extract genes
with a significant change in gene expression (adjusted p-value below 0.05) between treated and untreated samples used as input data.
**Filter** is used for filtering to extract genes with an abs(log2FC)>1.
The differentially expressed genes are annoted using **Annotate DESeq2/DEXSeq output tables** tool using the recent filter as input.
Normalized counts of the most differentially expressed genes are extracted in two steps and visualized by plotting using **heatmap2** tool.
The Z score for the most differentially expressed genes is determined by **Table Compute** both single and multiple table separetly 
and output used in plotting a heatmap.
Before running fuctional enrichment the datasets must be prepared for the task by selecting right parameters and tools to achieve it.
The last step of analysis is functional enrichment of the differentially expressed genes by performing gene ontology analysis with **goseq** tool.

**R studio** is supported on galaxy to enable R programming on the platform.






