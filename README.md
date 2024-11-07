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

### Waterloo-IV 
The Waterloo-IV dataset consists of 1,350 streaming videos, covering all combinations of five source videos, 
two video encoders (H.264 and HEVC), nine network traces, five ABR algorithms, and three types of viewing devices: 
phone, high-definition television (HDTV), and ultra-high-definition television (UHDTV). The source videos span 
various genres, such as nature and sports, with an average duration of approximately 30 seconds. Out of 97 participants 
in a university lab's subjective experiment, five users were deemed unreliable and excluded from the dataset. 
The remaining 92 participants were randomly assigned to one of the three device categories. The dataset includes QoE ratings, 
ranging from 0 to 100, for device-specific videos provided by 29 phone users, 32 HDTV users, and 31 UHDTV users.

####  Waterloo-IV reference
`Zhengfang Duanmu, Wentao Liu, Zhuoran Li, Diqi Chen, Zhou Wang, Yizhou Wang, Wen Gao, September 24, 2020, "The Waterloo Streaming Quality-of-Experience Database-IV", IEEE Dataport, doi: https://dx.doi.org/10.21227/j15a-8r35.`

## Results
### Video ratings analysis
Description of analysis:

<div style="display: flex; justify-content: space-between; gap: 10px;">
    <img src="images/Video_ratings_analysis/alluserbox1-1.png" alt="alluserbox" width="270">
    <img src="images/Video_ratings_analysis/cdfalluser2-1.png" alt="cdfalluser" width="270">
    <img src="images/Video_ratings_analysis/Box_plot2_avemos-1.png" alt="Box_plot2_avemos" width="270">
  
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
  <img src="images/Video_ratings_and_QoE_models_analysis/legend4-1.png" alt="legend" width="700">
</div>

<div style="display: flex; justify-content: space-between; gap: 10px;">

  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/plcc_hdtv-1.png" alt="alluserbox" width="270">
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/srcc_hdtv-1.png" alt="cdfalluser" width="270">
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/krcc_hdtv-1.png" alt="Box_plot2_avemos" width="270">
  </figure>
</div>

<div style="display: flex; justify-content: space-between; gap: 10px;">
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/diffplcc_hdtv-1.png" alt="alluserbox" width="270">
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/diffsrcc_hdtv-1.png" alt="cdfalluser" width="270">
  </figure>
  <figure style="margin: 0; text-align: center;">
    <img src="images/Video_ratings_and_QoE_models_analysis/diffkrcc_hdtv-1.png" alt="Box_plot2_avemos" width="270">
  </figure>
</div>

### QoE model vs personalized QoE model
We compare simple QoE models trained on MOS versus user-specific ratings, both using VMAF, VMAF variance, and rebuffering 
time as features. The models are trained on the HDTV data from the WaterlooSQoE-IV dataset using linear regression or 
Support Vector Regression (SVR) with a nonlinear kernel. Linear models use 5-fold cross-validation, while SVR models 
require 5-fold nested cross-validation for hyperparameter tuning. Training is done with MOS or individual scores, and 
testing is done with individual scores. The MAE (Mean Absolute Error) is used to evaluate the models.

The figure displays the error difference along with its standard deviation for HDTV users, ordered by their mean rating. Whether using SVR or linear regression, the MAE is consistently higher for MOS-trained models compared to personalized QoE models. For users close to the average HDTV user, the error difference is small. However, for users farther from the average, the error difference becomes larger and more significant. Therefore, personalized QoE models show greater accuracy than MOS-trained models for a large number of users.

<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/QoE_model_vs_personalized_QoE_model/svmlindiff-1.png" alt="legend" width="600">
</div>