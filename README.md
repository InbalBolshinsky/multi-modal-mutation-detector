# Multi-Modal Genetic Mutation Detector" 

## Project Overview
This project analyzes genetic mutations associated with lung cancer by focusing on three key genes: **EGFR**, **KRAS**, and **ALK**. The study explores the clinical significance of these mutations, categorized into:
- Pathogenic/Likely Pathogenic
- Benign/Likely Benign
- Variants of Uncertain Significance (VUS)

The goal is to prioritize mutations and lay the groundwork for integrating genetic and visual data for multi-modal analysis.

---

## Data Processing
### Source
- **ClinVar VCF Dataset**: Downloaded from [ClinVar VCF GRCh38](https://ftp.ncbi.nlm.nih.gov/pub/clinvar/vcf_GRCh38/).
- ## Download the ClinVar Data File

The `clinvar.vcf.gz` file is too large to store directly in this repository. You can download it from Google Drive using the following link:

[Download ClinVar Data](https://drive.google.com/uc?id=1ZMblL5-bpCWiSCDiQZ80B8K4S6i-fwzg&export=download)

Alternatively, use the following command to download it directly in your terminal or script:

```bash
wget https://drive.google.com/uc?id=1ZMblL5-bpCWiSCDiQZ80B8K4S6i-fwzg&export=download


### Steps
1. **Downloaded and filtered variants**:
   - **Genes**: EGFR, KRAS, ALK
   - **Clinical Significance**: Pathogenic/Likely Pathogenic, Benign/Likely Benign, VUS.
2. **Parsed `INFO` fields** from the VCF file for:
   - `GENEINFO`: Gene names.
   - `CLNSIG`: Clinical significance.
   - `CLNDN`: Disease names.

---

## Results
| **Gene** | **Pathogenic/Likely Pathogenic** | **Benign/Likely Benign** | **VUS** |
|----------|----------------------------------|---------------------------|---------|
| EGFR     | 119                              | 1292                      | 1409    |
| KRAS     | 62                               | 146                       | 198     |
| ALK      | 131                              | 2458                      | 3432    |

---

## Next Steps
1. Focus on `Pathogenic` and `Likely Pathogenic` variants for deeper analysis.
2. Investigate `VUS` variants using predictive tools or additional data.
3. Integrate visual data (e.g., imaging or histopathology) with genetic findings.
4. Build machine learning models to predict pathogenicity.

---

# Repository Structure

multi-modal-genetic-mutation-detector/
├── data/

│   ├── clinvar.vcf                     

**Raw genetic data file from ClinVar**:

│   ├── EGFR_Pathogenic.csv             

**Filtered data for EGFR Pathogenic variants**:

│   ├── KRAS_Benign.csv                 

**Filtered data for KRAS Benign variants**:

│   ├── ALK_VUS.csv                     

**Filtered data for ALK VUS variants**:

│   └── ...                             

**Additional filtered data files**:

├── results/
│   ├── gene_variant_summary.csv        

**Summary of variant counts per gene and classification**:

│   ├── visualizations/

│   │   ├── 
gene_variant_distribution.png 

**Bar plot of variant distribution**:

│   │   └── ...                         

**Other generated plots or figures**:

├── scripts/

│   ├── filter_variants.py              

**Script to parse and filter VCF data**:

│   ├── generate_plots.py               

**Script to generate visualizations**:

│   └── ...                             

**Other Python scripts**:

├── README.md                           

**Project documentation**:

├── requirements.txt                    

**Python dependencies list**:

├── .gitignore                          

**Files and folders to exclude from version control**:


