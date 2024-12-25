# Multi-Modal Genetic Mutation Detector

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
- **TCIA Metadata and Diagnosis Files**: Downloaded from:
  - [LIDC-IDRI Metadata](https://www.cancerimagingarchive.net/wp-content/uploads/LIDC-IDRI_MetaData.csv)
  - [TCIA Diagnosis Data](https://www.cancerimagingarchive.net/wp-content/uploads/tcia-diagnosis-data-2012-04-20.xls)

---

### Steps
1. **Downloaded and filtered variants**:
   - **Genes**: EGFR, KRAS, ALK
   - **Clinical Significance**: Pathogenic/Likely Pathogenic, Benign/Likely Benign, VUS.
2. **Parsed `INFO` fields** from the VCF file for:
   - `GENEINFO`: Gene names.
   - `CLNSIG`: Clinical significance.
   - `CLNDN`: Disease names.
3. **Automated File Downloads**:
   - Created a reusable function to download and process CSV, Excel, JSON, and legacy Excel (`.xls`) files programmatically.
   - Example usage:
     ```python
     from utils import download_and_load_file

     # Download and load CSV file
     url_csv = "https://www.cancerimagingarchive.net/wp-content/uploads/LIDC-IDRI_MetaData.csv"
     save_path_csv = "/content/LIDC-IDRI_MetaData.csv"
     metadata_csv = download_and_load_file(url_csv, save_path_csv, file_type="csv")

     # Download and load XLS file
     url_xls = "https://www.cancerimagingarchive.net/wp-content/uploads/tcia-diagnosis-data-2012-04-20.xls"
     save_path_xls = "/content/tcia-diagnosis-data-2012-04-20.xls"
     metadata_xls = download_and_load_file(url_xls, save_path_xls, file_type="xls")
     ```

4. **Analyzed Relationships Between Nodules and Patients**:
   - Investigated relationships in the LIDC-IDRI nodule count data (e.g., total nodules, size-specific nodules).
   - Key Findings:
     - Strong correlations between nodule sizes and counts.

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
│   ├── LIDC-IDRI_MetaData.csv          
│   ├── tcia-diagnosis-data-2012-04-20.xls
│   ├── EGFR_Pathogenic.csv             
│   ├── KRAS_Benign.csv                 
│   ├── ALK_VUS.csv                     
│   └── ...                             
├── results/
│   ├── gene_variant_summary.csv        
│   ├── visualizations/
│   │   ├── gene_variant_distribution.png
│   │   └── ...                         
├── scripts/
│   ├── filter_variants.py              
│   ├── generate_plots.py               
│   ├── download_and_load_file.py       
│   └── ...                             
├── README.md                           
├── requirements.txt                    
├── .gitignore                          

---

## License
This project is licensed under the MIT License. See the LICENSE file for details.
