---
layout: page
title: Relational Connectivity Transformer
description: Relational Connectivity Transformer for Enhanced Prediction of Absolute and Residual Intelligence
img: /assets/img/rct.jpg
importance: 1
category: Machine Learning
---



This project introduces the Relational Connectivity Trans- former (RCT), a novel Graph-Transformer model designed for predicting absolute and residual full-scale intelligence quotient (FSIQ), performance IQ (PIQ), and verbal IQ (VIQ) scores from resting-state functional magnetic resonance imaging (rs-fMRI) data. Early prediction of neurocognitive impairments via IQ scores may allow for timely intervention. To this end, our RCT model leverages a relation-learning strategy from paired sample data via a novel graph-based transformer framework. Through a comprehensive comparison with state-of-the-art approaches in a 5-fold cross-validation setup, our model demonstrated superior performance. Statistical analysis confirmed the significant improvement (p < 0.05) in FSIQ prediction, strengthening the efficacy of the proposed method. This work marks the first application of a Graph-Transformer in predicting IQ scores using rs-fMRI, introducing a novel learning strategy and contributing to the ongoing efforts to enhance the accuracy and reliability of human intelligence predictions based on functional brain connectivity.MAPE), (3) accuracy, (4) F1-score, and (5) binaryROC metrics. The ``fibe_function`` contains all the necessary functions to run this algorithm. 

## Contribution Summary
- It introduces the first Graph-Transformer-based approach for predicting absolute and residual IQ scores using rs-fMRI, addressing gaps in the SOTA by (a) predicting neurocognitive scores with Graph-Transformers for the first time, and (b) predicting ‘residual IQ’ scores along with absolute IQ scores.
- It pioneers pair-wise relation learning for neurocognitive prediction, processing data from two randomly selected subjects to learn relative relationships (i.e., effectively using each other as references) and improve IQ prediction accuracy. This relational learning enhances performance compared to traditional SOTA methods.
- It predicts four distinct relations (cumulative, relative, maximal, and minimal) to enhance task-specific learning.
- The pair-wise input strategy increases the training sample size from n to nPr (where P denotes permutation, n is the training sample size, and r = 2), addressing the infeasibility of rs-fMRI data augmentation.

## RCT Architecture
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/rct.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 1: Proposed Relational Connectivity Transformer framework.
</div>

## Data
We gathered 1,009 rs-fMRI data from the public Autism Brain Imaging Data Exchange (ABIDE). After excluding subjects with missing PIQ, VIQ, and FSIQ scores, N = 809 subjects remained (age: 6-64 years, mean: 16.63±7.26; male/female: 682/127; Autism Spectrum Disorder (ASD)/neurotypical (NT): 401/408) from 15 sites. The rs-fMRI data were preprocessed using the Configurable Pipeline for the Analysis of Connectomes (CPAC) with brain regions defined by the Craddock 200 atlas, resulting in 200 brain ROIs per sample. We then computed residual IQ scores (rFSIQ, rPIQ, rVIQ) for all subjects, considering age, sex, diagnostic group (ASD or NT), and data collection site as independent variables. The formula used was: rT = T −(α+βA+γS+δD+ηE), where rT and T represent residual and absolute IQ scores, respectively. The variables A, S, D, and E correspond to age, sex, diagnostic group, and sample collection site, respectively. α, β, γ, δ, and η are parameters of linear regression. A similar approach has been used for residual fluid intelligence estimation [23], however, our dataset lacks information on parental education and income. Absolute and residual IQ ranges are [41,180] and [-65,78], respectively.

## Results
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/rct_results.jpg' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 2: Comparison of absolute and residual IQ prediction performance. Bold red fonts denote the lowest mean error per IQ category. The blue font represents the second-lowest mean error. **differences are significant for p < 0.05.
</div>
To compare absolute and residual IQ prediction performance by the proposed RCT method with state-of-the-art approaches, we implemented a CNN-based graph representation learning approach BrainNetCNN, a task-specific graph generation-based GNN approach FBNetGen, a conventional graph trans- former approach Graphormer, and a rs-fMRI-tailored Graph-Transformer approach BNT [19]. We ran all these methods for 200 epochs in a 5-fold cross-validation setup. We used conventional single-input single-target feed-forward settings for these approaches and adhered to their authors-suggested hyperparameter settings. For the proposed approach, we tested two prediction scenarios: (1) both validation inputs are the same (i.e., from the same subject, X1 = X2), and (2) validation input pairs are mixed, i.e., X1=X2; X1 ̸= X2. We present absolute and residual IQ prediction performance by different approaches in Tables 2 and 3, respectively, in terms of MAE, MAPE, and MSE. In both tables, we observe that the proposed RCT approach consistently exhibits the lowest absolute and residual FSIQ, PIQ, and VIQ prediction errors. However, it is noteworthy that the lowest MAE, MAPE, and MSE are not consistently associated with a specific input scenario; rather, the best performance varies between the scenarios X1 = X2 and X1 = X2; X1 ̸= X2. In addition, we tested the statistical significance in prediction errors by the proposed RCT approach for X1 = X2 (to be fair with state-of-the-art) and by the best-performing state-of-the-art approach (i.e., FBNetGen in left table, and BrainNetCNN in right table). We found that the 2-tailed t-test on absolute error and absolute percentage error by the RCT and FBNetGen methods for the FSIQ score is significant for p < 0.05 (see left table). So, we can assume that the performance of the proposed RCT approach will also be statistically better than other approaches because other state-of-the-art performed worse than the FBNetGen method in absolute FSIQ prediction. This finding is also significant because the FSIQ score is a factor-weighted combination of the PIQ and VIQ scores.

<strong>For Details</strong>

Please read our papers [[1](https://marafathussain.github.io/assets/pdf/prime2024.pdf)]. The code can be found [here](https://github.com/marafathussain/RelationalConnectivityTransformer).
