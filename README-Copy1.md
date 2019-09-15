# team-shirin
Database-focused drug discovery and gene therapy for cutaneous neurofibroma

# Project 1: Mining RNASeq for new CNF drug targets

## Abstract
In this project we tried to mine the RNASeq gene expression dataset for possible new drug targets. RNASeq includes a variety of tumor types; we concentrated on CNF. Our strategy was to compare gene expression values between CNF samples and as close as we could get to a control group of normal tissue. We then took the set of genes that appeared "most disrupted" vs. normal, and cross-checked it against Synapese's Drug Target Explorer. We found that a high proportion of this "most disrupted" gene set appeared in the Drug Target Explorer as having known associations with copper. This seems intriguing - while copper is apparently novel in the NF1/CNF context it has a well-established role in many disease processes [HPK] - notably, it appears heavily involved in angiogenesis and tumor formation, likely through a variety of pathways. A number of drugs are used to reduce copper levels (ex. in Wilson's disease), including penicillamine and TM (tetrathiomolybdate); TM has also been investigated for cancer treatment. Perhaps this suggests a direction for drug development that could work on a number of pathways simultaneously, and possibly be synergistic with other drug approaches.

## Introduction
CNF tumors are a common complication of NF1, often in large numbers. They have no treatment other than surgery, which may be impractical. Therefore, finding plausible drug targets would be of interest. It's thought that CNF tumors are heterogenous. Therefore, drugs that target multiple pathways may work more effectively.

## Methods
For full details, see the shirinRNASeq notebook.

We began with the idea of comparing gene expression in CNF vs. "normal" values. We spoke with Sarah Gosline about our idea to compare expression values of "normal" and CNF cells, and she warned that some of the differences seen could be due to cell line effects, since the "normal" cells in RNASeq came from cell lines rather than biopsies. Based on a number of conversation with Ray Mattingly and Sarah, we used the "normal" values for the two cell lines with specimenID 'ipn02.3' and 'ipn97.4' - these were derived from immortalized normal Schwann cells which are thought to be the main drivers for CNF formation.

We took the RNASeq data from CNF samples (33 specimens, 11 individuals) and the two "normal" (Schwann-derived) cell lines and compared the average absolute difference of zScore for each gene (19,098) between the CNF specimens and the average of the two "normal" samples. We sorted the results and took the 100 "most disturbed" genes (highest average absolute difference values). We then cross-checked these top 100 genes against the Drug Target Explorer database.


## Results
A finding that immediately jumped out was the high proportion of "suspect" genes with known interactions with copper. Of the  genes in the suspect set that appeared in the DTE drug target associations database (v2), 23 of 58 (40%) had a known association with copper; of the total of target genes appearing in the database, only 144 of 3735 (4%) had a known association with copper.


## Conclusion/Discussion: 
Perhaps this suggests a direction for drug development that could work on a number of pathways simultaneously, and possibly be synergistic with other drug approaches. Copper is an essential micrometal, and is involved in many fundamental biological processes [HPL]. It's also implicated in a variety of diseases. Of note, there's strong evidence for its role in tumor growth, particularly in the complex process of angiogenesis, likely through a variety of pathways:
(the following quotes are taken from the review above)
- "high serum and tissue levels of copper were found in various human tumors"
- "it has been demonstrated that copper is required for angiogenic process"
- "lowering copper level moderately with a drug such as TM produces strong antiangiogenesis and potent anticancer effects in several rodent models"
- "limiting the biological availability of copper by penicillamine or TM administration slows tumor growth"
Copper chelators such as penicillamine and TM (tetrathiomolybdate) are used in 

Sharad Verma mentioned the possible importance of transdermal delivery for CNF drugs. Interestingly, it appears possible to administer penicillamine transdermally using ultrasound-mediated delivery (sonophoresis) [PHLB].

[HPK] Hordyjewska A, Popiolek L, Kocot J. The many "faces" of copper in medicine and treatment. Biometals. 2014;27(4):611–621. doi:10.1007/s10534-014-9736-5

[PHLB] Polat BE, Hart D, Langer R, Blankschtein D. Ultrasound-mediated transdermal drug delivery: mechanisms, scope, and emerging trends. J Control Release. 2011;152(3):330–348. doi:10.1016/j.jconrel.2011.01.006

## Future work:
- try to replicate the results with another (independent) set of CNF samples
- apply the same approach to other tumor types
- analyze the set of genes found for common pathways and clustering
- test CNF tumors for high copper levels
- in vitro or animal model tests of copper chelators such as penicillamine and TM (tetrathiomolybdate)

## Reproduction
Run the shirinRNASeq notebook.

### Docker

*The Docker image contains <R/jupyter> notebooks of all analyses and the dependencies to run them. *Be sure to note if you need any special credentials to access data for these analyses, **don't package restricted data** in your containers!*

Instructions for running the following notebooks: *be sure to adjust these instructions as necessary! check out https://github.com/Sage-Bionetworks/nf-hackathon-2019 for example containers and instructions*

1. `docker pull <your dockerhub repo>/<this container>` command to pull the image from the DockerHub
2. `docker run <your dockerhub repo>/<this container>` Run the docker image from the master shell script

### Important Resources *: primary data, github repository, Synapse project, dockerfile link etc.*


