# Cryptocurrencies
Use unsupervised Machine Learning techniques to analyze cryptocurrency data

## Project Overview

We have the chance to pitch an investment in cryptocurrencies to the firm Accountability Accounting. We know that bitcoin's popularity has caused a cost hop that makes it exorbitant for some new investors. In any case, there are many cryptocurrencies accessible at more reasonable costs. We will discover trends that will convince the firm to invest in these new currencies. This project is perfect for applying unsupervised machine learning.

We will work on how to process data to use an unsupervised model. We will work primarily with the K-means algorithm, the main unsupervised algorithm that groups similar data into clusters. We will build on this by speeding up the process using principal component analysis (PCA), which employs many different features. Finally, we will make our models more efficient using principal component analysis.

Follow below the goals for this project:

1) Objective 1: Preprocessing the Data for PCA
2) Objective 2: Reducing Data Dimensions Using PCA
3) Objective 3: Clustering Cryptocurrencies Using K-means
4) Objective 4: Visualizing Cryptocurrencies Results

## Resources

* Data Source: [crypto_clustering.ipynb](https://github.com/DougUOT/Cryptocurrencies/blob/main/crypto_clustering.ipynb). The database is available on [crypto_data.csv](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/crypto_data.csv) 
* Software & Data Tools: Python 3.8.8, Visual Studio Code 1.64.2, Jupyter Notebook 6.4.8, and pandas 1.4.1

## Results & Code

### Objective 1: Preprocessing the Data for PCA

  * Read in the crypto_data.csv to the Pandas DataFrame named crypto_df.
  * Keep all the cryptocurrencies that are being traded.

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_1_1.PNG)

  * Drop the IsTrading column.
  * Remove rows that have at least one null value.
  * Filter the crypto_df DataFrame so it only has rows where coins have been mined.

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_1_2.PNG)

  * Create a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
  * Remove the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
  * Use the get_dummies() method to create variables for the two text features, Algorithm and ProofType, and store the resulting data in a new DataFrame named X.
  * Use the StandardScaler fit_transform() function to standardize the features from the X DataFrame.

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_1_3.PNG)

### Objective 2: Reducing Data Dimensions Using PCA

  * Continue using the crypto_clustering.ipynb file from Objective 1 where you’ve already performed the preprocessing steps.
  * Using the information we’ve provided, apply PCA to reduce the dimensions to three principal components
  * Create a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_2.PNG)

### Objective 3: Clustering Cryptocurrencies Using K-means

  * Continue using the crypto_clustering.ipynb file that you used in Objective 2 to reduce the dataset to three dimensions
  * Using the pcs_df DataFrame, create an elbow curve using hvPlot to find the best value for K.

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_3_1.PNG)

  * Next, use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data
  * Create a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index should be the same as the crypto_df DataFrame
  * Add the CoinName column that holds the names of the cryptocurrencies, which you created in Step 7 of Objective 1, to the clustered_df.
  * Add another new column to the clustered_df named Class that holds the predictions, i.e., model.labels_,

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_3_2.PNG)

### Objective 4: Visualizing Cryptocurrencies Results

  * Continue using the crypto_clustering.ipynb file from Objective 3 where you have predicted the K clusters for the cryptocurrencies’ data.
  * Create a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters from the clustered_df DataFrame
  *  * Add the CoinName and Algorithm columns to the hover_name and hover_data parameters, respectively, so each data point shows the CoinName and Algorithm on hover

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_4_1.PNG)

 
  * Create a table with tradable cryptocurrencies using the hvplot.table() function.
  * Print the total number of tradable cryptocurrencies in the clustered_df DataFrame
  * Use the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of zero and one


![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_4_2.PNG)

  * Create a new DataFrame using the clustered_df DataFrame index that contains the scaled data you created in Step 5
  * Add the CoinName column from the clustered_df DataFrame to the new DataFrame
  * Add the Class column from the clustered_df DataFrame to the new DataFrame
  * Create an hvplot scatter plot with x="TotalCoinsMined", y="TotalCoinSupply", and by="Class", and have it show the CoinName when you hover over the the data point

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Capture18_4_3.PNG)

## SUMMARY

Follow below some highlights and findings related to the analyze cryptocurrency data predictions:

* The prediction 3 (PC 3) has the better findings related the CoinName
* The Waves, Poa Network, LitecoinCash, Acute Angle Cloud and BiblePay (CoinName) are the top new cryptocurrency to recommend for investments as according to the analysis
* In order to diversify the investment portfolio, I would also recommend the CoinName BitTorrent. 
* It is important to mentioned that the results generated from unsupervised Machine Learning, may be less precise as information isn't labeled, and algorithms don't have a clue about the exact output ahead of time.

![](https://github.com/DougUOT/Cryptocurrencies/blob/main/Resources/Images/Extra%20Analysis_Module18.PNG)

## RECOMMENDATIONS

We suggest a future analysis comparing the new currencies accessible at more reasonable costs vs the most popular bitcoins available to investors.
