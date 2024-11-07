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
The results are shown in the figures below. The project is organized into folders named 
"Figure x_results_name," where x indicates the figure number to reproduce, and the text 
following the underscore identifies the figure's category. Each folder contains additional information.

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
**Figure 1:** presents a box plot of the ratings given to
the videos by all 92 reliable users in the dataset. The plot arranges
the users in a non-decreasing order of their mean rating of the 450
device-specific videos. The mean rating varies from 42 to 89, i.e.,
form the low end of the fair grade to the middle of the excellent
grade, which constitutes a huge difference in the subjective quality
perception.
<div>
<img src="images/Video_ratings_analysis/alluserbox1-1.png" alt="alluserbox" width="300">
</div>

**Figure 2:** To illustrate the impact of the viewing device, figure 1b
reports the distribution of MOS computed for every video in each
of the phone, HDTV, and UHDTV classes. The MOS distributions
represent hypothetical "average" users of the three classes. While the perception of the UHDTV videos is more 
positive, the three MOS distributions are similar and resemble a normal distribution.
<div>
<img src="images/Video_ratings_analysis/cdfalluser2-1.png" alt="cdfalluser" width="300">
</div>

**Figure 3:** To avoid device-related bias, we analyze HDTV videos rated by 32 users. 
The box plot shows HDTV ratings range from a mean of 42 to 86, with a wide 
interquartile range similar to all device types in Figure 1. This variation highlights 
substantial user-to-user differences in video perception. Figure 1c also includes a hypothetical 
"average" HDTV user (green), based on MOS distribution. This "average" user differs notably 
from real users, with both a distinct mean rating and a much lower rating variance.
<div>
<img src="images/Video_ratings_analysis/Box_plot2_avemos-1.png" alt="Box_plot2_avemos" width="300">
</div>

**Figure 4:** Figure 4 compares the "average" HDTV user with two contrasting real HDTV users, 
H1 and H32, whose rating patterns differ significantly. User H1 rates roughly 70% of videos 
as fair or below (0–60), while user H32 rates about 80% as excellent (80–100). These results 
suggest that the MOS metric, as an aggregate across users, fails to accurately reflect the 
individual video quality perception for many users.
<div>
<img src="images/Video_ratings_analysis/ECDF_individual_scores-1.png" alt="alluserbox" width="300">
</div>

**Figure 5:** To refine the analysis, we focus on high-quality nature videos on phones, narrowing the 
set to 26 videos with VMAF scores of 90–100, VMAF variance under 10, and rebuffering time below 1 second. 
Figure 5 shows the ratings from all 29 phone users and the "average" phone user (in green), who 
represents each video's MOS. Despite this uniform video quality, the "average" phone user poorly 
reflects individual perceptions—user P1's mean rating is 64, while user P29’s is 98, with P29 frequently 
assigning perfect scores. This highlights that even for similar videos, user perceptions vary widely and 
are not well-represented by MOS.
<div>
<img src="images/Video_ratings_analysis/boxplot_subset-1.png" alt="cdfalluser" width="300">
</div>

**Figure 6:** ABR streaming algorithms often use QoE models that approximate subjective opinions with a linear 
function of certain influence factors. Here, we assess the linear correlation between these factors 
(VMAF, VMAF variance, and rebuffering time) and user ratings. To isolate each factor, we group videos by 
device and genre, varying only one factor while keeping the others constant:
- VMAF: 26 phone nature videos with VMAF variance <10 and rebuffering time <1s
- VMAF variance: 24 HDTV nature videos with VMAF 90–100 and rebuffering time <1s
- Rebuffering time: 26 HDTV slide videos with VMAF 90–100 and VMAF variance <10

For each user on the corresponding device type, we calculate the Pearson correlation coefficient (PCC) between 
the varied factor and the user’s video rating. Figure 6 shows PCC distributions across users for each factor. 
Only for rebuffering time—and only for 30% of users—does the absolute PCC exceed 0.5. Otherwise, PCC values are 
generally low and close to 0, with wide variability in both magnitude and sign across users. This suggests that 
user video perception is highly individual and non-linear, making linear QoE models used in ABR algorithms poorly 
suited for accurately predicting individual subjective perceptions.
<div>
<img src="images/Video_ratings_analysis/nonlinearityfact-1.png" alt="Box_plot2_avemos" width="300">
</div>

### Video ratings and QoE models analysis
Description of analysis:

**Figure 7:** 
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

**Figure 8:** 
<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/Video_ratings_and_QoE_models_analysis/legend4-1.png" alt="legend" width="700">
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
**Figure 9:** 
We compare simple QoE models trained on MOS versus user-specific ratings, both using VMAF, VMAF variance, and rebuffering 
time as features. The models are trained on the HDTV data from the WaterlooSQoE-IV dataset using linear regression or 
Support Vector Regression (SVR) with a nonlinear kernel. Linear models use 5-fold cross-validation, while SVR models 
require 5-fold nested cross-validation for hyperparameter tuning. Training is done with MOS or individual scores, and 
testing is done with individual scores. The MAE (Mean Absolute Error) is used to evaluate the models.

The figure displays the error difference along with its standard deviation for HDTV users, ordered by their mean rating. Whether using SVR or linear regression, the MAE is consistently higher for MOS-trained models compared to personalized QoE models. For users close to the average HDTV user, the error difference is small. However, for users farther from the average, the error difference becomes larger and more significant. Therefore, personalized QoE models show greater accuracy than MOS-trained models for a large number of users.

<div style="text-align: center; margin-bottom: 20px;">
  <img src="images/QoE_model_vs_personalized_QoE_model/svmlindiff-1.png" alt="legend" width="600">
</div>