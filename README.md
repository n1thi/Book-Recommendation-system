# Book-Recommendation-system

## Background and Objectives:

Regular book recommendation systems usually don't offer personalized suggestions. They
usually tend to just recommend books with filters like, most read books and most rated books.
However, this fails to consider the personal preferences, demographics, and reading behaviours of
users.  
The conventional book recommendation systems currently available are mostly single
dimensional, focusing mainly on recommending books based on filters like, most read books, most
liked books, trending books, latest books and most rated books. As a result, users often struggle to
find book recommendations that align with their interests.

## Potential Contribution:

This project aims to create a smart system that suggests books based on what users like,
what they've read before, and their personal details. This system will give each user suggestions that
match their interests and introduce them to new books. It will also fix the problem of existing
systems not being personal enough, by considering factors like age, what users liked before, and
where they live.

## An Overview of Data:

Three datasets: books, users, and ratings.
The books dataset contains a unique identifier “Book ID(ISBN)”, “Book-Title”, “Book-Author”,” Year-of
Publication”, “Publisher” along with some links to images as columns “Image-URL-S”, “Image-URL-L”,
and “Image-URL-M”.
The user dataset includes unique user ID, along with the user’s location and age.
The rating dataset consists of user ID, ISBN of the rated book, and corresponding rating. Notably, the
user ID and book ISBN serve as foreign keys referenced from the user and rating datasets,
respectively.

## Data Pre-processing and Exploratory Data Analysis (EDA) :

- Data is initially loaded with appropriate encoding settings for different datasets ('UTF-8'
  for books, 'Latin1' for users and ratings).
- Clear formatting issues.
- Convert data types to ensure consistency across datasets.
- Handle missing values, particularly in the age and ratings data.
- Rename columns to enhance code readability and accessibility.
- Filter out irrelevant data and outliers.
- Encode categorical data and correct structural errors.
- Adjusting data types for merging datasets.
- Validating and extracting important features.

- Utilized various statistical and visual analysis techniques, including:
- Histograms analyze the frequency of book ratings and age distributions.
- Scatterplots and heat maps to study the relationships between age categories and
  publication years.
- Correlation matrix to assess the relationships among publication year, age, and book
  ratings.
- Box plots for visualizing distributions and identifying outliers in book ratings and reader
  age.
- Bar graphs illustrate the average book ratings by country and the frequency of users by
  country.

## Evaluating and Comparing Recommendation Models:

Models Used:

#### Linear Regression:

- Purpose: Predict book ratings using user age.
- Performance: Demonstrated poor effectiveness with an R-squared value
  indicating negligible explanatory power and low predictive performance.

#### K-Means Clustering:

- Purpose: Segment books into clusters for recommendation based on
  similar attributes.
- Performance: Achieved a suboptimal silhouette score, indicating poor
  clustering effectiveness.

#### Decision Trees:

- Purpose: Recommend or predict book ratings based on a variety of
  attributes including book title, author, and user demographic info.
- Performance: Modest accuracy with good interpretability but limited
  ability to capture complex user preferences.

#### K-Nearest Neighbors (KNN):

- Purpose: Suggest books by finding similar users and their preferences.
- Performance: Demonstrated low accuracy, highlighting challenges in
  matching user preferences based solely on demographic data.

#### Naive Bayes:

- Purpose: Classify user preferences for books based on demographic and
  book interaction data.
- Performance: Provided moderate predictive accuracy with insights into
  user preferences but highlighted the need for more nuanced data
  handling.

#### Collaborative Filtering (SVD):

- Purpose: Offer book recommendations based on user-item interaction
  patterns.
- Performance: Best performing model in terms of accuracy and user
  satisfaction, effectively handling sparse data and capturing underlying
  patterns in user preferences.

### Performance Visualization:

For each model, generated Precision-Recall bar plots and Accuracy versus
Number of Recommendations plots. These visualizations were crucial for
evaluating model effectiveness and were derived from comparing model
predictions against a ground truth set.

## Used flask to create a UI

- Each function contains flask code for each element in the web application. The backend
  connection for each model is established properly.
- Singular Value Decomposition (SVD) was employed to break down the rating matrix  
  into latent factors that capture underlying user preferences and book characteristics.
- Using the decomposed matrices from SVD, predicted how a specific user would rate
  books they have not yet interacted with.
- We identified books not rated by the user, merged predicted ratings with book  
  information, and ranked them to select the top recommendations.
- The system provides a list of top recommended books with predicted ratings for the  
  given user.
- A histogram of prediction errors can be generated to assess the accuracy of the  
  recommendations and identify potential areas for improvement.

## User Interface working instruction:

- Use the below commands to run Book recommendation application in the Flask web
  user interface with the help of HTML, CSS and Bootstrap. Also involves Jinga2 for
  templating.
- Install the flask python module with the command → pip3 install flask
- Then run our application code as a python module with the command
  →"C:/Program Files/Python312/python.exe"
  C:\Users\swani\book_recommendation_system\app.py
- The user is given the option to upload a dataset. Based on the available data in this dataset,
  the user will receive book recommendations. The dataset is provided in src folder.
- The user is presented with a screen offering two choices:
  1. Recommendation by Popularity
  2. User-specific recommendations (Machine Learning-based Recommendation)
- If the user opts for Recommendation by Popularity, the user should upload their dataset and
  the code ranks all the books by the popularity metric in descending order, recommending
  the top 50 most popular books.
- To choose user-specific recommendations, the user can upload their dataset and their user
  ID. The recommendation model, which utilizes collaborative filtering, will predict the top
  10 books that the user is likely to enjoy. (Note: the user must have rated at least 100 books
  to receive user-specific recommendations, and as there are only 290 users in our dataset that
  meet this requirement, any user ID above 290 will not work.)
- A graph is visualized at the end of user specific recommendations page that shows a
  histogram graph of prediction errors.
