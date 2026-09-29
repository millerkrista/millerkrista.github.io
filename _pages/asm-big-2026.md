---
layout: default
title: ASM BIG Conference 2026
parent: Posters & Presentations
nav_order: 1
---

[Download poster PDF here](https://github.com/millerkrista/millerkrista.github.io/blob/main/assets/ASM%20BIG%20poster.pdf)

![ASM BIG 2026 Poster](https://raw.githubusercontent.com/millerkrista/millerkrista.github.io/main/assets/ASMBIG2026.png)

---

# Supplementary Methods

## QC and Genome Assembly
We ran all reads through the CDC/PHoeNIx pipeline, version 2.3.2, to obtain quality control metrics and genome assemblies for each isolate. 
We found that PHoeNIx v2.3.2 created genome assemblies that were more accurate and more compatible with BigBacter than PHoeNIx v2.1.1. 


## Current DCLS Methods for Cluster Detection
After sequencing and PHoeNIx quality control, data is uploaded to NCBI Pathogen Detection.
NCBI Pathogen Detection will then send an alert if/when an isolate has matched with a cluster.
DCLS scientists then confirm this cluster by running any/all Virginia isolates from that cluster through a species-specific SNP calling pipeline.
Carbapenem-resistant *Klebsiella pneumoniae* and *Acinetobacter baumannii* would both be run through Dryad. *Streptococcus pyogenes* would be run through Foushee. *Neisseria meningitidis* would be referred to CDC to be run through BMGAP.
Dryad is a DCLS-validated whole-genome reference-based SNP calling pipeline (workflow pictured below). 

![Dryad Workflow Image](https://raw.githubusercontent.com/millerkrista/millerkrista.github.io/main/assets/Dryad_workflow.png)


Foushee is a DCLS-validated reference-free SNP calling pipeline that includes an emm-typing tool (workflow pictured below).

![Foushee Workflow Image](https://raw.githubusercontent.com/millerkrista/millerkrista.github.io/main/assets/foushee.png)

## DCLS Cluster Definitions
For carbapenem-resistant *Klebsiella pneumoniae* and *Acinetobacter baumannii*, DCLS clusters were defined from DCLS cluster IDs that had been previously assigned to groups of related isolates. There were 10 DCLS clusters for *K. pneumoniae* and 37 DCLS clusters for *Acinetobacter baumannii*. For *Neisseria meningitidis*, DCLS clusters were defined from a combination of VDH-provided outbreak code, sequence type, serogroup, and clonal complex (e.g. Outbreak1_ST1466_Y_CC174). This resulted in 23 DCLS clusters for *N. meningitidis*, some of which were missing an outbreak code, serogroup, or clonal complex information. DCLS clusters for *Streptococcus pyogenes* were defined similarly, from a combination of VDH-provided outbreak code, sequence type, and emm-type (e.g. Outbreak1_ST101_EMM89). This resulted in 87 DCLS clusters for *S. pyogenes*, some of which were missing an outbreak code. Once DCLS clusters were defined, sensitivity and specificity were calculated both on the cluster level and the partition (subcluster) level as shown below.

## Sensitivity and Specificity
Sensitivity was calculated as (true positives) / (true positives + false negatives).
Specificity was calculated as (true negatives) / (true negatives + false positives). 
We calculated sensitivity and specificity for each DCLS cluster, then took the average across all DCLS clusters for each species to see how BigBacter performed.
- **True positives:** isolates belonging to the same DCLS cluster assigned to the same BigBacter cluster/partition.
- **False negatives:** isolates belonging to the same DCLS cluster assigned to different BigBacter clusters/partitions.
- **True negatives:** isolates belonging to different DCLS clusters assigned to different BigBacter clusters/partitions.
- **False positives:** isolates belonging to different DCLS clusters assigned to the same BigBacter cluster/partition.

---
# Supplementary Discussion
## Potential New Clusters Identified by BigBacter
Coming into the analysis, 115 *Klebsiella pneumoniae* and 310 *Acinetobacter baumannii* isolates did not have known genetic relationships with other isolates. 
Of these, 57 *K. pneumoniae* and 287 *A. baumannii* isolates were grouped into clusters with at least one other isolate, indicating that there might be a genetic relationship that previous DCLS methods did not identify. These clusters will require further investigation to determine if they are truly closely related.

---
# References
NW-PaGe. BigBacter v2.0.0. https://github.com/NW-PaGe/bigbacter.

Hagey JV, Vlachos N, Kent AG, et al. CDCgov/phoenix: v2.2.0. Zenodo. [https://doi.org/10.5281/zenodo.8147510](https://doi.org/10.5281/zenodo.8147510)

Created with BioRender.com


# Acknowledgements
This work was supported by the Public Health Laboratory Fellowship Program: an APHL-CDC Initiative. The fellowship assignment was supported by Cooperative Agreement Number NU60OE000104 (CFDA No. 93.322), funded by the Centers for Disease Control and Prevention. This publication’s contents are solely the responsibility of the authors and do not necessarily represent the official views of the Centers for Disease Control and Prevention, the Department of Health and Human Services, or the Association of Public Health Laboratories and member laboratories. The fellowship assignment was 100% funded with federal funds from a federal program of $120,402,978. 

We would like to thank the bioinformaticians at the Virginia Division of Consolidated Laboratory Services for mentorship and technical advice - Alexandra Lorentz, PhD; Logan Fink, MS; Rachael St. Jacques, MS; Molly Creighton, MS; and Gretchen Cote, MS. We would also like to thank the Sequencing and Bioinformatics Group at DCLS for their assistance with data processing and sequencing and group manager, Mary Toothman, for keeping everything moving forward. Special thanks also goes to Jared Johnson, PhD of the Washington State Department of Health for technical guidance.

