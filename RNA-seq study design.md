# RNA-seq Study Design

### Answer these questions to ensure that the data generated will be meaningful and interpretable:

<details>
<summary> Can you verify that the experiment ran as expected and produced reliable data? </summary>

  You could use **replicates** (multiple samples per condition) or checking if a known response is observed.

  **Example:** If you're studying the effect of a drug on gene expression, you could include replicates for each condition (e.g., treated and untreated) to confirm the drug’s consistent effect across samples.

</details>


<details>
<summary> What are the controls? </summary>

  
  The choice of control samples depends on the specific question you're asking. 
  
  **Controls** are essential for comparing your experimental samples and assessing the impact of the treatment or condition you’re testing.
  
  **Example**: If you want to know how a treatment affects cancer cells, a control could be untreated cancer cells. 
  This allows you to see which genes are differentially expressed due to the treatment.
</details>


  
<details>
<summary> What insight is to be gained from each treatment/condition? </summary>

  Think about what you want to learn from each condition. 
  This helps determine _which conditions are necessary_ and _how many replicates you need_ to answer your research question.

  **Example**: In a study with different drug doses (e.g., low, medium, high), you might want to see if gene expression changes in a dose-dependent manner. 
  Each dose level would represent a different condition to help answer this question.

</details>



  
<details>
<summary> What's the Signal-to-Noise Ratio for your cell type </summary>

  Different cell types have different levels of gene expression, which affects how easy it is to detect true biological signals over background noise. 
  Some tissues or cell types naturally have higher variability.

**Example**: Brain tissue has a complex mix of cell types, so it may have a higher “noise” level compared to something like cultured cells. 
This could mean you need more replicates to confidently detect gene expression changes.
</details>

