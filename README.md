# ESCMID-MGE-2022

Teaching materials for:

**ESCMID Online Courses and Workshops** 

**Moving beyond single species outbreaks: the role of mobile genetic elements** 

7 - 8 July 2022

* [View the course programme flyer here](https://www.escmid.org/fileadmin/src/media/PDFs/1Dates_Events/event_flyers/ESGEM_Course22_web.pdf)
* [Register for the event here (until 28 June 2022)](https://events.escmid.org/event/35)


This is supplementary "handbook" with a basic guide for **How to accurately reconstruct mobile genetic elements using bioinformatics**. We focus on 
plasmids, and mention other MGE (e.g. bacteriophage). We assume that you are interested in plasmid ecology and transmission as it applies to outbreak prevention and management.
We also assume that you could be a biological specialist (Infectious disease specialists, pharmacists, medical microbiologists, medical doctors, veterinarians) but may have minimal bioinformatics experience.

In that regard we will recommend simpler bioinformatics tools with intituitve outputs. This is no means an exhausitve review of all available options, merely a starting point with helpful advice to get you started. 

We have included basic theory (as lecture slides), workflows for steps you could take in your analysis, and worked examples with different tools (jupyter notebooks).

## Sample data

The worked examples includes sample data that you can also use to follow along. These include genome sequences, and simulated sequenced reads (short read/illumina and long read/ONT).These examples include:

* [A Multidrug resistant E. coli (ST131)](simulate_reads/simulate_reads.ipynb)

## Your starting point 

Bioinformatics often starts with a set of sequenced reads (short read Illumina), with
an added bonus of long read (PacBio/Oxford Nanopore) of a group of strains of interest. This is our starting point here. We will walk you through the steps to 
interogate the random ATGCs, and create meaningful biological results for mobile genetic elements especially for plasmid ecology and transmission. 

We recommend that you use [conda](https://docs.conda.io/en/latest/) where ever possible to install software. 

In general, we recommend that you approach your analysis with the following steps:

* Assemble your sequenced reads and partition plasmid and chromosome sequences. 
* Finding similar plasmids to compare with (maybe across species if thats desired); using genotyping, and taxonomy methods. 
* Comparing them visually, using tools like `mauve`/`act`/etc.
* Create a pangenome of all the sequences together.
* Use the core genes from this process for phylogenetic analysis 

See the suggested workflows below for more details.

## Suggested workflows 

[Identifying plasmid sequences in assemblies](https://tinyurl.com/4js7yf4y)

<img src="plas_vs_chrom.png "
     style="float: left; margin-right: 10px;" />


There are detailed worked examples for each of the tools mentioned:

* [Short read assembly with Shovill](assembly_annotation/assembly_annotation_short_reads.ipynb)
* [Hybrid (long + short read)assembly with unicycler](assembly_annotation/assembly_annotation_hybrid.ipynb)
* [Checking INC type (long read only) with Tiptoft](genotyping/plasmid_detect_tiptof.ipynb)
* [Reconstruction plasmid sequences with MOB-Suite](genotyping/plasmid_reconstruction_mobsuite.ipynb)
* [Selecting plasmid contigs with PLACNET](assembly_annotation/assembly_plasmid_placnet.ipynb)


### Installing the environment

```
conda create -y -n mge2022 mamba 
mamba create -y -n badread badread
conda activate mge2022 
mamba install -y  -c conda-forge notebook nb_conda_kernels
mamba install -y -c bioconda art
mamba install -y -c bioconda shovill
mamba install -y -c bioconda unicycler

```