## REPORT ON GALAXY TRAINING NETWORK (GTN) SMORGASBORD COURSE.

### OBJECTIVES.
1. To learn skills to comfortably maneuver through the galaxy platform.
2. To be able to create and use workflows for scientific data analysis.
3. To learn about various tools and their implementation in the workflows to achieve a desired results.
4. To learn different data visualization techniques.

### INTRODUCTION.
Galaxy is an open, web-based platform foe accessible, reproducible and transparent computational research.
It includes scientific workflows, data and analysis persistence and publishing platform that aims to make computational biology accesible
to research scientists that do not have computer programming or system administration.
Its data intergration supports data uploads from user's computer by URL, and directly from online resources such as UCSC Genome Browser,
InterMine and BioMart supporting a range of widely used biological data formats and translation between those formats.
Galaxy was originally written for biological data analysis, particularly genomics.
The set of available tools have been expanded over the years to cover gene expression, genome assembly, proteomics, epigenomics,
transcriptomics and other disciplines in life sciences.
Although it was initially developed for genomic research , it is largely domain agonistic and now is used as a
a general bioinformatics management workflow.
The GTN Smorgasbord Course was aimed to create awareness and give an introductory training to what the Galaxy platform has to offer.

### HOW TO ACCESS THE COURSE.
In order to undertake the course you need to first create an account in one of the three galaxy servers i.e
[american/main](UseGalaxy.org), [european](UseGalaxy.eu) or [australian](UseGalaxy.org.au) server.
It is recommended you choose an server near you.
I personally recommend the european instance for Kenyans as it is in good proximity and provides a wider range of tools.
Here is a [link](https://shiltemann.github.io/global-galaxy-course/workshop) to redirect you to the course material.
It includes slides, videos and both written and video tutorials.

### MY TAKE-AWAY FROM THE COURSE

#### Introductory lesson
Galaxy interface has 3 main parts : on the right is your current history, left are the available tools and
in the central panel displays the homepage, tool forms, your analysis results and inspection of data.
Data to start your analysis can be uploaded or gotten from the get data section.
To inspect your data you click on the eye icon and it appears on the central panel.
Galaxy supports many file formats.

The **filter tool** can filter data on columns using simple expressions.
**Intersect tool** looks for intersecting sections between two or more datasets and is useful in generating overlapping genes.
**Concatenate** is a tool that combines two or more datasets head to tail.
For visualization of BED files IGB, IGV or UCSC main can be used.
The first two are applications hence one has to install while the latter is an online link.

You can create a workflow from your analysis to reuse it in a similar task.
Workflows capture all the tools and parameter settings needed to perform an analysis.
Its creation is done by **extract workflow** found from your current history.
Unwanted steps can be filtered out and workflow created.
Workflows can be edited or created from scratch using the workflow editor.

#### Quality control
**FastQC** tool provides a simple way to quality control raw sequence data by a modular set of analyses hence giving
a quick impression of problems in relation to data before further steps.
Generally the quality of the sequences drops at the end of the sequences.
Sequences must be treated to reduce bias in downstream analysis.
Quality treatments include cutting, trimming and masking sequences from low quality score regions, beginning and end of sequence
and removing adapters.
Filtering criteria also improve scores.
**Cutadapt** tool automates adapter trimming.
Paired-end analysis can occur and the quality checked by fastQC.
The reports from the both ends are aggregate by **MultiQC** on the FastQC reports.

#### Mapping
Before mapping occurs quality control is important.
Read mapping is the process to align the reads on a reference genomes aligning each read in the set of reads on the reference genome.
There are over 60 different mappers **Bowtie2** being one of such tools.
After mapping the checking statistics is important before proceeding with analysis to get possible errors.
The output of Bowtie2 is usually a BAM file hence its statistics are checked by **Samtools stats - generate statistics for BAM dataset**.
The last step of mapping is vizualizing mapped reads and can be done using pre installed IGV or JBrowse from galaxy.
**JBrowse** instances are websites hosted online that provide an interface to browse genomics data.
 Mapping algorithms of choice depends on your data.

 #### Assembly
Genome assembly ideally is the process of joining together DNA sequencing fragments into longer pieces upto chromosome lengths.
**Nanoplot** tool is used to check quality of nanopore reads before assembly.
The long nanopore reads are assembled with the **Flye** tool which has 5 output files.
The assembly can be visualized by **BandagImage** tool.
Assembly can be polished by mapping the more accurate short reads to the assembly and create an alignment file.
In this case short illumina reads are first mapped with **Map with BWA-MEM** tool,
then the short reads are compared to the assembly, and a polished assembly file created using **pilon**.
**Fasta Statistics** is run on both polished and unpolished assemblies to see how they compare.
The assembly can then be annoted with **Prokka** or **GeSeq**, the latter is found in Chlorobox not directly in galaxy and visualized by JBrowse.

#### RNA-Seq data analysis and R
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
The Z score for the most differentially expressed genes is determined by **Table Compute** both single and multiple table separately
and output used in plotting a heatmap.
Before running fuctional enrichment the datasets must be prepared for the task by selecting right parameters and tools to achieve it.
The last step of analysis is functional enrichment of the differentially expressed genes by performing gene ontology analysis with **goseq** tool.

**R studio** is supported on galaxy to enable R programming on the platform as an interactive tool.
Basic R syntax such as creating objects, good nomenclature of objects, reassigning objects and deleting the objects was covered.
Object data types or mode, mathematical operations on the objects and functional operations were illustrated and practised.
Creation of vectors using the **c()** function was introduced, operations on vectors and coercing values in the vectors.
Easy accession of objects when compiled in a list and how the lists are created summed up basics of R.

Advances in R in galaxy starts with importation of annotated DE genes in R by read.csv() and subsequent manipulation.
It is important to note or specify the separator so as to import the dataframe correctly.
A new data type, factors was illustrated and simple plots plotted using them.
The concept of subsetting and how vectors may be used was in introduced.
Concepts covered previously were applied in changing columns types by coercing and inspecting numerical columns using math, sorting
and renaming.
Manipulated dataframes assigned to new objects can be written in new files using **write.csv()** function by providing the object and new input file.
The dplyr library was introduced and used to select columns and filter rows.
filter() keeps all the rows that match the conditions that are provided mainly characterized by logical operations and the concept of
pipes **%>%** used improves the process and reduces redundancy.
Other notable dplyr function are mutate(), group_by() and summarise() used in column creation, grouping and summarizing data frames respectively.
Data frames can be reshaped using spread() and gather() from tidyr library.

R is popularly known for visualization.
Visualization are an important step to check the data, their quality and represent the results found for publication in RNA-seq data
analysis and other omics experiments.
A plotting package known as ggplot2 makes it simple to create complex plots from data in a data frame in R.
ggplot2 provides a more programmatic interface for specifying what variables to plot, how they are displayed, and general visual properties.
The covered geoms of ggplot2 were: geom_point() for scatter plots and dot plots and geom_boxplot() for boxplots.
Plot specifications such as transparency using alpha, colour, axis labels, spliting using face_grid(), themes can be applied.

#### Single-cell RNA-Seq Analysis
The first step in processing scRNA is bar cooding cells.
Barcodes are small oligonucleotides that are inserted into the captured sequence at a specific point to provide information on the cell the sequence
came from and the transcript the sequence came from.
When verifying barcode formats first the reads are extracted using **Filter sequences by ID** and the confirming of barcodes is done using FastQC and
examining the distribution of bases in a FastQC plot to infer the encoding of barcodes.
Barcode extraction and annotation of reads using **UMI-tools extract** tool is done hence uniting barcodes with sequence.
Its important to note that the cell and umi in the reverse read are added from th forward read.

Before analysis the data must be pre-processed.
**RNA STARsolo** performs demultiplexing, mapping, and quantification generating 6 output files.
They include: Log, Feature Statistic Summaries, Alignments, Matrix Gene Counts, Barcodes, Genes which are a program log, a mapping quality file,
a BAM file of alignments, and 3 count matrix files respectively.
The log file is subjected to MultiQc to check mapping quality.
**DropletUtils** suite tools are used to  reproduced a Cell Ranger workflow, rank barcodes and custom filtering options in pre-processing.
After getting counts, they first need to be prepared before preparing for clustering.
This is done by:
- Selection and filtration of cells and genes based on quality metric: Low-quality cells would interfere with downstream analyses. These cells may have been damaged during processing and may not have been fully captured by the sequencing protocol.
- Data normalization and scaling: eliminate cell-specific biases (e.g., in capture efficiency), allowing us to perform explicit comparisons across cells afterwards. Some transformations, typically log, are also applied to adjust for the mean-variance relationship.
- Selection of features: this picks a subset of interesting features for downstream analysis, by modelling the variance across cells for each gene and retaining genes that are highly variable. This step is done to reduce computational overhead and noise from uninteresting genes.

Principal Component Analysis (PCA) was done on the log-normalized expression values and the first 50 Principal Component (PCs) computed using
**Cluster, infer trajectories and embed with scanpy** tool and visualized by plot with scanpy using various plotting methods.
An Elbow plot i.e a ranking of the PCs based on the percentage of variance they explain is used to determine which PCs to keep making sure percentage variance
doesn't drop alot and keeping only those that satisfy the condition.
PCs are the clustered based on similar expression profiles using unsupervised clustering.
Graph-based clustering has been popularized for clustering large scRNA-Seq datasets using approaches like the K-nearest neighbor (KNN) graph.
The Louvain graph-clustering method (community detection based on optimizing modularity) was used with a resolution of 0.5 for clustering then plotted.
The welch t-test was used to find markers which has good statistical properties for large numbers of cells.
Another widely used method for pairwise comparisons between groups of observations is the Wilcoxon rank sum test.
All methods were visualized in plots and anndata inspected.
The marker genes should be more expressed in the clusters for which they are markers this information was confirmed with visualizations.
This was done by plotting expression probability distributions across clusters of top marker genes and top marker gene expression on an UMAP plot.
Comparison of the marker genes between clusters was done by identifaction of marker genes distinguishing cluster 0 from cluster 1 using Wilcoxon rank sum and
plotting the results.
Cell type annotation of the clusters is the last step.
The cell types are added as cluster name manipulated then plotted.
With the annotated cell types, we can also visualize the expression of their canonical marker genes by plotting.

#### Automating galaxy with workflows.
Most of the processes in galaxy use similar tools and have the same rational behind their use.
For the subsequent analysis I used workflows.
The workflows can be found in the in galaxy shared data or downloaded from the tutorials and imported to your workflows using import workflows and choosing
the option to upload from local device.
What is important to note is that your data should be in the right format as input in the workflow.
Parts of the training run by workflows include:
- **Proteomics tutorials**

The major highlight on this part is making sure you add a pipe when running proteogenomics 3 on the Uniprot input file as it isn't present when importing it from Proteogenomics 2.
- **NGS data logistics**

What to note is to make sure your accession numbers are in tabular form

#### Gene Annotation.
First you need to load the data of the genes you want annotated.
**Prokka** tool is then used to run the annotation with the condition to annotate contigs that are contigs.fasta which generates multiple outputs.
The outputs are exammined and fna output of Prokka is visualized using Jbrowser
Prokka takes time to get output.
Our main focus in annotation is visualization with Jbrowse to make inferences.

### CONCLUSION
The GTN training was very insightful and various skills on maneuvering through galaxy, creating workflows from history, using various tools, accessing available
workflows from shared data and troubleshooting errors were learnt.
An introduction to different analyses was covered.
Challenges is understanding Single-cell RNA-Seq Analysis were encountered.
In general it was a good self teaching experience and the beginning to expand knowledge on galaxy.
