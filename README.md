# Artificial Intelligence and Machine Learning project - recommender systems
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

### Preparation of data
We loaded the data into three different pandas dataframes and cleaned them getting rid of invalid values, that were present both the customers and the articles datasets. This choice is justified by the fact that the percentage of invalid data was very low with respect to the total amount of data available.

### Exploratory Data Analysis and Data Visualization
To gain a deeper understanding of the dataset, we examineted and analyzed it with the aim to have a good understanding of it for in order to be able to build different recommender systems. The performed analysis was made for understanding the characteristics of the dataset, identifying patterns and relationships. Techniques of data visualization, statistical analysis, and data transformation were used. 

The python (version 3.11.1) packages that we mainly used are: 
- Numpy;
- Pandas;
- Seaborn;
- Matplotlib;

#### Articles dataset
We grouped articles following the two major features in our possesion representing them:
- their colours
<img src="images/articles per colours.png">

- their type
<img src="images/articles per garment group.png">

#### Customers dataset
For the customers and the transactions datasets, we computed statistics concerning:
- the age distribution of the customers:
<img src="images/age distribution.png">

- the percentage of the customers which are club member over the total number of customers. 
<img src="images/club members over total.png">
<img src="images/club members per age range.png">

- the percentage of the customers subscribed to the fashion news over the total number of customers. 
<img src="images/subscribers over total.png">
<img src="images/subscribers per age range.png">

The reason of the high similarity of these features is due to their high correlation (about 0.98): it is very likely that a customer being a club member will also be a subscriber to the fashion news letter and vice versa.

#### Transactions dataset
Crossing the information between the articles and the transactions datasets, we managed to compute the average purchase per age range, dividing the customers in age bins of five-years:
<img src="images/purchases per age range.png">

## Section 3) Experimental design
### Content-based recommander systems
We built a recommender system to suggests new articles to a user basing on the user's past purchases. Therefore suggesting items that are similar to the ones we already know the user has a preference for.

Similarity is measured between articles by comparing the attributes of articles that a user has previously bought with the attributes of other articles. We are going to use the cosine distance to measure similarity, which is a typical choice for content-based recommender systems. Cosine similarity works by calculating the dot product of the vectors (rows representing attribute-values that each article has), measuring how similar the directions of the vectors. The higher the cosine similarity, the more similar the items are.

The attribute choice is extremely important since it determines the types of recommendations that the system is able to make: we want to exploit as many relevant information as possible, but we also don't want to use too many attributes, because this may make the recommendation process slow and cumbersome. In order to strike a balance, we choose the following attributes for the recommendation task:

product_type;
colour_group;
section;
garment_group;

This choice comes from the need of taking under consideration attributes which span in a relatively high range of values and contribute with different kind of information. Once determined the piece of information to consider, we decided to use the attribute containing the numerical value.

In order to start building the content-based filtering recommender, we set up the dataset so that each row represent a different article and columns represent all the possible values that each of the attributes we considered can assume. To do so, we manipulate the columns representing the choosen attributes in the articles dataframe creating a new one (art_features_df). In this new dataframe each row contains a series of binary features: "1" indicates that the article falls under a given attribute value, while "0" indicates that it does not.

Since our initial goal was to recommend items directly to customers basing to their previous purchases (and not items from a single item), we will improve our content-based filtering system. We want to build a function that receive as input the customer id, and basing on all the purchases made by that customer, returns n recommended items. This function works by finding, for each article purchased by the user, 20 suggested items (by calling the basic content-based recommandation filter defined above). Once it has all this articles, it gives more weights to the ones that are mentioned several times. It finally returns the 10 articles that are mentioned more.

### Collaborative recommender system
For the collaborative filtering, we start by transforming our data into a "utility matrix" in which rows represent customers and columns represent articles. In order to do that, we need first to map each article to its index (and vice versa) and each customer to its index (and vice versa), then for generating it we call the scipy.sparse.csr_matrix method from sklearn library.

Once we have created the utility matrix, we need to be sure that we can retrieve reliable data from it. To do so, we need to check for the sparsity of the matrix, that is a measure of how many non-zero values are present in the matrix with respect to the overall number of values. For utility matrices, significant results are obtained if the sparsity is at least of 0.5%. Since our utility matrix has sparsity 0.11%, we increased it by getting rid of rows and columns which have less than 20 non-zero values. We build the function implementing the recommender system using the k-NN algorithm.

## Section 4) Results
Conducting manual test over the outputs of the different recommanding systems, we can assert that we built useful softwares to help an eventual cloths shop to enhance the offer customization. However, the best recommander system we would suggest to adopt is the second one, taking as input a customer id and returning various recommanded articles: it seems to be the most precise to a human-preferences manual test and it does not proceed with huge data loss (instead the case of the collaborative recommander system, due to the matrix sparsity).

## Section 5) Conclusions
During this group work we had the opportunity to test and practice our practical knowledge in the basics of reccommander systems creation. We would indicate as possible future work the the software refining in precision and the practice with other recommander system types; nevertheless we are totally satisfied with the actual results of our work, making us more confident with the skills we learnt during the related course.
