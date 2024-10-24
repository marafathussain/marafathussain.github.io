---
layout: page
title: Radiomics with Deep Learning
description: Learnable Image Histogram for Cancer Analysis
img: /assets/img/r1_cover.png
importance: 2
category: Machine Learning
---

Fuhrman cancer grading and tumor-node-metastasis (TNM) cancer staging systems are typically used by clinicians in the treatment planning of renal cell carcinoma (RCC), a common cancer in men and women worldwide. Pathologists typically use percutaneous renal biopsy for RCC grading, while staging is performed by volumetric medical image analysis before renal surgery. Recent studies suggest that clinicians can effectively perform these classification tasks non-invasively by analysing image texture features of RCC from computed tomography (CT) data. However, image feature identification for RCC grading and staging often relies on laborious manual processes, which is error prone and time-intensive. To address this challenge, we developed a learnable image histogram in the deep neural network framework, named "ImHistNet", that can learn task-specific image histograms with variable bin centers and widths. This approach enables learning statistical context features from raw medical data, which cannot be performed by a conventional convolutional neural network (CNN). The linear basis function of our learnable image histogram is piece-wise differentiable, enabling back-propagating errors to update the variable bin centers and widths during training. This novel approach can segregate the CT textures of an RCC in different intensity spectra, which enables efficient Fuhrman low (I/II) and high (III/IV) grading as well as RCC low (I/II) and high (III/IV) staging. 

<strong>Learnable Image Histogram</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/r1_fig1.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 1: The graphical representation of the architecture of our learnable image histogram using CNN layers. We also break down our piece-wise linear basis function <b>H<sub>b</sub><sup>x</sup></b> on top of the figure in relation to different parts of the learnable image histogram architecture.
</div>
Our proposed learnable image histogram (LIH) stratifies the pixel values in an image <b>x</b> into different learnable and possibly overlapping intervals (bins of width <b>w<sub>b</sub></b>) with arbitrary learnable means (bin centers <b>β<sub>b</sub></b>). Given a 2D image (or a 2D region of interest or patch) <b>x: R<sup>2</sup>→R</b>, the feature value <b>h<sub>b</sub><sup>x</sup>: b ∈ B→R</b>, corresponding to the number of pixels in <b>x</b> whose values fall within the <b>b<sup>th</sup></b> bin, is estimated as:

<b>h<sub>b</sub><sup>x</sup> = Φ{H<sup>x</sup><sub>b</sub>} = Φ{max(0, 1−|x−β<sub>b</sub>| × w<sub>b</sub>)}</b>,

where <b>B</b> is the set of all bins, <b>Φ</b> is the global pooling operator, <b>H<sub>b</sub><sup>x</sup></b> is the piece-wise linear basis function that accumulates positive votes from the pixels in <b>x</b> that fall in the b>b<sup>th</sup></b> bin of interval <b>[β<sub>b</sub>-w<sub>b</sub>/2, β<sub>b</sub>+w<sub>b</sub>/2]</b>, and <b>w<sub>b</sub></b> is the width of the <b>b<sup>th</sup></b> bin. Any pixel may vote for multiple bins with different <b>H<sub>b</sub><sup>x</sup></b> since there could be an overlap between adjacent bins in our learnable histogram. The final <b>|B|×1</b> feature values from the learned image histogram are obtained using a global pooling <b>Φ</b> over each <b>H<sub>b</sub><sup>x</sup></b> separately.

<strong>ImHistNet Classifier Architecture</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/r1_fig2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 2: Multiple instance decisions aggregated ImHistNet for RCC grade and stage classification. The light green block represents the proposed LIH layer shown in Fig. 1.
</div>
The classification network comprises ten layers: the LIH layer, five (F1-F5) fully connected layers (FCLs), one softmax layer, one average pooling (AP) layer, and two thresholding layers. The first seven layers contain trainable weights. The input is a 64×64 pixel image patch extracted from the kidney+RCC slices. During training, we fed randomly shuffled image patches individually to the network. The LIH layer learns the variables <b>β<sub>b</sub></b> and <b>w<sub>b</sub></b> to extract characteristic textural features from image patches. In implementing the proposed ImHistNet, we chose <b>B = 128</b> and "average" pooling at <b>H<sub>b</sub><sup>x</sup></b>. We set subsequent FCL (F1-F5) size to 4096×1. The number of FCLs plays a vital role as the model's overall depth is important for good performance. Empirically, we achieved good performance with five FCL layers. Layers 8, 9, and 10 of the ImHistNet are used during the testing phase and do not contain any trainable weights.

<strong>Data</strong>

We used CT scans of 159 patients from The Cancer Imaging Archive (TCIA) database. These patients' diagnosis was clear cell RCC, of which 64 belonged to Fuhrman low (I/II), and 95 belonged to Fuhrman high (III/IV). Also, 99 patients were staged low (I-II), and 60 were staged high (III-IV) in the same cohort. The images in this database have variations in CT scanner models and spatial resolution. We divided the dataset for training/validation/testing as 44/5/15 and 75/5/15 for Fuhrman low and Fuhrman high, respectively. For anatomical staging, we divided the dataset for training/validation/testing as 81/3/15 and 42/3/15 for stage low and stage high, respectively. This database does not specify the time delay between the contrast media administration and acquisition of the image. Therefore, we cannot distinguish a CT volume in terms of the corticomedullary and nephrographic phase.

<strong>Results</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/r1_fig3.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 3: RCC grading performance by different methods, where the proposed method performed the best.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/r1_fig4.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 4: RCC staging performance by different methods, where the proposed method performed the best.
</div>

<strong>For Details</strong>

Please read our papers [[1](https://link.springer.com/chapter/10.1007/978-3-030-32226-7_15)], [[2](https://link.springer.com/chapter/10.1007/978-3-030-32692-0_61)], [[3](https://www.sciencedirect.com/science/article/abs/pii/S0895611121000732)]. Code can be found [here](https://github.com/marafathussain/ImHistNet).
