## Discussion

While docking results are inherently **indicative** rather than definitive, they still reveal consistent structural trends ([Morris & Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)). Because molecular docking assumes a rigid receptor, omits solvent and dynamic effects, and cannot model covalent interactions ([Sousa et al., 2006](https://onlinelibrary.wiley.com/doi/10.1002/prot.21082)), the predicted affinities should be interpreted as comparative rather than absolute.

---

### Trends Observed and Literature Context

**Wildtype EGFR**  
For wild-type EGFR, Mobocertinib appears strongest in docking, but this is heavily skewed by a single high-affinity PDB (8F1X) ([Wang et al., 2022](https://pmc.ncbi.nlm.nih.gov/articles/PMC9433531/)). Afatinib and Gefitinib show more consistent binding, aligning with literature reports of their moderate-to-strong wild-type affinity ([Kim et al., 2012](https://pmc.ncbi.nlm.nih.gov/articles/PMC3390174/)). Control ligands bind weakly, validating the specificity of the docking workflow.

**L858R mutation**  
Docking predicts Mobocertinib binds strongest (−7.79 kcal/mol), followed by Afatinib (−7.58 kcal/mol), Gefitinib ≈ Osimertinib (−7.55 kcal/mol), and Erlotinib weakest (−6.53 kcal/mol). Mobocertinib’s flexible scaffold enables additional interactions in the L858R pocket, while Erlotinib forms few hydrogen bonds, explaining its poor fit ([Dipa et al., 2013](https://www.nature.com/articles/s41598-025-10412-4)). These trends align with studies showing second- and third-generation TKIs better accommodate L858R-induced pocket changes ([Gajiwala et al., 2013](https://www.sciencedirect.com/science/article/pii/S0969212612004297); [Karachaliou et al., 2018](https://tcr.amegroups.org/article/view/24920/html)).

**T790M mutation**  
Osimertinib retains strong predicted binding across PDBs, aligning with its established efficacy against T790M-mediated resistance ([Li et al., 2023](https://pmc.ncbi.nlm.nih.gov/articles/PMC10088170/)). First-generation inhibitors show reduced predicted affinity, though not drastically. This reflects docking’s inability to fully model steric hindrance and induced conformational changes ([Sousa et al., 2006](https://onlinelibrary.wiley.com/doi/10.1002/prot.21082)). Structural analyses confirm that T790M increases ATP affinity and alters pocket geometry, limiting earlier inhibitors’ effectiveness ([Yun et al., 2008](https://pmc.ncbi.nlm.nih.gov/articles/PMC2538882/)).

**Exon20 insertion**  
Afatinib is predicted to bind most strongly (−9.4 kcal/mol in PDB 9GL8) despite forming only one hydrogen bond (R841). This contradicts clinical evidence, where Afatinib monotherapy shows poor response rates and short progression-free survival in Exon20 insertion NSCLC (objective response rates typically <25%) ([Park et al., 2021](https://pubmed.ncbi.nlm.nih.gov/34647988/)). The discrepancy likely arises from static docking artifacts; pocket geometry, conformational bias, and absence of solvent effects. As a smaller molecule, Afatinib may fit more easily into the Exon20 pocket represented by the selected PDBs. However, these static structures likely do not capture the true conformational flexibility of Exon20 insertions, nor the steric constraints present *in vivo*. As a result, docking may artificially overestimate Afatinib’s binding affinity.

Mobocertinib and Osimertinib show lower predicted binding than Afatinib, despite being more effective clinically against Exon20 insertions ([Bai et al., 2023](https://pubmed.ncbi.nlm.nih.gov/37703723/)). Gefitinib and Erlotinib have the weakest predicted affinities, in line with their poor activity against this mutation ([Wang et al., 2020](https://pmc.ncbi.nlm.nih.gov/articles/PMC8799012/)). The high standard deviations in the Exon20 dataset, which are larger than for other mutation classes, reflect both structural heterogeneity among available PDBs and the use of non-panel ligands, which increases variability in docking poses. Together, these factors likely explain why the predicted binding does not match clinical outcomes and highlight the limitations of static docking for capturing the true conformational constraints of Exon20 insertions.

---

### Methodological and Dataset Limitations

- **PDB scarcity and heterogeneity:** EGFR structures suitable for docking are limited. Wildtype uses panel ligands, Exon20 uses only non-panel ones, and L858R/T790M are mixed, introducing comparability bias.  
- **Resolution variance:** Some PDBs (e.g., 4G5P at 3.17 Å) have lower resolution, which can distort side-chain geometry and hydrogen bond positioning. Both are critical for accurate docking scores ([Morris & Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)).  
- **Limited ligand pool:** Only three TKIs per receptor (representing different generations) were used, balancing generation coverage against data availability. Outlier structures can thus disproportionately influence mean values.  
- **Rigid docking assumptions:** AutoDock Vina cannot capture protein flexibility, solvent dynamics, or covalent chemistry ([Trott & Olson, 2010](https://pubmed.ncbi.nlm.nih.gov/19499576/)). This limitation is particularly relevant for **Afatinib** and **Osimertinib**, which form covalent bonds with C797 in the EGFR active site ([Shi et al., 2022](https://jhoonline.biomedcentral.com/articles/10.1186/s13045-022-01311-6)).  
- **Biological extrapolation:** Docking estimates potential binding affinity but not actual inhibitory potency. Factors such as ATP competition, cellular uptake, and steric hindrance strongly affect *in vivo* efficacy ([Morris & Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)).

---

### Future Directions

- **Molecular Dynamics (MD) simulations:** MD could capture receptor flexibility and solvent interactions, allowing refinement of docking poses and estimation of realistic binding free energies ([AlRawashdeh & Barakat, 2024](https://pubmed.ncbi.nlm.nih.gov/37676596/)).  
- **Covalent docking workflows:** Incorporating reactive warheads and explicit modelling of bond formation with C797 (e.g., using CovDock, GOLD, or AutoDockFR with reactive templates) would better represent Afatinib and Osimertinib’s irreversible mechanisms ([London et al., 2014](https://pubmed.ncbi.nlm.nih.gov/25344815/); [Verdonk et al., 2003](https://pubmed.ncbi.nlm.nih.gov/12910460/); [Bianco et al., 2016](https://pubmed.ncbi.nlm.nih.gov/26103917/)).  
- **Expanded structural dataset:** Including more high-resolution PDBs, especially for Exon20 insertions, and a broader range of ligands could improve statistical robustness.  
- **Free-energy calculations (MM/PBSA, FEP):** Post-docking free energy methods can refine relative ΔG values for more quantitative comparisons ([Kollman, 1993](https://pubs.acs.org/doi/abs/10.1021/cr00023a004)).  
- **Experimental correlation:** Linking computational predictions to measured affinities (e.g., K<sub>d</sub>, IC<sub>50</sub>) and clinical outcomes would validate and calibrate the docking workflow ([Morris & Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)).

---

### Conclusion

This docking-based analysis recapitulates key trends in EGFR–TKI interactions; Osimertinib’s resilience to T790M, Gefitinib’s preference for L858R, and Mobocertinib’s selectivity for Exon20 variants. Concurretnly, it is also highlighting discrepancies such as Afatinib’s overestimated binding *in silico*. These findings underscore both the interpretive value and inherent limitations of docking, and provide hypotheses for more detailed studies using molecular dynamics or experimental validation.

---
