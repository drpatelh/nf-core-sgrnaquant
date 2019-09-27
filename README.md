# ![nf-core/sgrnaquant](docs/images/nfcore-sgrnaquant_logo.png)

[![Build Status](https://travis-ci.com/nf-core/sgrnaquant.svg?branch=master)](https://travis-ci.com/nf-core/sgrnaquant)
[![Nextflow](https://img.shields.io/badge/nextflow-%E2%89%A50.32.0-brightgreen.svg)](https://www.nextflow.io/)

[![install with bioconda](https://img.shields.io/badge/install%20with-bioconda-brightgreen.svg)](http://bioconda.github.io/)
[![Docker](https://img.shields.io/docker/automated/nfcore/sgrnaquant.svg)](https://hub.docker.com/r/nfcore/sgrnaquant)

## Introduction

**nfcore/sgrnaquant** is a bioinformatics analysis pipeline used for the quantification of CRISPR sgRNA guides obtained from Illumina sequencing.

The pipeline is built using [Nextflow](https://www.nextflow.io), a workflow tool to run tasks across multiple compute infrastructures in a very portable manner. It comes with docker containers making installation trivial and results highly reproducible.

## Pipeline summary

1. Raw read QC ([`FastQC`](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/))
2. Adapter trimming ([`cutadapt`](https://cutadapt.readthedocs.io/en/stable/guide.html))
3. Alignment ([`BWA`](https://sourceforge.net/projects/bio-bwa/files/))
4. Count reads and split by strand after filtering ([`Pysam`](http://pysam.readthedocs.io/en/latest/installation.html) to remove:
    1. reads that are unmapped
    2. reads that map to multiple guides
    3. reads containing > 0 mismatches
5. Present QC for raw read, alignment and filtering results ([`MultiQC`](http://multiqc.info/))

## Quick Start

i. Install [`nextflow`](https://nf-co.re/usage/installation)

ii. Install one of [`docker`](https://docs.docker.com/engine/installation/), [`singularity`](https://www.sylabs.io/guides/3.0/user-guide/) or [`conda`](https://conda.io/miniconda.html)

iii. Download the pipeline and test it on a minimal dataset with a single command

```bash
nextflow run nf-core/sgrnaquant -profile test,<docker/singularity/conda>
```

iv. Start running your own analysis!

```bash
nextflow run nf-core/sgrnaquant -profile <docker/singularity/conda> --design design.csv --genome GRCh37
```

See [usage docs](docs/usage.md) for all of the available options when running the pipeline.

## Documentation

The nf-core/sgrnaquant pipeline comes with documentation about the pipeline, found in the `docs/` directory:

1. [Installation](https://nf-co.re/usage/installation)
2. Pipeline configuration
    * [Local installation](https://nf-co.re/usage/local_installation)
    * [Adding your own system config](https://nf-co.re/usage/adding_own_config)
    * [Reference genomes](https://nf-co.re/usage/reference_genomes)
3. [Running the pipeline](docs/usage.md)
4. [Output and how to interpret the results](docs/output.md)
5. [Troubleshooting](https://nf-co.re/usage/troubleshooting)

## Credits

The pipeline was originally written by [The Bioinformatics & Biostatistics Group](https://www.crick.ac.uk/research/science-technology-platforms/bioinformatics-and-biostatistics/) for use at [The Francis Crick Institute](https://www.crick.ac.uk/), London.

The pipeline was developed by [Harshil Patel](mailto:harshil.patel@crick.ac.uk).

## Citation

<!-- TODO nf-core: Add citation for pipeline after first release. Uncomment lines below and update Zenodo doi. -->
<!-- If you use nf-core/sgrnaquant for your analysis, please cite it using the following doi: [10.5281/zenodo.XXXXXX](https://doi.org/10.5281/zenodo.XXXXXX) -->

You can cite the `nf-core` pre-print as follows:  
Ewels PA, Peltzer A, Fillinger S, Alneberg JA, Patel H, Wilm A, Garcia MU, Di Tommaso P, Nahnsen S. **nf-core: Community curated bioinformatics pipelines**. *bioRxiv*. 2019. p. 610741. [doi: 10.1101/610741](https://www.biorxiv.org/content/10.1101/610741v1).
