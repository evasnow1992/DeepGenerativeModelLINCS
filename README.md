# Deep Generative Models on LINCS Data
Python code for the manuscript "Learning to Encode Cellular Responses to Systematic Perturbations with Deep Generative Models"

This repository provides Python code for preprocessing LINCS L1000 gene expression data and applying two deep generative models, Variational AutoEncoder (VAE) and Supervised Vector-Quantized Variational AutoEncoder (S-VQ-VAE) on the data for learning latent representations.
VAE and S-VQ-VAE are implemented with Pytorch.

## Required environment and packages
The code was tested on the following packages
* numpy 1.16.2
* matplotlib 3.0.3
* pandas 0.23.4
* cmapPy (for loading the LINCS datasets)
* torch 0.4.1
* sklearn 0.21.3
* scipy 1.3.1
* seaborn 0.9.0

Due to the requirement of cmapPy, the script should be run with Python2.7 to avoid compatibility issue.

## Data
The LINCS data are available from the Gene Expression Omnibus (GEO) with accession codes GSE70138 and GSE106127 (https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE70138; https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE106127)

The perturbagen class (PCL) information of small molecule perturbagens can be found in the paper "A next generation connectivity map: L1000 platform and the first 1,000,000 profiles" Supplementary Table S7.

## Files
### deep_generative_model_LINCS.ipynb
Code for preprocessing LINCS L1000 data and training VAE and S-VQ-VAE on three datasets:

**SM dataset** (SMP dataset in the manuscript): a subset of GEO dataset GSE70138, which contained the level 5 expression data (moderate z-scores) of the 978 landmark genes of 118,050 small-molecule-perturbed samples from 7 cell lines.

**GP dataset**: a subset of GEO dataset GSE106127, which contained the level 5 data of 119,013 gene-knocked-down samples from 9 cell lines.

**Both dataset** (SMGP dataset in the manuscript): a merge of the SM dataset and GP dataset while excluding 4,649 samples perturbed by two proteasome inhibitors, bortezomib, and MG-132.

### deep_generative model_LINCS_analysis.ipynb
Code for analyzing the latent representations of expression profiles learned with VAEs and S-VQ-VAEs. Analyses include:
* Identify signature nodes from the top hidden layer of SMGP-trained VAE model encoder.
* Compare the distribution of data generated with VAEs with real data.
* Generate data to simulate expression profiles perturbed with small molecules from a given perturbagen class.
* Classify PCL based on different latent representations of expression profiles.
* Predict drug-targets with latent representations of expression profiles.
* Reveal correlations between PCL global representations learned with S-VQ-VAE.

### VAE_encode_SMP.pth, VAE_decode_SMP.pth, VAE_mu_SMP.pth, and VAE_logvar_SMP.pth
Pretrained VAE model on SMP dataset.

### VAE_encode_GP.pth, VAE_decode_GP.pth, VAE_mu_GP.pth, and VAE_logvar_GP.pth
Pretrained VAE model on GP dataset.

### VAE_encode_SMGP.pth, VAE_decode_SMGP.pth, VAE_mu_SMGP.pth, and VAE_logvar_SMGP.pth
Pretrained VAE model on SMGP dataset.

### S_VQ_VAE_decode.pth, S_VQ_VAE_embedding.pth, and S_VQ_VAE_encode.pth
Pretrained S-VQ-VAE models for learning global representations for PCLs.


A tutorial of how to apply S-VQ-VAE on MNIST dataset is available at https://github.com/evasnow1992/S-VQ-VAE.
