## Discussion

While docking results are inherently **indicative** rather than definitive, they nonetheless reveal consistent structural trends. Molecular docking assumes a rigid receptor, omits solvent and dynamic effects, and cannot model covalent interactions, so predicted affinities should be interpreted as comparative rather than absolute ([Morris and Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19); [Sousa et al., 2006](https://onlinelibrary.wiley.com/doi/10.1002/prot.21082)).

---

### Trends Observed and Literature Context

**Wildtype EGFR**  
For wildtype EGFR, Mobocertinib appears strongest in docking, although this result is heavily skewed by a single high-affinity PDB structure, 8F1X ([Wang et al., 2022](https://pmc.ncbi.nlm.nih.gov/articles/PMC9433531/)). Afatinib and Gefitinib show more consistent binding, in line with literature reports of moderate to strong wildtype affinity ([Kim et al., 2012](https://pmc.ncbi.nlm.nih.gov/articles/PMC3390174/)). Control ligands bind weakly, validating the specificity of the docking workflow.

**L858R mutation**  
Docking predicts Mobocertinib binds most strongly, followed by Afatinib, Gefitinib and Osimertinib at similar values, with Erlotinib showing the weakest predicted binding. Mobocertinib’s flexible scaffold allows additional interactions in the L858R pocket, while Erlotinib forms few hydrogen bonds, explaining its poor fit ([Dipa et al., 2013](https://www.nature.com/articles/s41598-025-10412-4)). These trends are consistent with studies showing that second- and third-generation TKIs better accommodate the structural changes induced by L858R ([Gajiwala et al., 2013](https://www.sciencedirect.com/science/article/pii/S0969212612004297); [Karachaliou et al., 2018](https://tcr.amegroups.org/article/view/24920/html)).

**T790M mutation**  
Osimertinib retains strong predicted binding across PDBs, consistent with its clinical efficacy against T790M-mediated resistance ([Li et al., 2023](https://pmc.ncbi.nlm.nih.gov/articles/PMC10088170/)). First-generation inhibitors show reduced predicted affinity, although not drastically. This likely reflects the inability of rigid docking to fully capture steric hindrance and induced conformational changes ([Sousa et al., 2006](https://onlinelibrary.wiley.com/doi/10.1002/prot.21082)). Structural analyses confirm that T790M increases ATP affinity and alters pocket geometry, reducing the effectiveness of earlier inhibitors ([Yun et al., 2008](https://pmc.ncbi.nlm.nih.gov/articles/PMC2538882/)).

**Exon20 insertion**  
Afatinib is predicted to bind most strongly despite forming only a single hydrogen bond with R841. This contradicts clinical evidence, where Afatinib monotherapy produces poor response rates and short progression-free survival in Exon20 insertion NSCLC, with objective response rates typically below 25 per cent ([Park et al., 2021](https://pubmed.ncbi.nlm.nih.gov/34647988/)). The discrepancy is likely a result of static docking artifacts, including the influence of pocket geometry, conformational bias, and absence of solvent effects. As a smaller molecule, Afatinib may fit more easily into the Exon20 pocket represented by the selected PDBs, but these static structures do not capture the full conformational flexibility of Exon20 insertions nor the steric constraints present *in vivo*. Consequently, docking may overestimate Afatinib’s binding affinity.

Mobocertinib and Osimertinib show lower predicted binding than Afatinib, despite their greater clinical effectiveness against Exon20 insertions ([Bai et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37703723/)). Gefitinib and Erlotinib exhibit the weakest predicted affinities, reflecting their poor activity against this mutation ([Wang et al., 2020](https://pmc.ncbi.nlm.nih.gov/articles/PMC8799012/)). High standard deviations in the Exon20 dataset, larger than those observed for other mutation classes, reflect both structural heterogeneity among available PDBs and the use of non-panel ligands, which increases variability in docking poses. Taken together, these factors likely explain why predicted binding does not match clinical outcomes and highlight the limitations of static docking for this mutation class.

---

### Methodological and Dataset Limitations

Structures suitable for docking are limited, with wild-type EGFR using panel ligands, Exon20 only non-panel ligands, and L858R and T790M a mixture, introducing comparability bias. Some PDBs have lower resolution (e.g., 4G5P at 3.17 Å), which can distort side-chain geometry and hydrogen bond positions, both critical for accurate docking scores ([Morris and Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)). The ligand pool is also limited, with only three TKIs per receptor included to balance generational coverage against data availability, meaning outlier structures may disproportionately influence mean values. Additionally, AutoDock Vina cannot capture protein flexibility, solvent dynamics, or covalent chemistry ([Trott and Olson, 2010](https://pubmed.ncbi.nlm.nih.gov/19499576/)), a limitation particularly relevant for Afatinib and Osimertinib, which form covalent bonds with C797 in the EGFR active site ([Shi et al., 2022](https://jhoonline.biomedcentral.com/articles/10.1186/s13045-022-01311-6)). Docking predicts potential binding affinities but not actual inhibitory potency. Factors such as ATP competition, cellular uptake, and steric hindrance strongly affect *in vivo* efficacy ([Morris and Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)).

---

### Future Directions

Molecular dynamics simulations could capture receptor flexibility and solvent interactions, refining docking poses and enabling more realistic estimation of binding free energies ([AlRawashdeh and Barakat, 2024](https://pubmed.ncbi.nlm.nih.gov/37676596/)). Covalent docking workflows incorporating reactive warheads and explicit modelling of bond formation with C797, using tools such as CovDock, GOLD, or AutoDockFR, would better represent the irreversible mechanisms of Afatinib and Osimertinib ([London et al., 2014](https://pubmed.ncbi.nlm.nih.gov/25344815/); [Verdonk et al., 2003](https://pubmed.ncbi.nlm.nih.gov/12910460/); [Bianco et al., 2016](https://pubmed.ncbi.nlm.nih.gov/26103917/)). Expanding the structural dataset to include more high-resolution PDBs, particularly for Exon20 insertions, and a broader range of ligands would improve statistical robustness. Post-docking free energy calculations, using MM/PBSA or FEP, could refine relative binding energies for quantitative comparisons ([Kollman, 1993](https://pubs.acs.org/doi/abs/10.1021/cr00023a004)). Finally, linking computational predictions to experimental measurements such as K<sub>d</sub> or IC<sub>50</sub> and to clinical outcomes would validate and calibrate the docking workflow ([Morris and Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)).

---

### Conclusion

This docking-based analysis captures key trends in EGFR–TKI interactions, including Osimertinib’s resilience to T790M, Gefitinib’s preference for L858R, and Mobocertinib’s selectivity for Exon20 variants. Concurrently, it highlights discrepancies such as Afatinib’s overestimated binding *in silico*. These results underscore both the interpretive value and inherent limitations of docking and provide hypotheses for more detailed studies using molecular dynamics or experimental validation.

---
