# RNA-seq Study Design

### Answer these questions to ensure that the data generated will be meaningful and interpretable:

- **Can you verify that the experiment ran as expected and produced reliable data?**
  - You could use **replicates** (multiple samples per condition) or checking if a known response is observed.
  - **Example:**

    If you're studying the effect of a drug on gene expression, you could include replicates for each condition (e.g., treated and untreated) to confirm the drug’s consistent effect across samples.



- **What are the controls?**
  - The choice of control samples depends on the specific question you're asking.
  - **Controls** are essential for comparing your experimental samples and assessing the impact of the treatment or condition you’re testing.
  - **Example**:

    If you want to know how a treatment affects cancer cells, a control could be untreated cancer cells. 
    This allows you to see which genes are differentially expressed due to the treatment.


- **What insight is to be gained from each treatment/condition?** 
  - Think about what you want to learn from each condition. 
  - This helps determine <ins>which conditions are necessary</ins> and <ins>how many replicates you need</ins> to answer your research question.
  - **Example**: 
  
    In a study with different drug doses (e.g., low, medium, high), you might want to see if gene expression changes in a dose-dependent manner. 
    Each dose level would represent a different condition to help answer this question.



- **What's the Signal-to-Noise Ratio for your cell type?** 
  - Different cell types have different levels of gene expression, which affects how easy it is to detect true biological signals over background noise.
  - Some tissues or cell types naturally have higher variability.
  - **Example**:

    Brain tissue has a complex mix of cell types, so it may have a higher “noise” level compared to something like cultured cells.
    This could mean you need more replicates to confidently detect gene expression changes.



# RNA-seq Analysis

- **How Do I Check the Quality of My Reads?**
  - Quality control (QC) is essential to ensure that sequencing data is of high quality.
  - Tools like **FastQC** check for adapter contamination, low-quality bases, and GC content.
  - **Example:**

    After sequencing, you run FastQC on your FASTQ files to identify any low-quality bases or contamination that needs trimming before further analysis.

- **Which Aligner Should I Use?**
  - Aligners match reads to a reference genome or transcriptome.
  - **STAR and HISAT2** are popular choices for RNA-seq because they handle exon-exon junctions, which is important for spliced RNA.
    
    - ```STAR (Spliced Transcripts Alignment to a Reference)```:
      - Junction Detection: STAR uses a “seed-and-extend” approach to identify reads that align across exon-exon junctions. It first identifies short matching regions (seeds) at the ends of reads, then extends the alignment by finding where the read aligns across the junction.
      - Benefit: This approach allows STAR to accurately align reads that span across exons, even when it encounters novel splice junctions that aren’t annotated in the reference genome.
  
    - ```HISAT2 (Hierarchical Indexing for Spliced Alignment of Transcripts)```:
  
      - Hierarchical Indexing with FM Index: HISAT2 uses a technique called “**hierarchical indexing**” to handle large genomes efficiently. It combines the **Burrows-Wheeler Transform** with a special data structure for identifying exon-exon junctions quickly.
  
      - **Splice Site Indexing:** HISAT2 uses a splice-aware index, which includes known and predicted exon-intron junctions. When a read partially aligns to one exon and then continues across an intron to the next exon, HISAT2 can recognize this as a splice junction.
  
      - Benefit: HISAT2’s hierarchical approach allows it to align reads across large genomes while detecting exon-intron junctions efficiently, making it suitable for complex genomes.



- **Am I Using the Proper Statistical Methods?**
  - Correct statistical methods are crucial to accurately identify differentially expressed genes.
  - ```DESeq2``` and ```edgeR``` are commonly used for RNA-seq data because they account for biological variability and sequencing depth.
  - **Example**:

    After alignment, you use DESeq2 to compare gene expression between treated and control samples, identifying genes that show significant changes.

- **What Are the Best Ways to Visualize Results?**
  - Visualizing data helps you interpret and communicate your findings.
  - Common RNA-seq visualizations include heatmaps, PCA plots, and volcano plots.
  - **Example**:

    You use a PCA plot to check for clustering between your control and treated samples, which helps verify that the treatment is causing a distinct change in gene expression.
    A volcano plot can then show the differentially expressed genes, highlighting those with the greatest fold change and significance.








