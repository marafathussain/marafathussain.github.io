---
layout: page
title: <font style="color:blue;">Active Deep Learning</font> from Noisy Teacher
description: Semi-Supervised COVID-19 Pneumonia Infection Segmentation in CT
img: /assets/img/al_cover.png
importance: 1
---

<font style="color:red;">This work is under review in a top tier venue. So, detailed description and mathematical derivation has been skipped for now.</font>

Although reverse transcription polymerase chain reaction (RT-PCR) has been considered the gold standard for COVID-19 diagnosis, clinicians often utilize computed tomography (CT) scans to analyze the COVID-19 infection in lung. The automation of this infection analysis to accelerate clinical decision making typically requires pneumonia infection segmentation, where supervised deep learning has been showing promise. However, the difficulty of attaining pixel-level infection annotation for large volumetric CT images has recently steered the focus from developing supervised learning techniques to the investigation of semisupervised deep learning, so that a smaller expert-annotated dataset can be leveraged for infection segmentation in a larger dataset without annotation. However, semisupervised approaches often combine expert annotations and machine-generated annotation with equal weights in deep model training, though the later annotations are generally less reliable and potentially affect the model optimization negatively. To overcome this problem, we propose a semisupervised active learning approach that uses an example reweighting strategy, where machine-annotated training samples are weighted based on the similarity of their gradient directions to those of the expert-annotated data. We also adopt an active learning strategy by incorporating a query function in the reweighting algorithm to choose more trustworthy machine-annotated samples (i.e., noisy teacher) from the batch data. When validated on clinical benchmark data, our method showed better infection segmentation performance compared to state-of-the-arts.

<strong>Semi-Supervised Active Learning from Noisy Teacher</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/al_fig1.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 1: Schematic diagram of the proposed example-re-weighted active learning fromnoisy teacher approach for 3D image segmentation.
</div>
We have developed a semisupervised active learning (SSAL) from noisy teacher approach for pneumonia infection segmentation in CT. Contemporary semisupervised learning approaches often use a smaller pixel-level annotated dataset to train a deep model, which eventually generates pseudo labels for larger annotationless datasets. However, the predicted pseudo-labels are generally less reliable, and when those are weighted equally to expert annotations during network optimization, incorrect predictions get reinforced further that leads to a worse task performance. To overcome this problem, we use an example reweighting algorithm, where pseudo-annotated training samples are weighted based on the similarity of their gradient directions to those of the expert-annotated validation data. Similar example reweighting approach previously showed promise in 2D RGB image-based deep learning applications (Ren et al. 2018, Mirikharaji et al. 2019) for data with inaccurate labels, however, never been explored for volumetric radiographic medical images. In addition, the inaccurate/noisy labels in (Ren et al. 2018, Mirikharaji et al. 2019) were not produced automatically like the proposed approach. We also incorporate a query function in the reweighting algorithm so that in each iteration, it chooses more trustworthy samples from the batch data and discards the rest. This adaptive data sampling strategy of ours can be compared to pool-based SSAL strategy, where a small number of annotationless training samples are adaptively chosen in each training cycle (e.g., a fixed number of iterations, epochs, etc.) based on some preset criteria and presented to an oracle annotator (i.e., an expert teacher) for annotation. These data with the new expert annotatations are then added to the training data pool and the training cycle is repeated. In contrast, instead of using an oracle annotator, our approach adaptively chooses data samples based on the trustworthiness of their pseudo labels (i.e., noisy teacher), thus making a SSAL approach more time-efficient and automatic.

<strong>Data</strong>

We used three clinical datasets to validate our proposed method. We accessed two publicly available COVID-19 CT databases which contain pixel-level expert annotations of the COVID-19 infections. The first dataset is called COVID-19 CT benchmark dataset (Ma et al. 2020) that contains 20 COVID-19 CT volumes from 20 patients with expert radiologists performed pixel-level annotation of COVID-19 infection in lung. We also accessed the COVID-19 lung CT lesion segmentation challenge 2020' database, which contains 199 unenhanced chest CT scans from 199 COVID-19 patients with ground truth pixel-level annotations of COVID-19 lesions in the lung. Finally, we accessed 1473 CT scans from 623 patients from ANONYMOUS hospital with all required ethics approvals in place. Among these scans, 567 are from COVID-19 and 906 are from CAP patients or healthy humans. However, none of these scans have pixel-level annotation.

<strong>Results</strong>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/al_fig2.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 2: Pneumonia infection segmentation performance. (a) Bar-plot of Dice scoresachieved by contrasted methods. (b) Scatter-plot of Dice vs. annotation budget on thebenchmark data. (Acronyms: M-1 (Insensee et al. 2019), M-2 (Chen et al. 2020), M-3 (Yu et al. 2019), M-4 (Ma et al. 2020), M-5 (Fan et al. 2020), and M-6: supervised learning, w/o: without, w: with).
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ '/assets/img/al_fig3.png' | relative_url }}" alt="" title="example image"/>
    </div>
</div>
<div class="caption">
    Fig. 3: Pneumonia infection segmentation performance by different methods. (a) Bar-plot of Dice scores achieved by different methods. (b) Scatter-plot of Dice vs. annotationbudget on the challenge data. (Acronyms: C-1: supervised learning, and C-2: semi-supervised learning as in (Fan et al. 2020), w/o: without, w: with)
</div>

<strong>For Details</strong>

Coming soon....