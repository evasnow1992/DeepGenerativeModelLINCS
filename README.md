# Deep Generative Models on LINCS Data
Python codes for the manuscript "Decode the Gene Expression State with Deep Generative Models and LINCS L1000 Data"
This repository provides Python codes for preprocessing LINCS L1000 gene expression data and applying two deep generative models, Variational AutoEncoder (VAE) and Supervised Vector-Quantized Variational AutoEncoder (S-VQ-VAE) on the data for learning latent representations.
VAE and S-VQ-VAE are implemented with Pytorch.

The repository contains the following files.

#### deep_generative_model_LINCS.ipynb
Codes for preprocessing LINCS L1000 data and training VAE and S-VQ-VAE on three datasets:
**SM dataset** (SMP dataset in the manuscript): a subset of Gene Expression Omnibus (GEO) dataset GSE70138, which contained the level 5 expression data (moderate z-scores) of the 978 landmark genes of 118,050 small-molecule-perturbed samples from 7 cell lines.
**GP dataset**: a subset of GEO dataset GSE106127, which contained the level 5 data of 119013 gene-knocked-down samples from 9 cell lines.
**Both dataset** (SMGP dataset in the manuscript): a merge of the SM dataset and GP dataset while excluding 4649 samples perturbed by two proteasome inhibitors, bortezomib, and MG-132.

#### deep_generative model_LINCS_analysis.ipynb
Codes for analyzing the latent representations of expression profiles learned with VAEs and S-VQ-VAEs. Analyses include:
* Identify signature nodes from the top hidden layer of SMGP-trained VAE model encoder.
* Compare the distribution of data generated with VAEs with real data.
* Generate data to simulate expression profiles perturbed with small molecules from a given perturbagen class.
* Classify PCL based on different latent representations of expression profiles.
* Predict drug-targets with latent representations of expression profiles.
* Reveal correlations between PCL global representations learned with S-VQ-VAE.

#### VAE_encode_SMP.pth
#### VAE_decode_SMP.pth
#### VAE_mu_SMP.pth
#### VAE_logvar_SMP.pth
Pretrained VAE model on SMP dataset.

#### VAE_encode_GP.pth
#### VAE_decode_GP.pth
#### VAE_mu_GP.pth
#### VAE_logvar_GP.pth
Pretrained VAE model on GP dataset.

#### VAE_encode_SMGP.pth
#### VAE_decode_SMGP.pth
#### VAE_mu_SMGP.pth
#### VAE_logvar_SMGP.pth
Pretrained VAE model on SMGP dataset.

#### S_VQ_VAE_decode.pth
#### S_VQ_VAE_embedding.pth
#### S_VQ_VAE_encode.pth
Pretrained S-VQ-VAE models for learning global representations for PCLs.

Another tutorial of how to apply S-VQ-VAE on MNIST dataset is available at [https://github.com/evasnow1992/S-VQ-VAE] (https://github.com/evasnow1992/S-VQ-VAE)
