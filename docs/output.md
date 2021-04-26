# nf-core/smartseq2: Output

This document describes the output produced by the pipeline. Most of the plots are taken from the MultiQC report, which summarises results at the end of the pipeline.

## Table of contents

- [nf-core/smartseq2: Output](#nf-coresmartseq2-output)
  - [Table of contents](#table-of-contents)
  - [FastQC](#fastqc)
  - [MultiQC](#multiqc)
  - [BraCeR](#bracer)
  - [TraCeR](#tracer)
  - [STAR](#star)
  - [RSEM](#rsem)
  - [featureCounts](#featurecounts)

## FastQC

[FastQC](http://www.bioinformatics.babraham.ac.uk/projects/fastqc/) gives general quality metrics about your reads. It provides information about the quality score distribution across your reads, the per base sequence content (%T/A/G/C). You get information about adapter contamination and other overrepresented sequences.

For further reading and documentation see the [FastQC help](http://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/).

> **NB:** The FastQC plots displayed in the MultiQC report shows _untrimmed_ reads. They may contain adapter sequence and potentially regions with low quality. To see how your reads look after trimming, look at the FastQC reports in the `trim_galore` directory.

**Output directory: `results/fastqc`**

- `sample_fastqc.html`
  - FastQC report, containing quality metrics for your untrimmed raw fastq files
- `zips/sample_fastqc.zip`
  - zip file containing the FastQC report, tab-delimited data file and plot images

## MultiQC

[MultiQC](http://multiqc.info) is a visualisation tool that generates a single HTML report summarising all samples in your project. Most of the pipeline QC results are visualised in the report and further statistics are available in within the report data directory.

The pipeline has special steps which allow the software versions used to be reported in the MultiQC output for future traceability.

**Output directory: `results/multiqc`**

- `multiqc_report.html`
  - MultiQC report - a standalone HTML file that can be viewed in your web browser
- `multiqc_data/`
  - Directory containing parsed statistics from the different tools used in the pipeline

For more information about how to use MultiQC reports, see [http://multiqc.info](http://multiqc.info)

## BraCeR

[BraCeR](https://github.com/Teichlab/bracer) is a tool for reconstruction of B cell receptor sequences from single-cell RNA-seq data.

**Output direcetory: `results/BraCeR`**

- `filtered_BCR_summary/IMGT_gapped_db.tab`
  - summary of all detected Immunoglobuling chains for all cells
- `[CELL]`
  - For each cell, there's a dedicated output directory containing more detailed information than what's in the summary.

## TraCeR

[TraCeR](https://github.com/Teichlab/tracer) is a tool for reconstruction of T cell receptor sequences from single-cell RNA-seq data.

**Output directory: `results/TraCeR`**

- `filtered_TCR_summary/cell_data.csv`
  - summary of all detected T cell receptor chains for all cells
- `[CELL]`
  - For each cell, there's a dedicated output directory containing more detailed information than what's in the summary.

## STAR

[STAR](https://github.com/alexdobin/STAR) is a ultra-fast RNA-seq aligner.

**Output directory: `results/STAR`**

- `[CELL]/[CELL].Aligned.toTranscriptome.out.bam`
  - BAM file aligned to the transcriptome
- `[CELL]/[CELL].Aligned.sortedByCoord.out.bam`
  - The same BAM file, but sorted
- `[CELL]/[CELL].Log.final.out`
  - The STAR alignment report, containing mapping results summary.

## RSEM

[RSEM](https://github.com/deweylab/RSEM) is a tool for the accurate quantification of gene and isoform expression
from RNA-seq data. We use it to compute Transcript per Million (TPM)-normalized gene expression
values for each cell.

**Output directory: `results/RSEM`**

- `resultTPM.txt`
  - tab separated TPM matrix for all genes and cells.
- `[CELL]`
  - For each cell, there's a dedicated output directory, containing the raw results and statistics.

## featureCounts

[featureCounts](http://bioinf.wehi.edu.au/featureCounts/) is a highly-efficent tool that summarizes
mapped reads for genomic features. We use it to compute raw count values for each gene and cell.

**Output directory: `results/featureCounts`**

- `resultCOUNT.txt`
  - tab sparated count matrix for all genes and cells.
- `[CELL]`
  - For each cell, there's a dedicated output directory, containing the raw results and statistics.
