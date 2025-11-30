# 🧬 Day 07: DNA Sequence Analysis

## 📚 Contents

1. **Sequence_Identity_Similarity.ipynb** - DNA sequence comparison
2. **Mutation.ipynb** - DNA mutation effects analysis

---

## 📊 Sequence Identity & Similarity

### 🎯 Identity

Measures **exact matches** between DNA sequences.

```python
# Calculate identity between two DNA sequences
matches = sum(1 for a, b in zip(seq1, seq2) if a == b)
identity = (matches / len(seq1)) * 100
```

**Example:**

- `ATGCATAG` vs `ATGAATGG` → 75% identity

---

### 🔬 Similarity

Measures **exact matches** between **protein sequences**.

```python
# Calculate similarity between amino acid sequences
matches = sum(1 for a, b in zip(protein1, protein2) if a == b)
similarity = (matches / len(protein1)) * 100
```

---

## 🧬 DNA to Protein Pipeline

### Step 1️⃣: Complementary Strand

```python
def complementary_strand(dna):
    return dna.translate(str.maketrans("ATCG", "TAGC"))
```

**A** ↔ **T**, **C** ↔ **G**

### Step 2️⃣: DNA to mRNA

```python
def dna_to_mrna(dna):
    return dna.replace("T", "U")
```

Replace **T** with **U**

### Step 3️⃣: Split into Codons

```python
def split_into_codons(mrna):
    return [mrna[i:i+3] for i in range(0, len(mrna), 3)]
```

Group in **3s**: `AUGCGA` → `['AUG', 'CGA']`

### Step 4️⃣: Translate to Amino Acids

```python
amino_acid = "".join(codon_table.get(codon, "?") for codon in codons)
```

Use codon table: `AUG` → `M` (Methionine)

---

## 🧪 Mutations

### 🔄 Substitution

Replace one nucleotide with another.

```python
substitution = dna[:4] + "A" + dna[5:]
# ATGCCG → ATGACG (C→A at position 4)
```

### ➕ Insertion

Add an extra nucleotide.

```python
insertion = dna[:5] + "T" + dna[5:]
# ATGCC → ATGCCT (T inserted)
```

### ➖ Deletion

Remove a nucleotide.

```python
deletion = dna[:4] + dna[5:]
# ATGCCG → ATGCG (C removed)
```

---

## 🔑 Key Formulas

| Metric         | Formula                                     |
| -------------- | ------------------------------------------- |
| **Identity**   | `(matches / total_positions) × 100%`        |
| **Similarity** | `(protein_matches / protein_length) × 100%` |

---

## 💡 Quick Tips

- ✅ **Identity** = DNA level comparison
- ✅ **Similarity** = Protein level comparison
- ✅ Always check sequence lengths match before comparison
- ✅ Mutations can cause frameshift (insertion/deletion) or point mutations (substitution)

---

## 🚀 Usage

```python
# Basic workflow
dna = "ATGGCTGAACTG"
complement = complementary_strand(dna)
mrna = dna_to_mrna(complement)
codons = split_into_codons(mrna)
protein = translate_to_amino_acids(codons)
```

---

**📝 Note:** These notebooks demonstrate fundamental bioinformatics concepts for sequence analysis and mutation impact assessment.
