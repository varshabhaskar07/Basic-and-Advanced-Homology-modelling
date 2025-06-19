# 🧬 Homology Modelling of THCO5 Protein

## 📌 Overview

This project involves both **basic** and **advanced homology modelling** of the protein **THCO5** (UniProt ID: `Q13769`). The goal is to predict its 3D structure using comparative modelling techniques, validate the models using **DOPE scores**, and compare structural similarities using **RMSD**.

---

## 📁 Project Structure

```
.
├── input.fasta               # Original FASTA sequence of THCO5
├── output.pir                # PIR formatted sequence used for modelling
├── models/                   # Directory containing generated PDB models
│   ├── basic/                # Models from basic homology modelling
│   └── advanced/             # Models from advanced homology modelling
├── scores/                   # DOPE scores for all models
├── alignments/               # Structural alignment and RMSD comparisons
├── plots/                    # DOPE score plots and structural superimpositions
└── README.md                 # Project documentation
```

---

## 🧾 Steps Followed

### 1. Sequence Retrieval

* **Gene Name:** THCO5
* **UniProt ID:** `Q13769`
* Downloaded the FASTA format sequence and converted it to PIR format using Biopython.

```python
from Bio import SeqIO
record = SeqIO.read("input.fasta", "fasta")
SeqIO.write(record, "output.pir", "pir")
```

---

### 2. Template Search

* Used **BLASTp** against the **PDB database**.
* Criteria for template selection:

  * High sequence identity
  * High query coverage
  * Low E-value
  * Experimental 3D structure available
* **Selected templates**:

  * `7ZNL_E`
  * `7APK_E`
  * (Only two templates were found with suitable identity and coverage)

---

### 3. Basic Homology Modelling

* Used **template 7ZNL\_E** to generate **10 models**.
* **Evaluation:** Calculated DOPE score for each model.
* **Best model:** `THCO5.B99990010.pdb` with the lowest DOPE score.

---

### 4. Advanced Homology Modelling

* Used **both templates (7ZNL\_E and 7APK\_E)**.
* Generated **10 models** using advanced alignment.
* **Best model:** `THCO5.B99990006.pdb` (lowest DOPE score).

---

## 📊 Evaluation & Comparison

* **DOPE Score Profile**: Compared the score trends between models from both basic and advanced approaches.
* **RMSD Analysis**:

  * Superimposed structures with original templates.
  * Compared structural deviations using RMSD.
  * Advanced models showed higher RMSD—indicating more deviation but possibly more flexibility.

---

## 📌 Conclusions

* **Basic modelling** gave a model closer to the selected template.
* **Advanced modelling**, despite using more information, introduced more structural variance.
* Best models:

  * **Basic:** `THCO5.B99990010.pdb`
  * **Advanced:** `THCO5.B99990006.pdb`

---

## 📷 Visuals & Plots

* DOPE score plots for:

  * Basic models
  * Advanced models
* RMSD alignment snapshots:

  * Template vs. Basic model
  * Template vs. Advanced model
  * Multi-template alignments

---

## 🛠️ Tools & Libraries

* **Biopython** for sequence parsing
* **BLASTp** for template search
* **MODELLER** for model generation
* **Matplotlib/Seaborn** for plotting DOPE scores
* **PyMOL/Chimera** for RMSD and structural visualization



