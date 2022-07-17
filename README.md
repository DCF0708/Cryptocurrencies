# Cryptocurrencies
</br>
</br>
</br>

## The Problem...
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; *"...Martha is a senior manager for the Advisory Services Team at Accountability Accounting, one of your most important clients. Accountability Accounting, a prominent investment bank, is interested in offering a new cryptocurrency investment portfolio for its customers. The company, however, is lost in the vast universe of cryptocurrencies. So, they’ve asked you to create a report that includes what cryptocurrencies are on the trading market and how they could be grouped to create a classification system for this new investment."* 
</br>
</br>

## The Solution: 
- **Deliverable 1**: Preprocess the Crypto data to run Principle Component Analysis.
    - The data is put into a DataFrame (**crypto_df**) and cleaned in the order that follows:
        - All currencies that are *not* actively traded are discarded.
        - All currencies *without* a working algorythm are discarded.
        - The "IsTrading" column is dropped for non-utilization reasons.
        - All rows containing *at least 1 null value* are discarded. 
        - All rows *with values > 0 for the 'TotalCoinsMined' column* are isolated and kept.
        - A new DataFrame (**cc_name_df**) is created to hold *only names of resultant currencies.*
        - The "CoinName" column is then dropped from **crypto_df**.
        - Use get_dummies() on **crypto_df** to create variables for text features.
        - Standardize data with StandardScaler() method.
        </br>
        </br> 

- **Deliverable 2**: Reduce data demensions using PCA.
    - Results in a DataFrame with an index of Crypto names, with each row holding a value for Principle Components 1, 2 and 3. For more information on understanding Principle Component Analysis, follow this [link](https://towardsdatascience.com/pca-using-python-scikit-learn-e653f8989e60)
    </br>
    </br>
    
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;![PCA Image](./images/PCA.png)
    </br>
    </br> 

- **Deliverable 3**: Clustering cryptocurrencies using K-Means.
    - The DataFrame from the Principle Component Analysis is used to generate a graph known as an "Elbow Curve". This line graph indicates the best "k" value, this value is the value at which the data can be clustered and visualized most effectively. 
    - K-Means is then ran with the value 'k=4' and each data point's cluster is predicted. The predictions are returned in array format and are appended to the data frame under the "Class" column with Class symbolizing the cluster each data point falls under.
    
     For more background information on K Means Clustering, follow this [link](https://towardsdatascience.com/understanding-k-means-clustering-in-machine-learning-6a6e67336aa1)
    </br>
    </br> 

    ![Elbow Curve](./images/elbow.png)
    </br>
    </br> 

- **Deliverable 4**: Visualizing the results.
    - The clustered data from the K-Means clustering is used in combination with the Plotly Express library to display the ML data clusters in a 3D format.
    </br>
    </br> 

    ![3D](./images/3d.png)
    </br>
    
    Note: The graphs above are the same 3D graphs pictured twice. The top graph is viewed from a top-down vantage. The bottom graph is the same graph viewed from a bottom-up vantage to emphasize the 3-dimensional nature of the visual. Each data point has a *'hover'* functionality that displays that data point's corresponding information.
    </br>
    </br>

    - The data collected from the Predictive Unsupervised Machine Learning model was joined to the data in Del. 3, and is visualized in an hvplot table for display. (Note the addition of a "Class" column.)
    </br>
    </br> 

    ![hvplot](./images/hvplot.png)
    </br>
    </br>

    - The final visualization is a 2D Scatter Plot of the results from hvplot. Note that class is denoted by color in the legend to the right of the graph.
    </br>
    </br> 

    ![hvscatter](./images/hvscatter.png)
    </br>
    </br>



