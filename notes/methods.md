# Methods

This document outlines the workflow for EGFR-TKI docking analysis, including protein and ligand preparation, docking procedure, and data analysis.

---

## 1. Protein Fetching

EGFR structures of wildtype and clinically relevant mutations (L858R, T790M, Exon20 insertion) were collected from the Protein Data Bank (PDB). An attempt was made to include at least one ligand-bound structure per inhibitor generation to provide structural diversity. However, due to limited availability of co-crystallised structures, full coverage across all generations was not always possible.

**Wildtype:**
- 4WKQ (Gefitinib)
- 4G5J (Afatinib)
- 8F1X (Mobocertinib)

**L858R:**
- 2ITZ (Gefitinib)
- 6JWL (Osimertinib)
- 2ITT (AEE788) – provides a pocket conformation representative of second-generation TKIs.

**T790M:**
- 6JX0 (Osimertinib)
- 4G5P (Afatinib)
- 5GMP (XTF-262) – surrogate for first-generation TKIs.

**Exon20 Insertion:**
- 4LRM (PD168393) – first-generation reference
- 9GC6 (A1IZ9) – second/third-generation surrogate
- 9GL8 (STX-721) – captures mutant-induced pocket geometry

Proteins were downloaded as `.pdb` or `.cif` files and converted to `.pdb` using PyMOL for consistency.

---

## 2. Ligand Preparation

**Active Ligands (TKIs):** Gefitinib, Erlotinib, Afatinib, Mobocertinib, Osimertinib

**Control Ligands:** Aspirin, Ibuprofen, Caffeine

Ligands were retrieved from ChEMBL or manually sourced from PubChem. Canonical SMILES were read into Python, duplicates removed, and 3D structures generated using RDKit. Hydrogens were added, and torsions and charges were prepared using **Meeko**. Each ligand was saved as a `.pdbqt` file ready for docking. 3D conformer generation used the ETKDG method in **RDKit**; embeddings were generated without a fixed random seed to ensure compatibility across environments.

---

## 3. Protein Preparation

- Water molecules, ions, and bound ligands were removed using **PyMOL**.
- Receptors were converted to `.pdbqt` using **MGLTools** for AutoDock Vina docking.
- Docking boxes were defined using **PyMOL**.

---

## 4. Docking

Docking was performed using **AutoDock Vina 1.2.7**:

- Receptor `.pdbqt` files and ligand `.pdbqt` files were used.
- Grid boxes were centered on the original ligand binding sites.
- Exhaustiveness: 8
- Number of modes: 1
- Docking outputs were saved in the `docking_results` folder.

---

## 5. Analysis

- Affinities extracted from Vina log files.
- Average and standard deviation were calculated per mutation class.
- Heatmaps and tables highlight the best binding ligand per receptor.
- PDBQT docking poses visualised in **PyMOL**, including hydrogen bond analysis.

---

## 6. Notes on Interpretation

- Docking results are **indicative** and do not account for receptor flexibility or covalent binding.
- High standard deviations may indicate PDB-specific bias.
- MD simulations would be required for more accurate, dynamic binding predictions.

---

## 7. References
All software executables were obtained from official sources and used without modification.
1. RDKit: RDKit: Open-source cheminformatics; http://www.rdkit.org  
2. Meeko: Meeko: Ligand Preparation Tool; https://github.com/forlilab/meeko  
3. AutoDock Vina: Trott, O., Olson, A. J. AutoDock Vina: improving the speed and accuracy of docking with a new scoring function. *J Comput Chem* 2010, 31, 455–461.  
4. PyMOL: Schrödinger, LLC. PyMOL. https://pymol.org  
5. MGLTools: Morris et al., AutoDockTools, 2009.  
6. Protein Data Bank (PDB): Berman, H. M., et al. The Protein Data Bank. *Nucleic Acids Res* 2000, 28, 235–242. https://www.rcsb.org  
7. ChEMBL Database: Mendez, D., et al. ChEMBL: towards direct deposition of bioassay data. *Nucleic Acids Res* 2019, 47, D930–D940. https://www.ebi.ac.uk/chembl/
