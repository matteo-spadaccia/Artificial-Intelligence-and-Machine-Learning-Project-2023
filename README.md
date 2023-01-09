# Artificial Intelligence and Machine Learning project on recommender systems
- Lischi Maria Chiara (271281)
- Pacielli Gabriele (267701)
- Spadaccia Matteo (277141)

## Section 1) Introduction
This work consists in the implementation of different recommender systems, made for a clothing store. Before deeping into the recommender systems, a large part of the project is dedicated to the Exploratory Data Analysis and visualization of the data.

## Section 2) Methods
We worked over three different datasets, which we analyzed deeply through EDA.

### Data overview
The three datasets we worked over are:
- 'recsys_customers.csv', which contains information about 41253 different customers. For each customer, we have data about their age, and whether or not they have a club membership or are subscribed to the fashion newsletter of the clothing shop. 
- 'recsys_articles.csv', which contains information about 6536 articles, for each of which we know the value of 21 different attributes, mainly concerning the type, colour and group of the articles.
- 'recsys_transactions.csv', which contains informations about 369113 transactions; specifically the date in which the transaction happened, the costumer who made it and the article that was bought are known. 

### Data preparation
We loaded the data into three different pandas dataframes and cleaned them getting rid of invalid values, that were present both the customers and the articles datas
ets. This choice is justified by the fact that the percentage of invalid data was very low with respect to the total amount of data available.

# Exploratory Data Analysis and Data Visualization
To gain a deeper understanding of the dataset, we examineted and analyzed it with the aim to have a good understanding of it for in order to be able to build different recommender systems. The performed analysis was made for understanding the characteristics of the dataset, identifying patterns and relationships. Techniques of data visualization, statistical analysis, and data transformation were used. 

The python packages that we mainly used are: 
- Numpy;
- Pandas;
- Seaborn;
- Matplotlib;

During this tools, we computed the age distribution of the customers, findable above:
<img src="images/age distribution.png">



