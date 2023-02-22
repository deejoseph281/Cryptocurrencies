# Cryptocurrencies
Use unsupervised Machine Learning techniques to analyze cryptocurrency data

## Project Overview

The client is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they would like to see a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment.

The data we are working with is not ideal, so it will need to be processed to fit the machine learning models. Since there is no known output for what we are looking for, we have decided to use unsupervised learning. To group the cryptocurrencies, we decided on a clustering algorithm. We’ll use data visualizations to share findings with the board.

Our project includes four technical analysis parts:

1) Part 1: Preprocessing the Data for PCA
2) Part 2: Reducing Data Dimensions Using PCA
3) Part 3: Clustering Cryptocurrencies Using K-means
4) Part 4: Visualizing Cryptocurrencies Results

## Analysis

### Part 1: Preprocessing the Data for PCA

  * Read in the crypto_data.csv to the Pandas DataFrame named crypto_df.
  * Keep all the cryptocurrencies that are being traded.
  * Drop the IsTrading column.
  * Remove rows that have at least one null value.
  * Filter the crypto_df DataFrame so it only has rows where coins have been mined.
  * Create a new DataFrame that holds only the cryptocurrency names, and use the crypto_df DataFrame index as the index for this new DataFrame.
  * Remove the CoinName column from the crypto_df DataFrame since it's not going to be used on the clustering algorithm.
  * Use the get_dummies() method to create variables for the two text features, Algorithm and ProofType, and store the resulting data in a new DataFrame named X.
  * Use the StandardScaler fit_transform() function to standardize the features from the X DataFrame.

![](https://static.bc-edx.com/data/do-v2/m19/img/data-18-challenge-crypto-df-DataFrame-shows-four-columns.png)

### Objective 2: Reducing Data Dimensions Using PCA

  * Continue using the crypto_clustering.ipynb file from Objective 1 where you’ve already performed the preprocessing steps.
  * Using the information we’ve provided, apply PCA to reduce the dimensions to three principal components
  * Create a new DataFrame named pcs_df that includes the following columns, PC 1, PC 2, and PC 3, and uses the index of the crypto_df DataFrame as the index.

![](https://static.bc-edx.com/data/do-v2/m19/img/data-Module-18-Challenge-1-clustering-cryptocurrencies-using-k-means.png)

### Objective 3: Clustering Cryptocurrencies Using K-means

  * Continue using the crypto_clustering.ipynb file that you used in Objective 2 to reduce the dataset to three dimensions
  * Using the pcs_df DataFrame, create an elbow curve using hvPlot to find the best value for K.
  * Next, use the pcs_df DataFrame to run the K-means algorithm to make predictions of the K clusters for the cryptocurrencies’ data
  * Create a new DataFrame named clustered_df by concatenating the crypto_df and pcs_df DataFrames on the same columns. The index should be the same as the crypto_df DataFrame
  * Add the CoinName column that holds the names of the cryptocurrencies, which you created in Step 7 of Objective 1, to the clustered_df.
  * Add another new column to the clustered_df named Class that holds the predictions, i.e., model.labels_,

![](https://static.bc-edx.com/data/do-v2/m19/img/data-18-challenge-dataframe-clustered-df-visualizing-results.png)

### Objective 4: Visualizing Cryptocurrencies Results

  * Continue using the crypto_clustering.ipynb file from Objective 3 where you have predicted the K clusters for the cryptocurrencies’ data.
  * Create a 3D scatter plot using the Plotly Express scatter_3d() function to plot the three clusters from the clustered_df DataFrame
  *  * Add the CoinName and Algorithm columns to the hover_name and hover_data parameters, respectively, so each data point shows the CoinName and Algorithm on hover

 
  * Create a table with tradable cryptocurrencies using the hvplot.table() function.
  ![](https://static.bc-edx.com/data/do-v2/m19/img/data-18-challenge-hvplot-table-showing-all-tradable-cryptocurrencies.png)

  * Print the total number of tradable cryptocurrencies in the clustered_df DataFrame
  * Use the MinMaxScaler().fit_transform method to scale the TotalCoinSupply and TotalCoinsMined columns between the given range of zero and one
  * Create a new DataFrame using the clustered_df DataFrame index that contains the scaled data you created in Step 5
  * Add the CoinName column from the clustered_df DataFrame to the new DataFrame
  * Add the Class column from the clustered_df DataFrame to the new DataFrame

![](https://static.bc-edx.com/data/do-v2/m19/img/data-18-challenge-tradable-cryptocurrencies-DataFrame.png)

  * Create an hvplot scatter plot with x="TotalCoinsMined", y="TotalCoinSupply", and by="Class", and have it show the CoinName when you hover over the the data point

![](https://static.bc-edx.com/data/do-v2/m19/img/data-18-challenge-hvplot-scatter-plot.png)
