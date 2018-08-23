# US-County-Data---Statistical-Analysis
## Cluster Analysis on the US County data using SAS

### Dataset: 
The CountyData dataset contains county level data of all the states with data regarding: Population, Population Density, Population Change %, Hispanic %, Under 5 %, Age 65-75 %, Black %, Asian%, Birth Rate, Highschool Graduates%, College Graduates%, Household Income. 

### Data cleaning:

1.	It was observed that there are multiple blank fields in the dataset. 
2.	For better analysis the row element, i.e. county-level null fields have been filled with the average value of their corresponding state level data of those columns.

**Cluster Analysis** by definition is the grouping of elements into groups or clusters which are alike. Below are some of the cluster solutions prepared for this data set:

## Test-1: Clustering Using all the Factors

Inputs: All the variables

According to the Criterion for the Number of Clusters graph, the graph meets 0 at <8 or >4 and at 200 Number of Clusters. This implies that while using all the Factors to determine Clusters either 4-8 clusters or 200 cluster groups can be formed which can have similarities among them. More number of clusters implies greater variance (R-square) is explained. However, at some point of time adding new clusters will decrease the efficiency of clustering and more number of clusters is not an efficient model. 

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op1.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op2.png)

Cluster Observations Test using K-means:

Since from above test we can observe that number of clusters can be taken between 4 and 8, I performed trial and error to fix the value at 4 clusters to perform K-means for the Cluster Observation test to observe the results.

Though 7 clusters explain better than 4 clusters the data is not equally distributed amongst them.

And by not using Centroid update parameter, centroids are not recomputed after each iteration of the algorithm. By not using Centroid update parameter we do not force the algorithm to converge to a result. And randomizing centroids can give a better outcome.

The clusters are divided into 4 clusters:
- Cluster 1: Frequency of 1439
- Cluster 2: Frequency of 626
- Cluster 3: Frequency of 899
- Cluster 4: Frequency of 176

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op3.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op4.png)

The variance explained by the model is 32%.

Conclusion: All the factors together do not play a significant role in the clusters. Multiple permutations and combinations were used to determine the factors that can force the data into significant clusters. But by using K-means we are forcing the data into clusters. 

## Test-2: Clustering US Counties based on Race

For this analysis, I wanted to check if all the counties can be grouped according to the factor of Race and if Counties can be forced to form clusters. 

Cluster observations (**Average linkage**) technique was used to find out if that counties have significant clustering among them on the basis of race. 

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op5.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op6.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op7.PNG)

Inference : 

From the Criterion of number of clusters graph, a dip at 0 is observed on the number of clusters = 4-6 and at 25. More number of clusters does not mean the counties are efficiently clustered. Observing the R-square value for the number of cluster 4 is 0.353 and for number of clusters 6 is 0.506. There is however no much significant difference. 

For better analysis I decided to make the number of Clusters = 4 since the data given includes population of African-American, Hispanics and Asians; we can try to get 4 clusters which can show grouping of General US Population Counties (White Dominant), African-American Dominant Counties, Hispanic Dominant Counties and Asian Dominant Counties. I have used **K means** technique to come up with the solution.

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op8.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op9.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op10.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/op11.png)

Test and Inputs:
K-Means Clustering with number of Clusters = 4
Factors: Black %, Hispanic %, Asian %

Inference: 
-	From the outputs, it is clearly visible that the 4 clusters which are formed significantly define their underlying race amongst counties. 
-	Cluster 1 has a frequency of 2468 observation and represents the general us population which is white dominant with a mix of all other races. 
-	Cluster 2 with 450 observations represents the African American dominant counties with mean value 0.46 for Black
-	Cluster 3 with 207 counties represent the Hispanic dominant counties with their mean value of 0.46
-	Cluster 4 with 15 counties represent the Asian dominant counties with mean of 0.52. 

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl1.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl2.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl3.png)

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl4.png)

Related Inference:
-	Cluster 1 with general US Population has an average Income HH of $34K, average Highschool graduate percentage of 71.6%, Birthrate of 124
-	Cluster 2 with African American dominant counties have an average Income HH of $27.8K, average Highschool graduate percentage of 60.9%, Birthrate of 14.3
-	Cluster 3 with Hispanic dominant counties have an average Income HH of $29.2K, average Highschool graduate percentage of 64.7%, Birthrate of 15.7
-	Cluster 4 with Asian dominant counties have an average Income HH of $44.6K, average Highschool graduate percentage of 77.7%, Birthrate of 15.2

The above Inference shows that Asian dominant counties have the highest Household Income and Highest Highschool graduate percentage. 

The African American dominant counties have the lowest Household income and lowest high school graduate percentage.

The below Tableau representation shows counties clustered based on race:

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl5.png)

Quality of the K means cluster model:
	 
   The above model is a true indicator of clustering among the counties based on race and the quality of this solution is significantly better compared to the model from previous test where all the models are taken in determining the clustering. Since, the 4 clusters show significant dominance of specific race in each cluster from the cluster means table and factors like Highschool Graduates, Household Income and Birthrate are significantly different amongst the race dominant counties, I conclude by stating that this model is nearly perfect in clustering counties. 
   
 ## Test-3: Clustering US Counties based on Population Change
 
 For this analysis, I wanted to check if all the counties can be grouped according to the factor of Population Change and if Counties can be forced to form clusters. And, from the clustered results, I would like to do some inference if that clustering based on population change is affecting other parameters of our dataset. 

From the cluster observation (average linkage method), the criterion for the number of clusters graph meets zero at number of clusters value <3. From the cluster history table, the R-square value for number of cluster 3 is 0.60 which implies that around 60% of variance is explained for number of clusters 3. 

Therefore, I would like to perform the K means test keeping 3 as number of clusters to determine if the clustering can be done on the basis of population change and income HH. 

On performing K means clustering analysis, the counties were clustered based on population change and income. 

-	Cluster 1 with a frequency of 906 observation has more negative population change and low household income. This implies that the population are leaving the counties because of low income to areas with better income prospects. 

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl6.png)

-	Cluster 2 with a frequency of 583 observations has positive population change and high household income. This implies that these are counties with good job opportunities and high household income thereby inviting more people to come in. 

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl7.png)

- Cluster 3 has frequency of 1651 observations are neutral counties with no significant population change and have median household income. 

![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl8.png)

The below Tableau representation shows counties clustered based on population change:
![alt_text](https://github.com/mullapudirajaprashanth/US-County-Data---Statistical-Analysis/blob/master/Images/cl9.png)
