# TechnicalTestWangLab

## Description

This TechnicalTestWangLab repository which aims to classify DNase1 hypersensitvity site (DHSs) sequences from Meuleman et al. through a pre-trained Large Language Model (LLM) on the DNA sequences. The current analysis focuses on 4 classifying sequences from 4 different cell types: primitive / embryonic stemm cell line (hESCT0), Myeloid / erythroid cancer cell line (K562), Hepatocellular carcinoma cell line (HepG2), and a blood cell line (GM12878). 

In this repository, you will find the following. 
  1. Scripts to create and filter DHS dataset from for downstream classification tasks. 
  1. Fine-tuning a nucleotide transformer 500M_human_ref model on the DHS dataset
  3. Extract embeddins from fine-tuned model and unsupervised classification

The scripts were all run in `Google Colab`, using `Python version 3.10.12`.

##  Dependencies
Packages needed for nucleotide-transformer use nucleotide-transformer model: 
biopython: 1.83
transformers: 4.41.2
datasets: 2.19.2
huggingface_hub: 0.23.2
accelerate: 0.31.0

# Workflow

1. Run master_dataset.ipynb -> This will process DHS peaks from Meuleamn et al. 
2. Run filter_master.ipynb -> Will filter DHS peaks and sequences for select cell types --> `outputs:` exclusive_peaks.txt
3. Run fine_tune_DHS_NT_model.ipynb -> `outputs:` finetuned-DHS-nucleotide-transformer-model, DHS_NT_datasets 
5. Run embeddings_DHS_NT_model.ipynb


