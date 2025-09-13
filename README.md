# GWAS Height Analysis

## Overview
This project demonstrates a GWAS-style analysis using summary-level data from the **NHGRI-EBI GWAS Catalog**. The workflow includes data cleaning, and visualization, illustrating fundamental concepts of genome-wide association studies.

---

## Dataset
- **Source:** GWAS Catalog associations TSV for a specific trait (e.g., `gwas-association-downloaded_2025-09-13-OBA_VT0001253.tsv`).  
- **Columns used:** 
  - `CHR_ID` → Chromosome  
  - `CHR_POS` → SNP Position  
  - `SNP_ID_CURRENT` → SNP Identifier  
  - `P-VALUE` → Association P-value  
  - `OR or BETA` → Effect size  
  - `MAPPED_GENE` → Gene mapping (optional)  


## Workflow

1. **Data Loading & Cleaning**
   - Read the TSV with `pandas` (`low_memory=False`).  
   - Strip whitespace from headers.  
   - Standardize column names (`Chrom`, `Pos`, `SNP`, `P-value`, `Beta`).  
   - Clean chromosome column: convert floats (`1.0`) to integers (`'1'`), uppercase `X/Y/MT`, remove invalids.  
   - Ensure numeric columns (`P-value`, `Beta`, `Pos`) are valid.

2. **Filtering Significant SNPs**
   - Filter SNPs with genome-wide significance (`P < 5e-8`).  
   - Identify top associated SNPs.

3. **Visualization**
   - **Manhattan Plot:** Shows -log10(P-value) across chromosomes; highlights top SNPs.  
   - **QQ Plot:** Observed vs expected -log10(P-values) to check for inflation/deviation.  

4. **Output**
   - `gwas_catalog_processed.tsv` → cleaned and processed association data  
   - Figures: Manhattan, QQ

---

## Requirements
- Python ≥ 3.8  
- Packages:
  - pandas
  - numpy
  - matplotlib

```
pip install pandas numpy matplotlib
```
