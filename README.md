# This tool maps protein sequences from a Genome-scale metabolic model (GEM) to the coding sequences of a reference genome using BLASTp.

# Licensing
This software is Copyright (c) 2026. All rights reserved.

Academic/Education: Free for use.

Commercial: Prohibited without an explicit license from the author.

Collaboration: Academic researchers are prohibited from using this code in collaborative research with commercial companies.

Please see the LICENSE file for the full terms and disclaimer of warranty.


## Open in Google Colab

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/MeMoModelling/proteinSeqMapping/blob/main/protein_seq_mapping.ipynb)

## How to use

### What you need
- A Google account
- Your **model protein FASTA** (`.faa`) — protein sequences from your metabolic model
- Your **NCBI protein FASTA** (`.faa`) — protein sequences downloaded from NCBI for the same species

### Steps

**1. Open the notebook**

Click the **Open in Colab** button above. The notebook will open in your browser — no installation needed.

**2. Run all cells**

Go to **Runtime → Run all** in the top menu.

**3. Upload your FASTA files**

When prompted, upload your files:
- First: your **query FASTA** (model protein sequences)
- Second: your **database FASTA** (NCBI protein sequences)

**4. Wait for BLAST to finish**

This may take several minutes depending on the size of your files.

**5. Download the output CSV**

When complete, find the output file in the **Files panel on the left** (📁). Right-click it and select **Download**.

The file will be named `<species>_protein_id_mapping.csv`.

**6. Upload to the pipeline**

Upload the CSV to **Step 2** of the Universal Metabolic Community Pipeline.

---

## Processing multiple species

Each Google account can only run one Colab session at a time. To process multiple species:
- Run the notebook once per species — download the CSV after each run
- To run species in parallel, use a different Google account for each species
- Upload all CSVs together in Step 2 of the pipeline

---

## Output format

| Column | Description |
|---|---|
| `identifier_query` | Model protein/gene ID |
| `identifier_db` | Matched NCBI protein accession |

---

## Filtering criteria

Only matches passing all of the following thresholds are retained:

| Criterion | Threshold |
|---|---|
| Sequence identity | ≥ 95% |
| Gap openings | = 0 |
| Mismatches | ≤ 1 |
| Query coverage | ≥ 85% |
| Subject coverage | ≥ 85% |
