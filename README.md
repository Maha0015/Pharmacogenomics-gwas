# Pharmacogenomics-gwas
Genome-wide association study identifying genetic variants associated with drug response for precision medicine applications

# Pharmacogenomics Genome-Wide Association Study (GWAS)

##  Overview

This project performs a comprehensive genome-wide association study (GWAS) to identify genetic variants that influence individual responses to medications. By analyzing pharmacogenomic datasets, we can predict drug efficacy, adverse reactions, and optimal dosing strategies based on a patient's genetic profile.

### Research Questions
- Which genetic variants are significantly associated with drug metabolism?
- Can we predict drug response phenotypes from genotype data?
- What is the clinical utility of pharmacogenomic testing?

### Key Features
- **GWAS Analysis**: Genome-wide screening for drug-response associations
- **Quality Control**: Rigorous filtering of samples and variants
- **Population Stratification**: Ancestry-based correction using PCA
- **Functional Annotation**: Mapping variants to genes and pathways
- **Clinical Interpretation**: Translating findings to actionable recommendations

##  Methods & Workflow

### Analysis Pipeline

1. **Data Preprocessing**
   - Sample quality control (call rate, heterozygosity, sex check)
   - Variant quality control (MAF, HWE, missingness)
   - Relatedness filtering (IBD/IBS analysis)

2. **Population Structure Analysis**
   - Principal Component Analysis (PCA) for ancestry inference
   - Admixture analysis for mixed populations
   - Stratification correction in association tests

3. **Association Testing**
   - Linear/logistic regression for quantitative/binary traits
   - Covariate adjustment (age, sex, PCs)
   - Multiple testing correction (Bonferroni, FDR)

4. **Post-GWAS Analysis**
   - Functional annotation (gene mapping, regulatory elements)
   - Pathway enrichment analysis
   - Drug-gene interaction databases (PharmGKB, DrugBank)

5. **Clinical Translation**
   - Identify actionable pharmacogenomic variants
   - Generate dosing recommendations
   - Clinical guidelines integration (CPIC, DPWG)

### Technologies Used
- **Programming**: Python 3.8+, Pandas, NumPy
- **Bioinformatics Tools**: PLINK, BCFtools, pysam
- **Statistical Analysis**: scipy, statsmodels
- **Visualization**: Matplotlib, Seaborn (Manhattan plots, QQ plots)
- **Genomic Databases**: PharmGKB, ClinVar, dbSNP

##  Key Results

### Discovery Findings
- **Genome-wide significant loci**: Identified variants reaching p < 5×10⁻⁸
- **Candidate genes**: Drug-metabolizing enzymes (CYP2D6, CYP2C19, CYP3A4/5)
- **Effect sizes**: Odds ratios and beta coefficients for each association
- **Genomic inflation factor (λ)**: Quality metric for population stratification control

### Clinical Implications
- **Actionable variants**: FDA-labeled pharmacogenomic biomarkers
- **Dosing adjustments**: Recommendations for poor/ultra-rapid metabolizers
- **Drug selection**: Alternative medications based on genetic profile
- **Adverse event prediction**: Risk stratification for serious side effects

### Sample Visualizations
*Generated in notebook:*
- Manhattan plots showing genome-wide p-values
- QQ plots for assessing test statistic inflation
- PCA plots for population structure
- Regional association plots (LocusZoom-style)
- Heatmaps of drug-gene interactions

##  Usage

### Prerequisites
```bash
pip install -r requirements.txt
```

### Running the Analysis
```bash
# Interactive analysis in Jupyter
jupyter notebook pharmacogenomics-gwas.ipynb

# Command-line execution
jupyter nbconvert --execute --to html pharmacogenomics-gwas.ipynb
```

### Input Data Format
The analysis expects:
- **Genotype data**: VCF or PLINK binary format (.bed/.bim/.fam)
- **Phenotype data**: CSV with sample IDs and drug response measurements
- **Covariate data**: CSV with age, sex, ancestry PCs

Example phenotype file:
```csv
SampleID,DrugResponse,Age,Sex,PC1,PC2,PC3
SAMPLE001,responsive,45,M,0.012,-0.008,0.003
SAMPLE002,non-responsive,52,F,-0.015,0.021,-0.001
```

##  Project Structure

```
pharmacogenomics-gwas/
├── pharmacogenomics-gwas.ipynb       # Main analysis notebook
├── README.md                          # This file
└── requirements.txt                   # Python dependencies
```

##  Data Sources

### Datasets Used
This analysis was performed on datasets from the following sources:

**Genomic Data:**
- **1000 Genomes Project Phase 3**: Population-scale whole genome sequencing
  - Reference: https://www.internationalgenome.org/
  - Chromosomes analyzed: chr1-chr22, chrX
  - Format: VCF files (GRCh38 coordinates)

**Pharmacogenomic Annotations:**
- **PharmGKB**: Clinical variant annotations
  - Source: https://www.pharmgkb.org/downloads
  - File: `clinicalVariants.tsv`
  - Drug-gene associations and clinical guidelines

**Population Information:**
- **IGSR 1000 Genomes Phase 3**: Sample metadata
  - Population codes and ancestry assignments
  - File: `igsr_1000genomes_phase3_release.tsv`

### Data Availability
Raw genomic data files (multi-GB VCF files) are not included in this repository due to size constraints. 

**To reproduce this analysis:**
1. Download 1000 Genomes Phase 3 data from: https://www.internationalgenome.org/data
2. Download PharmGKB clinical variants: https://www.pharmgkb.org/downloads
3. Ensure data files are in `1000Genomes/` subdirectory
4. Run the notebook cells in order

**Note:** All analysis outputs, visualizations, and results are preserved in the Jupyter notebook, so you can review the complete analysis without re-running the code.

##  Biological & Clinical Significance

### Pharmacogenomics in Precision Medicine

This analysis contributes to **precision medicine** by:

1. **Drug Selection**: Choosing medications most likely to be effective
2. **Dosing Optimization**: Adjusting doses based on metabolizer status
3. **Adverse Event Prevention**: Avoiding drugs likely to cause harm
4. **Cost Reduction**: Eliminating trial-and-error prescribing


##  Dependencies

See `requirements.txt` for complete list. Main packages:
```
pandas>=1.5.0
numpy>=1.23.0
matplotlib>=3.6.0
seaborn>=0.12.0
scipy>=1.9.0
pysam>=0.19.0
jupyter>=1.0.0
```

**External tools** (not managed by pip):
- PLINK 1.9+ (for LD operations)
- BCFtools 1.15+ (for VCF manipulation)
- Tabix (for indexed VCF files)


##  References & Resources

### Key Pharmacogenomic Databases
- **PharmGKB**: https://www.pharmgkb.org/
- **CPIC Guidelines**: https://cpicpgx.org/
- **FDA Pharmacogenomics**: https://www.fda.gov/drugs/science-research-drugs/table-pharmacogenomic-biomarkers-drug-labeling

### Relevant Publications
- Roden DM, et al. "Pharmacogenomics." *Lancet* (2019)
- Relling MV, Evans WE. "Pharmacogenomics in the clinic." *Nature* (2015)
- Clinical Pharmacogenetics Implementation Consortium (CPIC) guidelines

---
