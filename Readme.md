<h1 align="center">Characterization and predictive role of human-specific genes in Acute Lymphoblastic Leukemia</h1> 

## Authors

Project developed by: 
  * [Andrea Tonina](https://github.com/iamandreatonina)
  * [Gloria Lugoboni](https://github.com/GloriaLugoboni)
  * [Thomas Sirchi](https://github.com/Thokas99)
  * [Lorenzo Santarelli](https://github.com/Lor-Santa)


`All authors contribute equally`

## Overview
- Analyzing data related to Acute Lymphoid Leukemia (ALL)
- Utilizing bioinformatics techniques
- Seeking insights into underlying mechanisms
- `work in progress`

## Dataset
| Dataset    | Origin_Bone_marrow_or_Blood | Cells                     | Number_Samples | N_Healty_sample | N_tumor_sample | Pediatric_Adult |
|------------|-----------------------------|---------------------------|----------------|-----------------|----------------|-----------------|
| GSE84445   | Blood                       | CD4_CD8_T                 | 20             | 20              | 0              | Unknown         |
| GSE133499  | Both                        | All                       | 42             | 0               | 42             | Pediatric       |
| GSE181157  | Both                        | All                       | 173            | 0               | 173            | Pediatric       |
| GSE227832  | Both                        | All                       | 340            | 10              | 330            | Pediatric       |
| Cohort_7_8 | Unknown                     | All                       | 107            | 0               | 107            | Both            |
| GSE139073  | Bone                        | Bone marrow stromal cells | 40             | 40              | 0              | Adult           |
| GSE162562  | Blood                       | All                       | 5              | 5               | 0              | Unknown         |
| GSE115736  | Blood                       | CD4_CD8_T, B              | 18             | 18              | 0              | Unknown         |

## Overview
This project investigates the role of human-specific genes in Acute Lymphoblastic Leukemia (ALL). By leveraging advanced quantitative methodologies, we aim to extend the current understanding of these genes and their association with ALL. This repository contains all relevant data, methods, and tools used in our study.

## Motivation
### Background
Humans and chimpanzees diverged approximately 6 million years ago. This evolutionary split has led to rapid genetic alterations in the human lineage, resulting in significant differences, particularly in diet, immune function, and anatomy. These unique genetic features, termed ‘human-specific’ genes, are not entirely understood. Many studies have aimed to identify these genes and understand their association with human-specific diseases.

### Acute Lymphoblastic Leukemia (ALL)
ALL is the most common type of leukemia in children, accounting for 80% of pediatric leukemia cases. It involves the malignant transformation of lymphoid progenitor cells, leading to abnormal proliferation and differentiation. This disease is closely linked to genetic aberrations, including complex chromosomal rearrangements.

### Study Objective
This study aims to characterize human-specific genes associated with ALL and evaluate their predictive role. By analyzing differential gene expression and performing enrichment analysis, we seek to identify key human-specific genes involved in ALL and develop classifiers to predict tumor subtypes.

## Methods
### Data Collection
We utilized 8 comprehensive databases ( more to come, `work in progress` ) from the Gene Expression Omnibus (GEO), which include mRNA expression profiles derived from bone marrow and blood cells of 794 patients. These patients' samples were categorized into tumoral ALL samples and controls. Metadata allowed further classification based on age (adult and pediatric) and tumor subtype (B, T, PreB, and PreT).

### Data Preprocessing
- **Batch Correction:** Combat-Seq from the sva package in R was employed to correct batch effects in the count matrices.
- **Normalization:** Data normalization was performed using the Trimmed Mean of M-values (TMM) method to ensure comparability across samples.

### Differential Gene Expression Analysis
- **Tools Used:** The EdgeR package in R was used to identify differentially expressed genes (DEGs).
- **Filtering Criteria:** DEGs were filtered using a p-value threshold of < 0.01. Significant genes were determined by setting a ±1.5 threshold on log-transformed fold changes.

### Extraction of Human-Specific Genes
A reference list of human-specific genes, derived from existing literature, was used to extract relevant DEGs from our dataset.

### Enrichment and Pathway Analysis
- **Functional Enrichment:** Enrichment analysis was performed using the clusterProfiler and EnrichR packages in R. The analysis focused on the Biological Process (BP) sub-ontology.
- **Pathway Analysis:** WikiPathway was utilized to perform pathway analysis, identifying key pathways involving the identified DEGs.

### Classification and Predictive Modeling
- **Methodology:** Various classification methods were implemented using R libraries, including ensemble methods, non-parametric, and CPU-based deep learning.
- **Training and Validation:** The classifiers were trained on differentially expressed human-specific genes. A three-fold cross-validation with two repeats was used, employing the ADASYN algorithm for balanced sampling.
- **Hyperparameter Tuning:** Hyperparameters were tuned using Latin hypercube sampling followed by Simulated Annealing, executed for 25 search iterations.
- **Model Evaluation:** Post-classification, variable importance was extracted from the models, and features were ranked.

## Results
### Differential Gene Expression
We identified numerous human-specific genes that characterize ALL and its various subtypes (B, T, PreB, and PreT). The differential expression patterns highlighted the involvement of these genes in critical biological processes such as immune response deregulation, differentiation, and splicing.

### Enrichment Analysis
Enrichment analysis revealed significant involvement of human-specific genes in pathways related to cancer. The deregulation of immune response and cell differentiation processes were particularly prominent.

### Predictive Modeling
We developed a consensus classifier capable of accurately associating unknown data with specific tumor subtypes. The classifier demonstrated robust performance with:
- **Mean Balanced accuracy:** Approximately 0.89%
- **F Mean Score:** Approximately  0.81
- **Kappa Mean Score:** Approximately 0.75
<div align="center">
  <img src="Code/ML/HS/line_plot_Metrics.png" alt="drawing" width="400"/>
</div>

### Key Genes Identified
Among the human-specific genes with high importance in our models, we identified:
- **EBF1:** A gene related to signal transduction in leukemia.
- **MYO7B:** A known proto-oncogenic driver.
- **RAB6C:** A member of the RAS oncogene family.
<div align="center">
  <img src="Code/ML/HS/big_imp_plot_2.png" alt="drawing" width="400"/>
</div>

### Conclusion
This study successfully highlights a set of human-specific genes associated with ALL, providing a basis for patient characterization by age and subtype. The developed classifier effectively predicts tumor subtypes in unknown samples, demonstrating high accuracy. Identifying significant human-specific genes offers potential biomarkers for ALL subtypes, aiding in targeted therapies and personalized medicine approaches.

## Repository Contents
- **[data](data):** Includes the study's expression profiles and associated metadata.
- **[Code](Code):** Contains R scripts for data preprocessing, differential expression analysis, enrichment analysis, and classification.

## Supplementary Information
For detailed information on the methodologies and results, please take a look at our future publication (`work in progress`).

## License
This project is licensed under the MIT License. Please take a look at the [LICENSE](LICENSE) file for more details.

## Contact
For any questions or comments, please open an issue on this repository or contact the authors via email.

---
<p align="center">
  <img src="Images/logos/cibio.jpg" alt="Image 1" width="150" />
  <img src="Images/logos/disi.jpg" alt="Image 2" width="150" />
  <img src="Images/logos/imem.png" alt="Image 3" width="150" />
  <img src="Images/logos/amd.png" alt="Image 4" width="150" />
</p>
