# Customer Segmentation: Project Overview
_Please refer to link for code._
_I also recommend reading the notebook on Kaggle._

<a href="https://www.kaggle.com/code/blulypsee/customer-segmentation-clustering/notebook"><img src="https://kaggle.com/static/images/open-in-kaggle.svg" alt="Open in Kaggle" /></a> 


## SUMMARY
* Identified seven customer segments and performed customer profiling for each one of them by creating general portraits of customers from each group, which can help the mall to better understand their customers, increasing their business revenue and customer retention.
* Conducted segmentation studies for the physical FMCG store customer dataset from Kaggle that comprises demographical data about the customers.
* Utilized four unsupervised clustering algorithms, namely K-Means, DBSCAN, Gaussian Mixture, Agglomerative Clustering, to pinpoint the right number of customer groups for the dataset.

## RESULTS

In this project, the customer data has been analyzed in order to perform Customer Segmentation for a given FMCG store. FMCG stores are these where they sell fast-moving consumer goods which have a short shelf life because of high consumer demand, such are milk, fruit and vegetables, baked goods. 

The best clustering algorithm turned out to be the __Gaussian Mixture algorithm__, which predicted that customers should be divided into __7 groups__ based on their __demographic data__ from bonus cards. The general portraits of the customers from each cluster have been created and are shown in the figure below.

![summary pic](https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/summary_profiling.png)

The summary of each cluster incorporates the ideal customer's biological sex, age, marital status, category of occupation, median annual income for the group, level of education, and the size of the city the customer lives in. If some of the characteristics are not mentioned in the cluster description that means the cluster spans all options or the entire range of values. The ones mentioned are considered to be prevailing over other options of the characteristic.

