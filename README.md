## FireRisk: A Remote Sensing Dataset for Fire Risk Assessment with Benchmarks Using Supervised and Self-supervised Learning

### Description

![FireRisk overview image](https://github.com/CharmonyShen/FireRisk/blob/main/images/FireRisk_overview.png?raw=true)

### Download

##### Paper

FireRisk: A Remote Sensing Dataset for Fire Risk Assessment with Benchmarks Using Supervised and Self-supervised Learning

##### Dataset

[FireRisk](https://drive.google.com/file/d/1J5GrJJPLWkpuptfY_kgqkiDtcSNP88OP/view?usp=share_link)

##### Pre-trained Checkpoints

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

### Benchmarks


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

### References

If you have used our FireRisk dataset, please cite the following papers: 

<!-- ### Acknowledgements

This research was undertaken using the LIEF HPC-GPGPU Facility hosted at the University of Melbourne. This Facility was established with the assistance of LIEF Grant LE170100200. -->