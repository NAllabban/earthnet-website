---
layout: default
---

# Rich-get-Richer Mechanism

In this section we analyze the distributions of significant parameters to assess actor success and impact on movies and we give a possible explanation for such behaviors. It is indeed interesting to qualitatively understand why actors' success can be influenced by external factors and not only by the quality of the actors' work. We observed that distribution of actors' careers number of movie appearances is shown below. It is interesting to notice that it follows a power law, given that is linear in the logarithmic domain. Moreover, the typical exponential tail in the semilogarithmic y domain is visually observable.

<p align="center">
    <img width="1000" alt="correlation" src="https://user-images.githubusercontent.com/114060781/208259952-6f8f75e7-de37-418e-923b-6594a3d87134.png">

To statistically prove that the distribution follows a power law we perform a Kolmogorov-Smirnov test on the tail of the distribution. The results are here shown. Given the p-values larger than 0.05 we cannot reject the null hypothesis that the distribution is exponential.
   
| Dataset   | KS test  | p-value |
| --------- | -------- | ------- |
| Overall   | 0.32     | 0.11    |
| Actors    | 0.33     | 0.09    |
| Actresses | 0.30     | 0.17    |

An explanation for the onset of a power law can be given. Just as normal distributions arise from many independent random decisions averaging out, power laws can arise from the feedback introduced by correlated decisions across a population [1]. Successful actors keep starring with other successful actors, making them even more successful and naturally generating a power law in actors' productivity, namely the number of appearances in movies. This mechanism makes it difficult to quantify the impact of actors on movies, because of the large amount of possible confounders that influence the probability of an actor joining this 'rich-get-richer' loop.

    

[1] D. Easley and J. Kleinberg, Networks, Crowds, and Markets: Reasoning about a Highly Connected World, Cambridge University Press, 2010.
 # Observational Study
