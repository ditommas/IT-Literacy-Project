# 🔬 03 — Molecular Fingerprints

Introduction to molecular fingerprints for A-level students, using Python and
**RDKit** to convert molecules into numerical vectors suitable for machine
learning.

This notebook directly follows the SMILES tutorial — fingerprints are the
bridge between molecular structure and machine learning algorithms.

---

## 📁 Folder Contents

| File | Type | Description |
|------|------|-------------|
| `fingerprints_tutorial.ipynb` | Notebook | Main tutorial covering MACCS and Morgan fingerprints |

> ⚠️ No additional data files are required — all molecules are defined
> directly in the notebook using SMILES strings.

---

## 📖 What You Will Learn

### The Core Problem

Machine learning models cannot read molecular drawings or SMILES strings —
they require **numbers**. A molecular fingerprint solves this by encoding a
molecule as a fixed-length binary vector:

```
Aspirin  → [0, 0, 1, 0, 1, 1, 0, 0, 1, 0, 0, 1, ...]   ← 166 or 512 numbers
Caffeine → [0, 1, 0, 0, 1, 0, 1, 0, 0, 0, 1, 0, ...]
```

Each position represents a chemical feature. A **1** means the feature is
present; a **0** means it is absent.

---

### Two Fingerprint Types Covered

| Fingerprint | Full name | Key idea | Vector length |
|-------------|-----------|----------|---------------|
| **MACCS** | Molecular ACCess System | Fixed checklist of 166 predefined structural questions | 166 bits |
| **Morgan** | Morgan / ECFP | Circular neighbourhood encoding around each atom | 512–2048 bits (configurable) |

**MACCS** works like a checklist:
> "Does the molecule contain a ring? An OH group? A nitrogen atom?"

**Morgan** works like a postcode:
> Each atom is assigned an identifier encoding everything within a set number
> of bonds around it. Two atoms in different molecules with the same local
> environment activate the same bit.

---

### The Morgan Radius Parameter

Increasing the Morgan radius makes fingerprints more specific:

| Radius | What is encoded | Active bits |
|--------|----------------|-------------|
| 1 | Atom + immediate bonds | More (general patterns) |
| 2 | Atom + 2-bond neighbourhood | Medium |
| 3 | Atom + 3-bond neighbourhood | Fewer (highly specific) |

---

### Binary vs Count Morgan Fingerprints

| Variant | What it stores | Best use |
|---------|---------------|----------|
| **Binary** | 1 if a pattern is present, else 0 | Similarity searching |
| **Count** | How many times each pattern appears | Quantitative ML models |

---

### Tanimoto Similarity

Fingerprints enable fast mathematical similarity between molecules using the
**Tanimoto coefficient**:

$$T(A, B) = \frac{|A \cap B|}{|A \cup B|} = \frac{\text{bits active in both}}{\text{bits active in either}}$$

- $T = 1$ → identical molecules
- $T = 0$ → no shared features
- $T > 0.85$ → typically considered similar in drug discovery

---

## 🗂️ Notebook Structure

| Section | Content |
|---------|---------|
| 1 | What is a molecular fingerprint? — motivation and analogy |
| 2 | Imports |
| 3 | MACCS fingerprints — generation, bit string visualisation, comparison across molecules |
| 4 | Building a molecule dataset with pandas |
| 5 | Generating MACCS fingerprints for a full dataset; heatmap visualisation |
| 6 | Morgan fingerprints — binary and count variants; radius effect |
| 7 | Similarity searching with Tanimoto — MACCS vs Morgan ranking comparison |
| 8 | Which fingerprint should you use? — decision guide |
| 9 | Summary, discussion questions, and further reading |

---

## 💬 Discussion Questions

The notebook ends with questions to encourage critical thinking:

1. A SMILES string contains complete structural information. A 166-bit MACCS
   fingerprint does not. What types of information are lost? Does this matter
   for drug discovery?
2. Morgan fingerprints use a hash function that can produce collisions — two
   different patterns mapped to the same bit. How might this affect similarity
   calculations?
3. How does increasing the Morgan radius change similarity scores between
   structurally related drugs?
4. A neural network trained on Morgan fingerprints to predict toxicity learns
   which bit combinations correlate with toxicity — but has no idea what those
   bits mean chemically. Is this a problem?
5. Researchers have developed 3D fingerprints encoding molecular shape. When
   would a 3D fingerprint be more useful than a 2D one?

---

## ⚙️ Requirements

```bash
pip install rdkit pandas numpy matplotlib
```

---

## 🔗 Position in the Workshop

This notebook is the **third tutorial** in the AI Literacy Project series,
building directly on the concepts introduced in:

```
01_house_prices/   → Supervised ML with tabular data
02_smiles_rdkit/   → Molecules as text (SMILES) and molecular properties
03_fingerprints/   → Molecules as numbers (fingerprints)   ← you are here
04_ml_chemistry/   → Training ML models on molecular data
```

---

## 📚 Further Reading

- Rogers & Hahn, Extended-connectivity fingerprints: *J. Chem. Inf. Model.*,
  2010, **50**, 742–754
- Bajusz et al., Why is the Tanimoto index an appropriate choice for
  fingerprint-based similarity calculations: *J. Cheminform.*, 2015, **7**, 20
- RDKit fingerprints guide: https://www.rdkit.org/docs/GettingStartedInPython.html#fingerprinting-and-molecular-similarity
- DeepChem fingerprints tutorial: https://deepchem.io/tutorials/molecular-fingerprints/

---

*Notebook developed for the QMUL AI Literacy Project Taster Day · Department of Chemistry*
