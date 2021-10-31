# UWFinTech_Module10_Challenge
Assignment on Unsupervised Learning, an approach to assembling investment portfolios that are based on cryptocurrencies. 

## Technologies Used

Leveraging Jupyter Notebook
Gitbash CLI is used to pull and push the code from local repository to remote repository
Code written with the help of Jupyter Notebook.

---

## Libraries and Dependencies

import pandas as pd
import hvplot.pandas
from pathlib import Path
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler

## Steps
The steps for this project are divided into the following sections:

python jupyter notebook file is crypto_investments.ipynb

Import the Data (Resource folder)
Prepare the Data
Find the Best Value for k Using the Original Data
Cluster Cryptocurrencies with K-means Using the Original Data
Optimize Clusters with Principal Component Analysis
Find the Best Value for k Using the PCA Data
Cluster the Cryptocurrencies with K-means Using the PCA Data
Visualize and Compare the Results
IMPORTANT
k refers to lowercase k. The instructions will specify "uppercase K" where necessary.

Find the Best Value for k Using the Original Data
In this section, you will use the elbow method to find the best value for k.

Code the elbow method algorithm to find the best value for k. Use a range from 1 to 11.

Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

```

elbow_curve_original = df_elbow.hvplot.line(
    x="k", 
    y="inertia", 
    title="Elbow Curve", 
    xticks=k
)
elbow_curve_original

```

Answer the following question: What is the best value for k?
Answer: As per elbow curve the best value for k would be 4.


Cluster Cryptocurrencies with K-means Using the Original Data
In this section, we used the K-means algorithm with the best value for k (found in the previous section) in order to cluster the cryptocurrencies according to the price changes of cryptocurrencies provided.

Initialize the K-means model with four clusters by using the best value for k.

Fit the K-means model using the original data.

Predict the clusters to group the cryptocurrencies using the original data. View the resulting array of cluster values.

Add a new column to the DataFrame with the original data to store the predicted clusters.

Using hvPlot, create a scatter plot by setting x="price_change_percentage_24h" and y="price_change_percentage_7d". Colored the graph points with the labels found using K-means. Then, add the crypto name in the hover_cols parameter to identify the cryptocurrency represented by each data point.

```
predicted_clusters_plot = df_market_data_scaled.hvplot.scatter(
    x="price_change_percentage_24h",
    y="price_change_percentage_7d",
    by="predicted_clusters",
    hover_cols = ["coin_id"],
).opts(yformatter="%.0f")

predicted_clusters_plot

```

Optimize Clusters with Principal Component Analysis
In this section, you will perform a principal component analysis (PCA) and reduce the features to three principal components.

Create a PCA model instance and set n_components=3.

Use the PCA model to reduce to three principal components. View the first five rows of the DataFrame.

Retrieve the explained variance to determine how much information can be attributed to each principal component.

Answer the following question: What is the total explained variance of the three principal components?

Create a new DataFrame with the PCA data. Be sure to set the coin_id index from the original DataFrame as the index for the new DataFrame. Review the resulting DataFrame.

Find the Best Value for k Using the PCA Data
In this section, you will use the elbow method to find the best value for k using the PCA data.

Code the elbow method algorithm and use the PCA data to find the best value for k. Use a range from 1 to 11.

Plot a line chart with all the inertia values computed with the different values of k to visually identify the optimal value for k.

Answer the following questions: What is the best value for k when using the PCA data? Does it differ from the best k value found using the original data?
The total explained variance of the three principal components is 0.8844285111826466


Cluster Cryptocurrencies with K-means Using the PCA Data
In this section, you will use the PCA data and the K-means algorithm with the best value for k (found in the previous section) in order to cluster the cryptocurrencies according to the principal components.

Initialize the K-means model with four clusters by using the best value for k.

Fit the K-means model by using the PCA data.

Predict the clusters to group the cryptocurrencies by using the PCA data. View the resulting array of cluster values.

Add a new column to the DataFrame with the PCA data to store the predicted clusters.

Using hvPlot, create a scatter plot . Colored the graph points with the labels found using K-means. Then, add the crypto name in the hover_cols parameter to identify the cryptocurrency represented by each data point.

```
elbow_curve_pca_data = df_elbow_pca.hvplot.line(
    x="k_pca", 
    y="inertia_pca", 
    title="Elbow Curve PCA data", 
    xticks=k_pca
)
elbow_curve_pca_data

```

Visualize and Compare the Results
In this section, we visually analyzed the cluster analysis results by observing the outcome with and without using the optimization techniques.
```

predicted_clusters_pca = df_market_data_pca.hvplot.scatter(x= "PC1", y="PC3" , by="predicted_clusters", title="Scatter Plot by stock segments")

predicted_clusters_pca
```

Create a composite plot using hvPlot and the plus (+) operator to compare the elbow curve that you created to find the best value for k with the original data and the PCA data.

```

elbow_curve_original + elbow_curve_pca_data

```

Create a composite plot using hvPlot and the plus (+) operator to compare the cryptocurrencies clusters using the original data and the PCA data.

```
predicted_clusters_plot + predicted_clusters_pca
```

Answer the following question: After visually analyzing the cluster analysis results, what is the impact of using fewer features to cluster the data by using K-means?

The number of optimum clusters with original data and pca data is 4. The impact of using fewer features to cluster makes it easy to choose the best value of k. As per the elbow curve drawn after pca value is clearly 4.



### Contributors
This project is designed by Swati Subhadarshini 
Emaid id: sereneswati@gmail.com
LinkedIn link: https://www.linkedin.com/in/swati-subhadarshini