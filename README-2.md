## Bowtie and BWA: DNA-Seq-Optimized Aligners
- Purpose: Bowtie and BWA are designed for DNA-seq data and are optimized for short-read alignments without splicing.
- Direct Alignment:
  - DNA doesn’t have splicing like RNA, so reads can be aligned directly to the genome without accounting for exon-intron boundaries.
  - Bowtie and BWA align reads continuously along the genome, without the need to detect spliced junctions.
- Applications:
  - Commonly used for aligning short DNA reads to a reference genome in applications like whole genome sequencing (WGS), exome sequencing, variant calling, and genome assembly.
  - Since they don’t detect splicing, they’re not ideal for RNA-seq, but they are efficient for DNA sequencing and for applications where precise, short-read alignment is needed.
- Pros:
  - Very fast and memory-efficient, especially for high-throughput DNA sequencing data.
  - Well-suited for applications that require aligning short DNA reads to a reference without splicing, like genome resequencing and SNP detection.
- Cons:
  - Cannot handle spliced reads, so they’re not suitable for RNA-seq where exon-intron boundaries must be considered.
  - Lack the flexibility needed for aligning reads in highly spliced, complex RNA samples.