## The Outline

 1. [Project At A Glance](#Project_At_A_Glance)
 2. [Introduction](#Intro)
 3. [Problem Statement and Motivation](#Problem_Motiv)
 4. [EDA](#EDA)
 5. [Clustering](#clustering)
 6. [Customer Profiling](#profile)

<a id="Project_At_A_Glance"></a>
## Project At A Glance

__Python Version__: 3.7.12

__Packages__: numpy, pandas, matplotlib, seaborn, plotly, scipy, sklearn.

<a id="Intro"></a>
## Introduction

Customer segmentation is the process of dividing customers into groups based on common characteristics such as demographics, behavior, or preferences. This is important for businesses because it allows them to tailor their marketing, sales, and customer service strategies to specific groups of customers. For example, it can used to improve customer understanding, i.e. by segmenting customers, businesses gain a deeper understanding of their needs, preferences, and behaviors. This allows them to better serve their customers, create more targeted marketing campaigns, and improve customer satisfaction. 

In addition, when businesses understand their customer segments, they can create more targeted marketing campaigns that are more likely to resonate with the intended audience. This can increase the effectiveness of marketing efforts, leading to more sales and revenue. Customer segmentation also allows businesses to create personalized experiences for different groups of customers, which can lead to increased customer loyalty and retention. Moreover, by targeting specific customer segments, businesses can save money on marketing and advertising by only reaching out to those who are most likely to buy their products or services.

By understanding their customers better, businesses can create more effective strategies that lead to customers being satisfied and thus higher revenue.

<a id="Problem_Motiv"></a>
## Problem Statement and Motivation

Since I was a child, I have always wondered how the store decides which of the products should be on sale on a specific day and why sometimes the product becomes sold out in a matter of seconds and the other day nobody even pays attention to it. Why have I never seen certain products with red price labels? How does the store decide how often to buy some groceries, not to mention how they choose the right number? It was something I have considered thought-provoking until I have actually understood how it works and how easily one can make a wrong decision, which will lead to the decrease in revenue and to customer dissatisfaction. 

After realizing that a lot of such decisions rely on the analysis of customers, products sold, products people buy on special occasions etc. altogether, I have started asking myself, what customer group do I belong to? Based on the spent money only I can roughly estimate what should the group I belong to look like, however, there is certainly more to it than I can see. But how actually can the customer groups be identified? This question piqued my interest in this field and that is the exact reason why I decided to explore it on my own and get the feeling of what the analysis and segmentation process actually looks like in the real world.

My __goal__ for this project was to implement different clustering algorithms to identify the main groups of customers for the dataset. Also, after finding these groups, my objective was to characterize these groups with the help of visualization tools and to make an attempt at understanding consumer behaviour and gaining a deeper understanding of the challanges and opportunities within this industry.

__So the outline of the project looks roughly like this.__

At first, I have looked through the whole dataset, visualized some of the relationships and identified the key features in the dataset that allowed me to find out more about the population structure and gave me the opportunity to approximate the popularity of the mall with certain types of customers. For example, the Education feature is one of these and it reveals that, in the place where the mall is located, there are a lot of people with high school diploma at most and a really low number of people who finished their graduate studies. This information, in turn, gave me the hint what age ranges should be expected for each of customer groups based on education solely. This data assisted me in comprehending what kinds of clusters I anticipated to see after actually performing clustering, and these insights emerged to be extremely helpful in further comparision of the results of different clustering algorithms. 

A Principal Component Analysis has been performed for dimensionality reduction. For the clustering itself, I have run four easily distinguishable clustering models, which were K-Means, DBSCAN, Gaussian Mixture and Agglomerative Clustering, on the the PCA components to cluster customer population into different segments and have performed optimization for each of these models separately to receive clusters best describing the data. Next, after choosing the best clustering algorithm I have created pictures of the customers from each cluster, which can act as a guide for the mall's marketing and advertising to reach their ideal customers.

<a id="EDA"></a>
## EDA
Here are some highlights from the notebook's EDA section. 

<img src="https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/age_distribution.png" width="1254" height="860" />


The plots above show us the distribution of age with respect to different categorical values in our dataset. First, recall that the ratio of the number of females to the number of males in our dataset is almost one, i.e. the dataset contains almost the same number of women as the number of men. That said, we see that there are more older men than women in the data with the median age for men 36 years, and for women 30 years.

Concerning marital status, the plot suggests that the people who are 'single' are usually older than these who are 'non-single'. In the central left plot we see that the data consists mostly of the high school graduates in their 30s, also there are people a bit youger than the ones mentioned in their 20s who either have not filled in this section or have other educational attainment. Usually the people who have graduated from university are in their 50s, whilst these who finished their graduate studies are older with the median age of 65.

As for the occupation variable, we see that the majority of customers is in their 30s for each of the curves. So we can't really tell what the customer's occupation is if we were to come across one of the customers, unless we will be relying on probabilities based on the number of members in each category, still this feature and the age aren't enough to form distinct clusters of customers. The same can be said about the settlement size.

![eda_education](https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/eda_education.png)


Note, other takeaways from the EDA can be found in the notebook.

<a id="clustering"></a>
## Clustering

<img src="https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/clustering_algorithms_comparison.png"/>

Out of all four algorithms I have used, I have chosen the __Gaussian Mixture__ model to be the most suitable for the problem at hand, because K-Means and Agglomerative Clustering split visible clusters in halves, and DBSCAN, even though fits the data well, predicts one cluster to be representing all outliers in the dataset, which would not make sense for customer profiling.  Gaussian Mixture seems to be the best model, because it predicts visible clusters better than DBSCAN.

<a id="profile"></a>
## Customer Profiling

To see what clusters tell us about customers who belong to them, I took a look at the features in the light of clusters using visualization tools and then summarized the information from all plots in the picture right after the charts.

![](https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/counts_age_distribs.png)

The customer profile of the cluster may vary depending on how many people are in that cluster, whether it's 500 or 100. The clusters with greater numbers of customers do seem trust-worthy, since they capture all similarities between customers and generalize well. However, small clusters are not necessarily terrible, because they might consist of the underrepresented population visiting the mall. Take the cluster no.5, it has 81 members, and consists mostly of people over 60 years old.

<img src="https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/sex_education_distrib_clusters.png" width="1254" height="480"/>

If we were to continue looking at the cluster no.5, we may notice that it includes only males who graduated from university. That alone tells us a lot about the cluster.

![summary pic](https://raw.githubusercontent.com/Sofxley/customer-segmentation/main/images/summary_profiling.png)
