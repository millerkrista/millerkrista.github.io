---
layout: default
title: APHL Annual Conference 2026
parent: Posters & Presentations
nav_order: 1
---

[Download poster PDF here](https://github.com/millerkrista/millerkrista.github.io/blob/main/assets/APHL%20AC26%20Poster.pdf)

![APHL 2026 Annual Conference Poster](https://raw.githubusercontent.com/millerkrista/millerkrista.github.io/main/assets/APHL_AC26_poster.png)

# Supplementary Figures
**Supplementary Table 1**. floc and PopPUNK sensitivity and specificity for carbapenem-resistant *Klebsiella pneumoniae*

| Method | Average Sensitivity | Average Specificity |
|---|---|---|
| floc | 1 | 0.961581971 |
| PopPUNK | 1 | 0.027977687 |
| PopPUNK+PopPIPE | 1 | 0.916195334 |


**Supplementary Table 2**. Further Work Since Poster Creation, PopPUNK+PopPIPE misclustering likely due to custom database

In further research to determine why PopPUNK is incorrectly separating genetically related isolates from each other (see poster Figure 3), we looked at output data from a PopPUNK+PopPIPE workflow run on our CRAB data that did not create a custom database. Instead, the PopPUNK reference database for *Acinetobacter baumannii* was utilized. Below are the sensitivity and specificity scores for that workflow, as well as floc. Results showed that this output was relatively equivalent to floc. Ultimately, we have decided to focus on floc moving forward because ...

| Method | Average Sensitivity | Average Specificity |
|---|---|---|
| floc | 1 | 0.8901 |
| PopPUNK+PopPIPE (RefDB) | 1 | 0.9035 |

---
# Supplementary Methods
## QC and Genome Assembly
We ran all reads through the CDC/PHoeNIx pipeline, version 2.1.1, to obtain quality control metrics and genome assemblies for each CRAB isolate.

## PopPUNK

### Database Creation

1. Created a custom database of 645 CRAB isolates using poppunk create-db.
2. Fit a Bayesian Gaussian Mixture Model to the database using poppunk fit-model bgmm.

### Without PopPIPE

1. Once the database was created, we queried with another 29 CRAB isolates using poppunk_assign.
2. Created visualizations using poppunk_visualise with the microreact flag.

### With PopPIPE

1. Once the database was created, we ran the PopPIPE workflow on the database.
2. Queried the database with another 29 CRAB isolates using poppunk_assign.
3. Ran PopPIPE workflow to get subcluster identities for the 29 CRAB isolates.
 
### Notes
PopPUNK calculates pairwise distances between sequences across a range of k-mer lengths. By utilizing multiple k-mer lengths, PopPUNK is able to estimate both core and accessory gene distances. PopPUNK's cluster boundaries are determined by the Bayesian Gaussian mixture model fit. Therefore, a poor model fit can lead to inaccurate cluster assignment.


## floc

### Database Creation, Query, and Visualization
1. Sketched 645 CRAB isolates to create a database. Used k-mer size of 31 and scaled value of 100.
2. Queried the database with another 29 CRAB isolates.
3. Ran distance output through custom python script (using BioPython Phylo) to obtain neighbor-joining trees.

### Notes
floc estimates pairwise genetic distances between sequences using the sourmash k-mer containment method. This is a single k-mer length of 31 and thereby produces a single distance metric for each pair that combines all sources of genomic variation. floc assigns genomes to clusters using a fixed distance threshold, assigning genomes to a cluster if they fall below the threshold or founding a new cluster otherwise. 

## Dryad
Once we had clustering outputs from PopPUNK and floc, we noticed that floc cluster 5 (floc's largest cluster output) and PopPUNK+PopPIPE strain 2 contained similar DCLS cluster IDs. We decided to run genome assemblies belonging to floc cluster 5 and PopPUNK strain 2 through Dryad, a DCLS validated reference-based SNP calling pipeline (workflow pictured below). We wanted to see the SNP ranges of cluster 5 and strain 2, as well as the tree topology on Dryad trees compared to PopPUNK+PopPIPE and floc trees.

![Dryad Workflow Image](https://raw.githubusercontent.com/millerkrista/millerkrista.github.io/main/assets/Dryad_workflow.png)

## Sensitivity and Specificity
Sensitivity was calculated as (true positives) / (true positives + false negatives).
Specificity was calculated as (true negatives) / (true negatives + false positives). We calculated sensitivity and specificity for each DCLS cluster, then averaged across all DCLS clusters according to each clustering method (floc or PopPUNK).
- **True positives:** isolates belonging to the same DCLS cluster assigned to the same floc/PopPUNK cluster.
- **False negatives:** isolates belonging to the same DCLS cluster assigned to different floc/PopPUNK clusters.
- **True negatives:** isolates belonging to different DCLS clusters assigned to different floc/PopPUNK clusters.
- **False positives:** isolates belonging to different DCLS clusters assigned to the same floc/PopPUNK cluster.
  
---
# References
Argimón S, Abudahab K, Goater RJE, et al. Microreact: visualizing and sharing data for genomic epidemiology and phylogeography. *Microb Genom.* 2016;2(11):e000093. doi:10.1099/mgen.0.000093

Created with BioRender.com

Hagey JV, Vlachos N, Kent AG, et al. CDCgov/phoenix: v2.2.0. Zenodo. [https://doi.org/10.5281/zenodo.8147510](https://doi.org/10.5281/zenodo.8147510)

Johnson J. 2025. floc. [https://github.com/DOH-JDJ0303/floc](https://github.com/DOH-JDJ0303/floc)

Lees JA, Harris SR, Tonkin-Hill G, et al. Fast and flexible bacterial genomic epidemiology with PopPUNK. *Genome Res.* 2019;29(2):304-316. doi:10.1101/gr.241455.118


# Acknowledgements
This work was supported by the Association of Public Health Laboratories (APHL) and Centers for Disease Control and Prevention (CDC) Public Health Laboratory Fellowship Program. We would like to thank the bioinformaticians at DCLS for mentorship and technical advice - Alexandra Lorentz, PhD; Logan Fink, MS; Rachael St. Jacques, MS; Molly Creighton, MS; and Gretchen Cote, MS. We would also like to thank the Sequencing and Bioinformatics Group at DCLS for their assistance with data processing and sequencing and group manager, Mary Toothman, for keeping everything moving forward. Special thanks also goes to Jared Johnson, PhD of the Washington State Department of Health for technical guidance.

