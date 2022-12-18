---
layout: default
---

# Observational Study
To understand the merit of an actor in joining the rich-get-richer circle and its impact on the movie rating, we carry out an observational study to limit the effect of the confounders. Actors are matched through propensity score matching, namely their probability of being part of the treatment group, based on observed covariates. The treatment group is defined by the most successful actors, while the control group by the rest of the actors' population. According to the Pareto principle, the threshold between the number of appearances that dominate and the long tail of the power law distribution is defined by the 80/20 rule. Basically, 20% of the people detain the most number of appearances. Therefore, the splitting of the dataset will be carried out based on the 80th percentile of the distribution, more representative than the mean or the median when considering skewed distributions. To make the study more recent and to take into account movies where the ratings has a significant number of votes, we decided to only consider actors born after 1930. The used dataset involves 50869 actors and 86116 movies of released in the US.

The 80th percentile is identified with *7* career appearances.

<p align="center">
    <img width="1000" alt="correlation" src="https://user-images.githubusercontent.com/114060781/208290942-a9791b12-e75f-41e8-aa0c-872f72e672f5.png">

Multiple factors can influence the job assigment in the movie industry. The following observed covariates are taken into account for the observational study and for the matching process targeted to only consider the actors with similar propensity scores:

- **Gender**;
- **Main genre**, defined as the genre of the most movies where actors starred in. The affinity of actors towards specific genres may affect their probability of getting successful (e.g., affinity of Adam Sandler with Comedy movies);
- **Director**, defined as the director who directed the most movies where actors starred in. Directors tend to have preferences towards specific actors and hire them again for roles in their movies (e.g., Quentin Tarantino with Brad Pitt or Samuel L. Jackson);
- **Birth year**. Some actors may have a lower number of appearances just because they are young and at the beginning of their career;
- **Average movie release date**, defined as the average of the release dates of the movies where actors starred in. This would give a sense of the period of main activity of the actors career.

To further balance the dataset, a perfect matching is done on gender. An example of the resulting propensity scores is displayed below.

| actor               |   propensity_score | 
|:--------------------|:-------------------|
| Frank_Farrington    |           0.90474  |
| Jade_Pettyjohn      |       0.915799     | 
|Pat_Harmon           |           0.443002 |
| Aino-Maija_Tikkanen |           0.918347 | 
| TJ_O'Connell        |           0.870847 |

The resulting coefficients of the logistic regression are associated with each directors and genre and with birth date and average movie year. The highest (positive or negative) coefficients are shown below.

The balanced dataset contains 12066 actors.

## Analysis on balanced dataset



# Gender biases
Tthe gender bias seems to play a systematic role in the assigment of movies to actors, because of the difference in movie appearances and average ratings, visible from the bar plots (with 95% confidence intervals). However, by performing a Mann-Whitney U test between two distributions before and after the matching, it is observed that the difference in distributions by gender passes from being significantly different to being non significant, given the changes in p-values. This means that the majority of of the people in the control group were actresses and got discarded in the matching process, due to its larger size, so that the probability of joining the 'rich-get-richer' circle is not gender biased. We are aware that not all the possible confounders have been tackled in the present study, but this change in p-values shows an interesting trend. It is worth mentioning that the percentage of actresses in the original dataset and in the balanced one are almost the same, 0.42 and 0.39 respectively, making it a meaningful comparison in terms of size.

The label *is_post* in the legend indicates if the data refer to the dataset post treatment or not.


<p align="center">
    <img width="1000" alt="correlation" src="https://user-images.githubusercontent.com/114060781/208271104-66e076e9-6ce0-4e76-91a8-ff84fd0c9372.png">

The results of the Mann-Whitney U test for multiple parameters of interest is here shown, considering pre-matching and post-matching situations. Every test is performed with the goal of understanding if the distributions of actors and actresses are the same.
    
| Parameter   |Dataset| WMU test | p-value |
| --------- | -------- | ------- | ------- |
| Appearances| Pre-matching|534502483 | 0.001   |
|            |Post-matching| 17729895| 0.91   |
| Average ratings| Pre-matching| 510829106| 0   |
|            |Post-matching| 17704010.5| 0.81   |
| Birth year| Pre-matching| 444274431.5| 0   |
|            |Post-matching| 15803658| 0   |
| Average movie release year| Pre-matching| 528915061.0| 0.36   |
|            |Post-matching| 18196261| 0.02   |

The results show that the average birth year does not have significant differences, while the average movie release year, indicating the approximate time period when the actors have starred, changes from being non significant to being significant.

The distribution of the actors ratings is visible below.

<p align="center">
    <img width="650" alt="correlation" src="https://user-images.githubusercontent.com/114060781/208272505-eb06acf1-c86b-4b34-b393-e43887b5c11a.png">

A linear regression is implemented to actually verify that coming from the treatment group positively influences the movie ratings and to assess the influence of gender on the ratings.
    
<p align="center">
    <img width="650" alt="correlation" src="https://user-images.githubusercontent.com/114060781/208290083-d2aad207-6d84-4cfd-b7f7-ca77dbe350a3.png">
    
The results show the expected positive correlation of the treatment group on the ratings. However, it also shows that the gender does not play a significant role in influencing it. 
    
### Genre analysis
It is also interesting to show the relation between genres and ratings and how they are distributed in the balanced dataset. This could show if the preferences of the audience are diversified or if they tend to stick to certain types of films.
    
In the first bar plot (red palette), the distribution of actors per genre is strongly skewed (log y axis), where the most popular categories between actors are *Drama*, *Crime* and *Comedy*. However, the average ratings per genre show a different trend (blue palette). The star scores are comparable between different genres (linear y axis). The highest average star scores is obtained by the categories *Biography*, *Animation* and *Musical*. This could be explained because in such genre categories there is less competition (less movies produced), therefore the audience is less distributed over all the movies produced and the single actor can more easily have an impact on the rating. Moreover, there are less famous actors in Biography, Animation, and Music movies with respect to Drama, Crime and Comedy, therefore the few successful actors joining the rich-get-richer circle keep starring and increasing their number of appearances and their success.

To clarify, Animation genre refers to movies where actors give their voice to characters, while Music genre refers to movies about music or musicians (e.g., The Bohemian Rapsody).
    
<p align="center">
    <img width="1000" alt="correlation" src="https://user-images.githubusercontent.com/114060781/208291037-84372ff8-5eb0-4277-9733-98f3e4d0437c.png">
    

<iframe src="./plots/pie.html" width="1000" height="1000"> </iframe>
