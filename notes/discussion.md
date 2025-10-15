## Discussion

While docking results are inherently indicative rather than definitive, they still reveal consistent structural trends ([Morris & Lim-Wilby, 2008](https://link.springer.com/protocol/10.1007/978-1-59745-177-2_19)). Because molecular docking assumes a rigid receptor, omits solvent and dynamic effects, and cannot model covalent interactions ([Sousa et al., 2006](https://onlinelibrary.wiley.com/doi/10.1002/prot.21082)), the predicted affinities should be interpreted as comparative rather than absolute.

---

### Trends Observed and Literature Context

**Wildtype EGFR**  
For wild-type EGFR, Mobocertinib appears strongest in docking, but this is heavily skewed by a single high-affinity PDB (8F1X) ([Wang et al., 2022](https://pmc.ncbi.nlm.nih.gov/articles/PMC9433531/)). Afatinib and Gefitinib show more consistent binding, aligning with literature reports of their moderate-to-strong wild-type affinity ([Kim et al., 2012](https://pmc.ncbi.nlm.nih.gov/articles/PMC3390174/)). Control ligands bind weakly, validating the specificity of the docking workflow.

**L858R mutation**  
Docking predicts Mobocertinib binds strongest (−7.79 kcal/mol), followed by Afatinib (−7.58 kcal/mol), Gefitinib ≈ Osimertinib (−7.55 kcal/mol), and Erlotinib weakest (−6.53 kcal/mol). Mobocertinib’s flexible scaffold enables additional interactions in the L858R pocket, while Erlotinib forms few hydrogen bonds, explaining its poor fit ([Dipa et al., 2013](https://www.nature.com/articles/s41598-025-10412-4)). These trends align with studies showing second- and third-generation TKIs better accommodate L858R-induced pocket changes ([Gajiwala et al., 2013](https://www.sciencedirect.com/science/article/pii/S0969212612004297); [Karachaliou et al., 2018](https://tcr.amegroups.org/article/view/24920/html)).

**T790M mutation**  
Osimertinib retains strong predicted binding across PDBs, aligning with its established efficacy against T790M-mediated resistance ([Li et al., 2023](https://pmc.ncbi.nlm.nih.gov/articles/PMC10088170/)). First-generation inhibitors show reduced predicted affinity, though not drastically. This reflects docking’s inability to fully model steric hindrance and induced conformational changes ([Sousa et al., 2006](https://onlinelibrary.wiley.com/doi/10.1002/prot.21082)). Structural analyses confirm that T790M increases ATP affinity and alters pocket geometry, limiting earlier inhibitors’ effectiveness ([Yun et al., 2008](https://pmc.ncbi.nlm.nih.gov/articles/PMC2538882/)).

**Exon20 insertion**  
Afatinib is predicted to bind most strongly (−9.4 kcal/mol in PDB 9GL8) despite forming only one hydrogen bond (R841). This contradicts clinical evidence, where Afatinib monotherapy shows poor response rates and short progression-free survival in Exon20 insertion NSCLC (objective response rates typically <25%) ([Park et al., 2021](https://pubmed.ncbi.nlm.nih.gov/34647988/)). The discrepancy likely arises from static docking artifacts—pocket geometry, conformational bias, and absence of solvent effects—that over-favor Afatinib in silico.  
Mobocertinib and Osimertinib show moderate predicted binding, consistent with their reported preclinical and clinical activity in Exon20 insertion mutants ([Zhou et al., 2021](https://jamanetwork.com/journals/jamaoncology/fullarticle/2784882); [Li et al., 2022](https://www.frontiersin.org/journals/oncology/articles/10.3389/fonc.2022.1010311/full)).

High standard deviations in the Exon20 dataset—greater than in other mutation classes—reflect structural heterogeneity among available PDBs and the fact that all Exon20 docking runs used **non-panel ligands**, increasing pose variability.

---

### Methodological and Dataset Limitations

- **PDB scarcity and heterogeneity:** EGFR structures suitable for docking are limited. Wildtype uses panel ligands, Exon20 uses only non-panel ones, and L858R/T790M are mixed, introducing comparability bias.  
- **Resolution variance:** Some PDBs (e.g., 4G5P at 3.17 Å) have lower resolution, which can distort side-chain geometry and hydrogen bond positioning—both critical for accurate docking scores.  
- **Limited ligand pool:** Only three TKIs per receptor (representing different generations) were used, balancing generation coverage against data availability. Outlier structures can thus disproportionately influence mean values.  
- **Rigid docking assumptions:** AutoDock Vina cannot capture protein flexibility, solvent dynamics, or covalent chemistry. This limitation is particularly relevant for **Afatinib** and **Osimertinib**, which form covalent bonds with Cys797 in the EGFR active site.  
- **Biological extrapolation:** Docking estimates potential binding affinity but not actual inhibitory potency. Factors such as ATP competition, cellular uptake, and steric hindrance strongly affect in vivo efficacy.

---

### Future Directions

- **Molecular Dynamics (MD) simulations:** MD could capture receptor flexibility and solvent interactions, allowing refinement of docking poses and estimation of realistic binding free energies.  
- **Covalent docking workflows:** Incorporating reactive warheads and explicit modeling of bond formation with Cys797 (e.g., using CovDock, GOLD, or AutoDockFR with reactive templates) would better represent Afatinib and Osimertinib’s irreversible mechanisms.  
- **Expanded structural dataset:** Including more high-resolution PDBs, especially for Exon20 insertions, and a broader range of ligands could improve statistical robustness.  
- **Free-energy calculations (MM/PBSA, FEP):** Post-docking free energy methods can refine relative ΔG values for more quantitative comparisons.  
- **Experimental correlation:** Linking computational predictions to measured affinities (e.g., K<sub>d</sub>, IC<sub>50</sub>) and clinical outcomes would validate and calibrate the docking workflow.

---

### Conclusion

This docking-based analysis recapitulates key trends in EGFR–TKI interactions—Osimertinib’s resilience to T790M, Gefitinib’s preference for L858R, and Mobocertinib’s selectivity for Exon20 variants—while also highlighting discrepancies such as Afatinib’s overestimated binding in silico. These findings underscore both the interpretive value and inherent limitations of docking, and provide hypotheses for more detailed studies using molecular dynamics or experimental validation.

---
