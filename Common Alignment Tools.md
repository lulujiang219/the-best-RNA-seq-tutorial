## STAR and HISAT2: RNA-Seq-Optimized Aligners
- **Purpose**: STAR and HISAT2 are specifically designed for **RNA-seq data**. They can handle **spliced alignments**, meaning they recognize and account for the exon-intron structure of genes in eukaryotes.
- **Spliced Alignment**:
  - In RNA-seq, spliced reads often span these **exon-exon junctions**, meaning part of the read aligns to the end of one exon and the other part aligns to the beginning of the next exon. 
    - **exon-exon Junction**: In the mature mRNA (after splicing), exons are directly connected to each other, with no intron in between. The junction is where one exon ends and the next begins.
  - STAR and HISAT2 are designed to detect these exon-exon junctions in the reads, which allows them to correctly map reads even though the intron was removed.
- **Applications**: Used for aligning RNA-seq reads to reference genomes for studies on _gene expression_, _alternative splicing_, _gene structure_, and _transcript quantification_.
- **Pros**:
  - Can accurately align spliced reads, which is essential for RNA-seq data.
  - Suitable for detailed studies on gene structure and expression levels.
- **Cons**:
  - Requires more computational resources than simpler aligners because they handle the complexity of spliced alignments.
  - Not typically used for DNA-seq or short-read DNA alignments where splicing isn’t a concern.

## Bowtie and BWA: DNA-Seq-Optimized Aligners
- **Purpose**: Bowtie and BWA are designed for **DNA-seq data** and are optimized for **short-read alignments** without splicing.
- **Direct Alignment**:
  - DNA doesn’t have splicing like RNA, so reads can be aligned directly to the genome without accounting for exon-intron boundaries.
  - Bowtie and BWA align reads continuously along the genome, without the need to detect spliced junctions.
- **Applications:**
  - Commonly used for aligning short DNA reads to a reference genome in applications like _whole genome sequencing (WGS)_, _exome sequencing_, _variant calling_, and _genome assembly._
  - Since they don’t detect splicing, they’re not ideal for RNA-seq, but they are efficient for DNA sequencing and for applications where precise, short-read alignment is needed.
- **Pros**:
  - Very fast and memory-efficient, especially for high-throughput DNA sequencing data.
    - Why?
      - **Bowtie** uses an indexing method called the **Burrows-Wheeler Transform (BWT)** along with the **FM Index**. These methods compress the genome data and allow the tool to quickly find matching regions without having to scan through the entire genome base by base.
      - **BWA** also uses BWT and FM Index, which makes the alignment process fast and memory-efficient.
      - These indexing methods allow Bowtie and BWA to quickly locate potential matches and perform exact alignment only in specific regions, rather than searching the whole genome in a linear fashion.
      - Also Bowtie and BWA are designed for DNA-seq so they don’t need to identify splicing junctions or handle the additional complexity of RNA splicing. This allows them to process reads in a more straightforward and streamlined way.

  - Well-suited for applications that require aligning short DNA reads to a reference without splicing, like genome resequencing and SNP detection.
- **Cons**:
  - Cannot handle spliced reads, so they’re not suitable for RNA-seq where exon-intron boundaries must be considered.
  - Lack the flexibility needed for aligning reads in highly spliced, complex RNA samples.


## Summary: Methods of Matching Reads to Reference Genomes and Transcriptomes
| Feature                  | STAR & HISAT2                              | Bowtie & BWA                              | Salmon & Kallisto                         |
|--------------------------|--------------------------------------------|-------------------------------------------|-------------------------------------------|
| **Designed For**         | RNA-seq spliced reads  | DNA-seq align reads continuously to reference genome   | RNA-seq quantification   |
| **Handles Spliced Reads**| Yes (critical for RNA-seq)                | No (this is DNA-seq)                     | Not needed (pseudo-alignment)             |
| **Common Applications**  | RNA-seq, transcriptomics, gene expression  | DNA-seq, variant calling, genome assembly | RNA-seq quantification, gene expression, provide raw counts for each gene in Differential Expression Analysis (DESeq2)   |
| **Speed and Efficiency** | slow and computationally intensive to find the exact position of each read    | Fast and memory-efficient | Very fast and efficient     |
| **Alignment Type**       | Spliced alignment across exons/introns     | Continuous alignment without splicing     | Pseudo-alignment |
| **Input File**           | FASTQ (reads), FASTA (reference genome or transcriptome) | FASTQ (reads), FASTA (reference genome) | FASTQ (reads), FASTA (reference transcriptome) |
| **Output File**          | BAM/SAM (aligned reads)                   | BAM/SAM (aligned reads)                   | Quantification file (e.g., TPM counts, transcript/gene abundance) |
