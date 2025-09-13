# GWAS Height Analysis

## Overview
This project demonstrates a GWAS-style analysis using summary-level data from the **NHGRI-EBI GWAS Catalog**. The workflow includes data cleaning, visualization, and polygenic risk score (PRS) simulation, illustrating fundamental concepts of genome-wide association studies.

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

> Note: Individual-level genotype data is not included. PRS is simulated for demonstration purposes.

---

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
   - **PRS Simulation Plot:** Simulated individuals’ PRS vs simulated trait values.

4. **Polygenic Risk Score Simulation**
   - Generate random genotypes for top SNPs.  
   - Calculate PRS as weighted sum of effect sizes (Beta).  
   - Plot PRS against simulated trait values to demonstrate predictive power.

5. **Output**
   - `gwas_catalog_processed.tsv` → cleaned and processed association data  
   - `simulated_prs.csv` → simulated PRS for N individuals  
   - Figures: Manhattan, QQ, and PRS plots

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
