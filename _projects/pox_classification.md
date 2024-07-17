---
layout: page
title: Digital Skin Image Classification
description: Classification of Pox Types
img: /assets/img/pox.png
importance: 2
category: Machine Learning
---

The clinical characteristics of Monkeypox closely resemble Smallpox, and the skin lesions and rashes associated with Monkeypox often bear a resemblance to other pox infections like Chickenpox and Cowpox. These similarities pose a challenge for healthcare professionals who rely on visual examination to detect Monkeypox. Additionally, due to the infrequency of Monkeypox cases prior to the current outbreak, there is a lack of knowledge among healthcare professionals regarding this disease. Inspired by the success of artificial intelligence (AI) in COVID-19 detection, there is growing interest within the scientific community to explore the potential of AI in detecting Monkeypox using digital skin images. However, the scarcity of available Monkeypox skin image data has been a major obstacle in utilizing AI for Monkeypox detection. Therefore, in this research paper, we addressed this limitation by utilizing a web-scraped dataset consisting of Monkeypox, Chickenpox, Smallpox, Cowpox, Measles, and healthy skin images. The aim was to investigate the feasibility of employing state-of-the-art AI deep models for Monkeypox detection from skin images.


<strong>Brief Description of the Method</strong>

In this paper, we test the feasibility of using state-of-the-art AI techniques to classify different types of pox from digital skin images of pox lesions and rashes. The novelties of this work are the following.
1) We utilize a database that contains skin lesion/rash images of 5 different diseases i.e., Monkeypox, Chickenpox, Smallpox, Cowpox, and Measles, as well as contains healthy skin images.
2) Our database contains more data for pox, measles, and healthy images scraped on the Web.
3) We tested the disease classification power of seven state-of-the-art deep models for digital skin images. We tested the disease classifica- tion performance of ResNet50, DenseNet121, Inception-V3, SqueezeNet, MnasNet-A1, MobileNet-V2, and ShuffleNet-V2.
4) We performed 5-fold cross-validation tests for each of the AI deep models to more comprehensively analyzing our findings.


<strong>Results</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/pox_table1.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    TABLE 1
    
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/pox_table2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    TABLE 2
</div>

We presented the quantitative comparison of mean precision, mean recall, mean F1 score and mean accuracy, estimated over the 5-fold cross-validation, for all classes by all deep AI models in Table 1. Here, we see that the best accuracy is achieved by the ShuffleNet-V2 (79%). ShuffleNet-V2 has fewer trainable parameters (i.e., 2.3 million [M]) than ResNet50 (25.6 M), Inception-V3 (23.8 M), DenseNet121 (7.2 M), MnasNet- A1 (3.9 M) and MobileNet-V2 (3.4 M) (see Table II). From our observation of the prediction performance by different deep models, as summarized in Table 1, we hypothesize that models with a larger number of trainable parameters may be under fitted due to the small training sample size. On the other hand, although the SqueezeNet has fewer trainable parameters (i.e., 1.2 M) than the ShuffleNet-V2 (2.3 M), it is overfitted on the small number of training samples, thus resulting in worse prediction performance on the validation data.

Furthermore, we present the quantitative comparison of mean precision, mean recall, mean F1 score, and mean accuracy, estimated over the 5-fold cross-validation, for all classes using the ensemble approach in Table 2. We see in this table that the ensemble approach shows the best performance in terms of all the metrics, notably in terms of accuracy (83%), compared to those by individual deep models as summarized in Table 1.


<strong>For Details</strong>

Please read our paper for details [[1](https://www.biorxiv.org/content/biorxiv/early/2022/08/09/2022.08.08.503193.full.pdf)].
