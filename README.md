# Artificial Intelligence and Machine Learning project on recommender systems

-Lischi Maria Chiara (271281)
-Pacielli Gabriele (267701)
-Spadaccia Matteo (277141)

## Section 1) Introduction
As a team, we have been inquired to increase revenues of a prestigious fashion firm improving the recommender system of 
the platform testing different recommendation systems.

## Section 2) Methods
### Data understanding
We received three dataset with relevant information about: Customers, transactions and articles. To understand the meaning of these data we conduced a deep explanatory data analysis
The first dataset, recsys_articles, is composed by the following attributes: an articled id linked to the product name, the product type id with its following name,the colour of the product with very detailed attributes, then the department, group of membership, section and type of garment.
The second dataset, recsys_customers, on the other hand, gives information about the customer which is uniquely identified by the customer id, then tells us whether the customer is part of the special club member and if receives the newsletter or not and finally the age.
The third dataset, recys_transactions, last but not least concerns the purchases done by each customer identified in the customer dataset on a certain date.

### Preparing data 
During the EDA we found null values in the customer dataset. We calculated the percentage of null values and then decided that would have been better removing those values instead of filling with false data. The same operation has been executed with the article dataset 
because of some undefined or unknown values. For the sake of simplicity we created dataframes when needed. 

To process data it is crucial to understand its features invisible at the naked eye, using different python packs such as:

1) Pandas 
2) Numpy 
3) Sklearn 
4) Matplot.lib
5) Seaborn
6) Collection 

##Articles 



