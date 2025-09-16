# EGFR TKI Docking Analysis

Docking study of EGFR wildtype and resistance mutations (L858R, T790M, Exon20 insertions) with clinically relevant tyrosine kinase inhibitors (TKIs) and control ligands.  
This repository summarizes results, figures, and discussion of binding affinities obtained using AutoDock Vina.

---

## Background

Epidermal growth factor receptor (EGFR) mutations drive oncogenesis in many cancers, particularly non-small cell lung cancer.  
Targeted inhibitors have been developed, but resistance mutations (e.g., **L858R**, **T790M**, **Exon20 insertions**) complicate treatment.  

This project evaluates binding affinities of representative TKIs against wildtype and mutant EGFR using docking.  
Control ligands (aspirin, caffeine, ibuprofen) were included to benchmark nonspecific binding.

---

## Methods

- **Ligand docking**: AutoDock Vina  
- **Ligands**: Afatinib, Erlotinib, Gefitinib, Mobocertinib, Osimertinib, + controls  
- **Receptor structures (PDBs)**:  
  - **Wildtype**: 4WKQ (Gefitinib), 4G5J (Afatinib), 8F1X (Mobocertinib)  
  - **L858R**: 2ITZ (Gefitinib), 6JWL (Osimertinib), 2ITT (AEE788)  
  - **T790M**: 6JX0 (Osimertinib), 4G5P (Afatinib), 5GMP (XTF-262)  
  - **Exon20**: 4LRM (PD168393), 9GC6 (A1IZ9), 9GL8 (STX-721)  

- **Analysis**: Affinities averaged across available PDBs per receptor.  
- **Visualization**: PyMOL (pocket & ligand binding comparisons).

---

## Results

### Binding Affinity Table
Mean ± SD affinities (kcal/mol):

| EGFR receptor | Afatinib | Aspirin (control) | Caffeine (control) | Erlotinib | Gefitinib | Ibuprofen (control) | Mobocertinib | Osimertinib |
|---------------|----------|--------------------|--------------------|-----------|-----------|----------------------|--------------|-------------|
| Wildtype      | -7.76 ± 0.27 | -5.53 ± 0.12 | -5.18 ± 0.04 | -7.20 ± 0.53 | -7.85 ± 0.40 | -6.28 ± 0.10 | -7.93 ± 0.73 | -7.62 ± 0.37 |
| L858R         | -7.58 ± 0.37 | -5.28 ± 0.21 | -5.05 ± 0.12 | -6.53 ± 0.36 | -7.55 ± 0.29 | -6.14 ± 0.26 | -7.79 ± 0.30 | -7.55 ± 0.24 |
| T790M         | -7.73 ± 0.69 | -5.06 ± 0.35 | -5.16 ± 0.15 | -6.56 ± 0.61 | -7.54 ± 0.67 | -5.98 ± 0.24 | -7.68 ± 0.29 | -7.84 ± 0.64 |
| Exon20        | -9.12 ± 0.33 | -5.93 ± 0.61 | -5.75 ± 0.18 | -7.91 ± 0.42 | -8.93 ± 0.33 | -6.74 ± 0.44 | -8.40 ± 0.75 | -8.69 ± 0.63 |

---

### Heatmap

![Heatmap](results/figures/heatmap.png)  
*Best binder per receptor circled in black.*

---

### Structural Highlights (PyMOL)

**Figure 1 – L858R mutation**  
Comparison of binding in the same pocket:  
- **Osimertinib**: 2 H-bonds (T854), weaker fit  
- **Mobocertinib**: 4 H-bonds (M793, T790, L718), stronger fit  

![L858R pocket](results/figures/l858r.png)

---

**Figure 2 – T790M mutation**  
Clinical relevance of Osimertinib:  
- **Osimertinib**: 2 H-bonds (D855, N842), strong binding  
- **Erlotinib**: no H-bonds, weak fit  

![T790M pocket](results/figures/t790m.png)

---

**Figure 3 – Exon20 insertion**  
- **Afatinib**: very strong docking score (-9.4 kcal/mol) despite only 1 H-bond (R841).  
- **STX-721 (original ligand of 9GL8)** shown for pocket size comparison.  

![Exon20 pocket](results/figures/exon20.png)

---

## Discussion & Limitations

- **Statistical bias**:  
  Wildtype appears to favor mobocertinib, but this is likely skewed by one very strong binding PDB (8F1X).  
- **Exon20 pocket**:  
  Larger surrogate ligands may explain why all TKIs scored surprisingly well. High SD suggests unstable fits.  
- **Covalent inhibitors**:  
  Afatinib and Osimertinib are covalent binders, but Vina only considers non-covalent docking.  
- **Static docking**:  
  Vina does not allow pocket flexibility or induced fit. Real systems adapt; here they cannot.  
- **Next step**:  
  Molecular dynamics (MD) simulations would be needed to confirm stability of binding poses.  

---

## Repository Structure

