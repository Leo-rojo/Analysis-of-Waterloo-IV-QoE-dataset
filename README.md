# Analysis of Waterloo-IV QoE Database
This repository contains code for the analysis of the *Waterloo-IV* database, demonstrating how individual QoE (Quality of Experience) 
perception significantly differs from group QoE perception. Since QoE models in the literature are constructed based on group perception, 
the results of this analysis suggest that these models could greatly benefit from personalization. This analysis represents the 
preliminary stage for the publication *Empowerment of Atypical Viewers via Low-Effort Personalized Modeling of Video Streaming Quality*.

The set-up is composed by:
 * OS: Windows 10
 * python version: 3.7
 * Microsoft Excel 365

In `requirements.txt` are listed the additional libraries needed to run the python code.

## Description
The project is organized in folders called "Figure x" where x represents the figure/figures of paper that you want to reproduce. Inside each folder further information are provided.

Part of the original [Database](https://ieee-dataport.org/open-access/waterloo-streaming-quality-experience-database-iv) is replicated in folder `Waterloo Streaming QoE Database IV`

### Waterloo-IV reference
`Zhengfang Duanmu, Wentao Liu, Zhuoran Li, Diqi Chen, Zhou Wang, Yizhou Wang, Wen Gao, September 24, 2020, "The Waterloo Streaming Quality-of-Experience Database-IV", IEEE Dataport, doi: https://dx.doi.org/10.21227/j15a-8r35.`

## Results
### Video ratings analysis
Description of analysis:

<div style="display: flex; justify-content: space-between; gap: 10px; text-align: center;">
  <div>
    <img src="images/Video_ratings_analysis/alluserbox1-1.png" alt="alluserbox" width="270">
    <p><em>Individual QoE perception</em></p>
  </div>
  <div>
    <img src="images/Video_ratings_analysis/cdfalluser2-1.png" alt="cdfalluser" width="270">
    <p><em>Group QoE perception</em></p>
  </div>
  <div>
    <img src="images/Video_ratings_analysis/Box_plot2_avemos-1.png" alt="Box_plot2_avemos" width="270">
    <p><em>Group QoE perception</em></p>
  </div>
</div>


<div style="display: flex; justify-content: space-between; gap: 10px;">
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_analysis/ECDF_individual_scores-1.png" alt="alluserbox" width="270">
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_analysis/boxplot_subset-1.png" alt="cdfalluser" width="270">
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_analysis/nonlinearityfact-1.png" alt="Box_plot2_avemos" width="270">
  </figure>
</div>

### Video ratings and QoE models analysis
Description of analysis:

<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/Video_ratings_and_QoE_models_analysis/legend4-1.png" alt="legend" width="600">
</div>

<div style="display: flex; justify-content: space-between; gap: 10px;">

  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/plcc_hdtv-1.png" alt="alluserbox" width="300">
    <figcaption>Individual QoE perception</figcaption>
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/srcc_hdtv-1.png" alt="cdfalluser" width="300">
    <figcaption>Group QoE perception</figcaption>
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/krcc_hdtv-1.png" alt="Box_plot2_avemos" width="300">
    <figcaption>Group QoE perception</figcaption>
  </figure>
</div>

<div style="display: flex; justify-content: space-between; gap: 10px;">
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/diffplcc_hdtv-1.png" alt="alluserbox" width="300">
    <figcaption>Individual QoE perception</figcaption>
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/diffsrcc_hdtv-1.png" alt="cdfalluser" width="300">
    <figcaption>Group QoE perception</figcaption>
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/diffkrcc_hdtv-1.png" alt="Box_plot2_avemos" width="300">
    <figcaption>Group QoE perception</figcaption>
  </figure>
</div>

### QoE model vs personalized QoE model
Description of analysis:

<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/QoE_model_vs_personalized_QoE_model/svmlindiff-1.png" alt="legend" width="600">
  <figcaption>Group QoE perception</figcaption>
</div>