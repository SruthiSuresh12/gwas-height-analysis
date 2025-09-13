# Report on a Proof-of-Concept GWAS Project
## Project Summary
This report documents a genome-wide association study (GWAS) project focused on a polygenic trait, human height, using publicly available data from the GWAS Catalog. The project demonstrates the standard workflow of a GWAS, including data processing, statistical visualization, and conceptual demonstration of a Polygenic Risk Score (PRS).

## 1. Key Understandings and Findings
The project successfully executed the core steps of a GWAS pipeline, providing valuable insights into the nature of complex traits.

**Manhattan Plot:** The most significant finding from the project is the visualization of a polygenic trait. The Manhattan plot  clearly shows multiple distinct "towers" or peaks distributed across different chromosomes. Each peak represents a genomic region where genetic variants are significantly associated with the trait. This scattered pattern of significant associations, rather than a single, dominant peak, is characteristic of polygenic traits influenced by many genes, each with a small effect.

**QQ Plot:** The QQ plot served as a critical quality control step. The plot's "hockey stick" shape, where the observed P-values deviate sharply from the expected diagonal line, is strong evidence that the dataset contains a large number of true genetic associations rather than random noise. The extreme curvature of the plot confirms that the data source is not a raw GWAS but a filtered list of highly significant findings from a larger study.

## 2. Limitations of this Proof-of-Concept
While the project is a successful demonstration, it is essential to recognize its limitations due to the nature of the data used.

**Summary-Level Data:** The most significant limitation is that the project used summary-level data from the GWAS Catalog, which contains only aggregate information (e.g., P-values and effect sizes) from published studies. It does not include individual-level genotype data, which is crucial for a real-world analysis.

**Inability to Calculate a Real PRS:** Because of the lack of individual-level data, it was not possible to calculate a true Polygenic Risk Score. A PRS requires knowing the specific genotype for each SNP for every individual in a cohort.

**Pre-filtered Data:** The GWAS Catalog is a curated database of significant associations. Therefore, the data is not a complete, unfiltered GWAS dataset. This is why the QQ plot shows an extreme "hockey stick" shape and why the Manhattan plot lacks the typical "sea of noise" from non-significant SNPs. Consequently, this project could not be used to assess issues like population stratification, which are typically identified by looking for widespread genomic inflation in a full QQ plot.

## 3. Future Work
To evolve this project into a more comprehensive, real-world analysis, the following steps are recommended:

**Obtain Individual-Level Data:** The most critical step is to acquire an individual-level genotype dataset. Public resources like the UK Biobank or the 1000 Genomes Project are potential sources, though they often require approval and are not as easy to access as the GWAS Catalog.

**Perform a Full GWAS:** With individual-level data, you can run a full GWAS from scratch, including quality control, imputation, and association testing. This will generate a complete set of P-values for all SNPs, allowing for a more accurate and realistic QQ plot.

**Calculate PRS:** Once the full dataset is available and the GWAS has been performed, you can calculate a real Polygenic Risk Score for each individual in the cohort.

**Validate the PRS:** The final step would be to validate the PRS by analyzing its correlation with the actual phenotype (the measured trait). You could also explore different PRS methods, such as P+T (Pruning and Thresholding) or LDPred, to see which provides the best predictive power.

## Conclusion:

This project serves as a robust and insightful proof-of-concept for understanding the fundamentals of a GWAS pipeline. While the data limitations prevent a real-world PRS calculation, the project successfully demonstrates key concepts of data visualization and statistical interpretation, providing a solid foundation for more advanced genetic analyses in the future.
