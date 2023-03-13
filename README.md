## FireRisk: A Remote Sensing Dataset for Fire Risk Assessment with Benchmarks Using Supervised and Self-supervised Learning

### Description

In recent decades, wildfires, as widespread and extremely destructive natural disasters, have caused tremendous property losses and fatalities, as well as extensive damage to forest ecosystems. Many fire risk assessment projects have been proposed to prevent wildfires, but GIS-based methods frequently suffer from inflexible data features and limited generalizability. Inspired by the abundance of publicly available remote sensing projects and the burgeoning development of deep learning in computer vision, our research focuses on assessing fire risk using remote sensing imagery.

In this work, we propose a novel remote sensing dataset, FireRisk, consisting of 7 fire risk classes with a total of 91,872 labelled images for fire risk assessment. This remote sensing dataset is labelled with the fire risk classes supplied by the Wildfire Hazard Potential (WHP) raster dataset, and remote sensing images are collected using the National Agriculture Imagery Program (NAIP), a high-resolution remote sensing imagery program.

![FireRisk overview image](https://github.com/CharmonyShen/FireRisk/blob/main/images/FireRisk_overview.png?raw=true)

*This figure shows sample images of all 7 labels in our FireRisk dataset. The images measure 270 × 270 pixels, with a total of 91,872 image.*

### Contributions

1. We propose FireRisk, a remote sensing dataset for fire risk assessment, and offer a novel method for constructing a mapping between 7 fire risk classes and remote sensing images.
2. To investigate the performance of supervised and self-supervised learning on our FireRisk, we employ ResNet, ViT, DINO, and MAE as benchmark models. With the use of transfer learning, we obtain the results of these models pre-trained on ImageNet and then fine-tuned on our FireRisk.
3. Using the performance of our benchmarks on 20\% and 50\% of the training data from the original FireRisk, we illustrate the efficiency of data labelling in FireRisk as well as the sensitivity of various benchmark models to the amount of labelled data.y sampling 20% and 50% from the training set.
4. We gather an unlabelled dataset, UnlabelledNAIP, from the NAIP remote sensing project and utilize it to pre-train novel latent representations of DINO and MAE. The results of fine-tuning on FireRisk using these two representations demonstrate the potential of different self-supervised benchmarks for enhancement in fire risk assessment.

### Experiments

* The supervised benchmarks, we use ResNet-50 and ViT-B/16.
* The self-supervised benchmarks, we use DINO and MAE, with ViT-B/16 as backbone.
* Using 2 GPUs and batch size per GPU of 16 for training, and taking the results of the highest accuracy out of 100 epoches.

|Dataset|Model|pre-trained|Accuracy|F1-score|Precision|Recall|
|:----|:----|:----|:----|:----|:----|:----|
|FireRisk |ResNet-50 |ImageNet1k |63.20|52.56|52.75|53.41|
|FireRisk |ViT-B/16|ImageNet1k |63.31|52.18|53.91|51.15|
|FireRisk |DINO|ImageNet1k |63.36|52.60|54.95|51.27|
|FireRisk |DINO|UnlabelledNAIP|63.44|52.37|53.79|51.75|
|FireRisk |MAE|ImageNet1k |65.29|55.49|56.42|55.36|
|FireRisk |MAE|UnlabelledNAIP| 63.54|52.04|54.09|51.78|
|50% FireRisk |ResNet-50 |ImageNet1k |62.09|50.27|51.07|50.41|
|50% FireRisk |ViT-B/16|ImageNet1k |62.22|50.07|52.20|50.15|
|50% FireRisk |DINO|ImageNet1k |61.75|51.21|51.35|51.63|
|50% FireRisk |DINO|UnlabelledNAIP|62.49|51.35|52.08|51.48|
|50% FireRisk |MAE|ImageNet1k |63.70|50.23|52.85|51.94|
|50% FireRisk |MAE|UnlabelledNAIP|62.68|52.05|52.63|51.59|
|20% FireRisk |ResNet-50 |ImageNet1k |61.37|49.53|50.28|50.12|
|20% FireRisk |ViT-B/16|ImageNet1k |61.43|48.80|50.89|48.53|
|20% FireRisk |DINO|ImageNet1k |60.95|50.72|50.99|51.28|
|20% FireRisk |DINO|UnlabelledNAIP|61.96|50.83|53.03|50.62|
|20% FireRisk |MAE|ImageNet1k |62.51|51.13|52.46|50.87|
|20% FireRisk |MAE|UnlabelledNAIP|61.80|50.07|51.69|49.11|

*From the table we can draw the following conclusions:*

1. The maximum accuracy for the supervised benchmarks can reach 63.31%, while for the self-supervised benchmarks, the MAE pre-trained on ImageNet1k can achieve the optimal accuracy of all models at 65.29%.
And the checkpoint of the optimal model is
[MAE pre-trained on ImageNet1k](https://drive.google.com/file/d/1JEmEcGD-qTRXs_pGpR4FdiXGshpAsSo9/view?usp=sharing)

2. Our self-supervised learning benchmarks outperform supervised learning on FireRisk, although their improvement on less training data is limited.
3. Our new pre-trained latent representations have a considerable increase in DINO, which can reach 63.44% compared to 63.36% for the DINO pre-trained on ImageNet.

### Download

##### Paper

FireRisk: A Remote Sensing Dataset for Fire Risk Assessment with Benchmarks Using Supervised and Self-supervised Learning

##### Dataset

[FireRisk](https://drive.google.com/file/d/1J5GrJJPLWkpuptfY_kgqkiDtcSNP88OP/view?usp=share_link)

Image naming in our FireRisk:
$(pointid)\_(grid\_code)\_(x\_coord)\_(y\_coord).png$

| Name       | Data Type            | Meaning                                                                                                                                                     |
|------------|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FID        | integer              | ID of the data point in the file                                                                                                                            |
| pointid    | integer              | unique ID of the data point in the WHP dataset                                                                                                              |
| grid_code  | integer(from 1 to 7) | code for fire risk level                                                                                                                                    |
| class_desc | string(seven values) | description of the fire risk level, corresponding to the grid_code, which are 1:Very Low, 2:Low, 3:Moderate, 4:High, 5:Very High, 6:Non-burable and 7:water |
| x_coord    | number               | longitude coordinates of the grid centroid                                                                                                                  |
| y_coord    | number               | latitude coordinates of the grid centroid                                                                                                                   |


##### Pre-trained Checkpoints

* Using ViT-B/16 as the backbone architecture of MAE and DINO 
* Pre-training MAE for 80 epoches on our UnlabelledNAIP
* Pre-training DINO for 100 epoches on our UnlabelledNAIP

<table><tbody>
<!-- START TABLE -->
<!-- TABLE HEADER -->
<th valign="bottom"></th>
<th valign="bottom">DINO</th>
<th valign="bottom">MAE</th>
<!-- TABLE BODY -->
<tr><td align="left">pre-trained checkpoint</td>
<td align="center"><a href="https://drive.google.com/file/d/1iuaBpPZ3p_6dNplO60rzkJVkz2xfcmcH/view?usp=sharing">download</a></td>
<td align="center"><a href="https://drive.google.com/file/d/1p73kNHSya9mnCXsp_DP8ZVU7JcfB9Kpi/view?usp=sharing">download</a></td>
</tr>
</tbody></table>

### References

If you have used our FireRisk dataset, please cite the following papers: 

<!-- ### Acknowledgements

This research was undertaken using the LIEF HPC-GPGPU Facility hosted at the University of Melbourne. This Facility was established with the assistance of LIEF Grant LE170100200. -->