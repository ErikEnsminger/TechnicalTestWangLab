# TechnicalTestWangLab

## Description

This TechnicalTestWangLab repository aims to classify DNase1 hypersensitivity site (DHS) sequences from Meuleman et al. using a pre-trained Large Language Model (LLM) on DNA sequences. The current analysis focuses on classifying sequences from 4 different cell types: primitive/embryonic stem cell line (hESCT0), myeloid/erythroid cancer cell line (K562), hepatocellular carcinoma cell line (HepG2), and a blood cell line (GM12878).

In this repository, you will find the following:
1. Scripts to create and filter the DHS dataset for downstream classification tasks.
    - `TechnicalTestWangLab/code/master_dataset.ipynb`
    - `TechnicalTestWangLab/code/filter_dataset.ipynb`

2. Fine-tuning a nucleotide transformer 500M_human_ref model on the DHS dataset.
    - `TechnicalTestWangLab/code/fine_tun_DHS_model.ipynb`
    - Associated Figures can be found in: `TechnicalTestWangLab/figures/`
3. Extracting embeddings from the fine-tuned model and performing PCA analysis on embeddings 
    - `TechnicalTestWangLab/code/embeddings_DHS_NT_model.ipynb`
    - Associated Figures can be found in: `TechnicalTestWangLab/figures/`

The scripts were all run in `Google Colab`, under `Python version 3.10.12`. \
Due to limited available GPU on my HPC. I used one **L4 GPU**. 


## Dependencies

Packages needed to use the nucleotide-transformer model:
- **biopython**: 1.83
- **transformers**: 4.41.2
- **datasets**: 2.19.2
- **huggingface_hub**: 0.23.2
- **accelerate**: 0.31.0

## Installation

To install the required packages, run the following command:

```bash
pip install biopython transformers datasets huggingface_hub accelerate umap-learn
```

# Workflow
**Note:** for simplicity, steps 1 and 2 can be skipped as data file is directly imported from google drive in step 3. 
1. **Run `master_dataset.ipynb`**  
   This will process DHS peaks from Meuleamn et al.
2. **Run `filter_master.ipynb`**  
   This will filter DHS peaks and sequences for select cell types.  
   **Outputs:** `exclusive_peaks.txt` 
3. **Run `fine_tune_DHS_NT_model.ipynb`**  
   **Outputs:** 
   - Folder `finetuned-DHS-nucleotide-transformer-model` contains the fine-tuned nucleotide-transformer model 
   - Folder `DHS_NT_datasets` contains the split dataset object needed for embeddings. 
4. **Run `embeddings_DHS_NT_model.ipynb`**
   - Note: Use a *GPU L4* from Google Colab for this step.

# Usage
1. Open [Google Colab](https://colab.research.google.com/) and upload the `.ipynb` files.
2. Follow the workflow as outlined in `Workflow`.
3. The `fine_tune_DHS_NT_model.ipynb` will create a new folder within google drive to save model, and datasets, which are then automatically called when running `embeddings_DHS_NT_model.ipynb`


# Further Resources

- [How Instadeepai Fine-Tuned Their Nucleotide Transformer](https://github.com/huggingface/notebooks/blob/main/examples/nucleotide_transformer_dna_sequence_modelling.ipynb)

# References

1. Dalla-Torre, Hugo, Liam Gonzalez, Javier Mendoza Revilla, Nicolas Lopez Carranza, Adam Henryk Grywaczewski, Francesco Oteri, Christian Dallago, Evan Trop, Hassan Sirelkhatim, Guillaume Richard, et al. "The Nucleotide Transformer: Building and Evaluating Robust Foundation Models for Human Genomics." *bioRxiv* (2023). Cold Spring Harbor Laboratory.

2. Meuleman, Wouter, et al. "Index and biological spectrum of human DNase I hypersensitive sites." *Nature* 584.7820 (2020): 244-251. [Link to Paper](https://www.nature.com/articles/s41586-020-2559-3)

3. [Nucleotide Transformer GitHub](https://github.com/instadeepai/nucleotide-transformer)

4. Trop, Evan, et al. "Nucleosome Transformer: A deep learning framework for chromatin accessibility prediction." *bioRxiv* (2023). [Link to Paper](https://www.biorxiv.org/content/10.1101/2023.01.11.523679v3)

