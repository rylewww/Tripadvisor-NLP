
# Tripadvisor Review NLP Project
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/3e/Tripadvisor_Logo_circle-green_vertical-lockup_registered_RGB.svg/1200px-Tripadvisor_Logo_circle-green_vertical-lockup_registered_RGB.svg.png" alt= "Tripadvisor Logo" width="650" height="300">
Authors: Anisha Malholtra & Ryan Lewis

# Overview
This project applies Natural Language Processing to a dataset of Tripadvisor hotel reviews. NLP allows computers to interact with text data, deriving the semantic value of words in relation to the target. In this project, we classify whether we consider a review as 'poor', 'average', or 'excellent' by utilizing different models in efforts to identify which model produces the highest accuracy & F-1 score.

# Business Problem
Businesses around the world rely on reviews to better understand customer satisfaction. Most review platforms use a 'scaled rating system', such as, Amazon 'star-ratings' or Youtube's like or dislike' system, however many businesses do not have such rating systems. Therefore, by classfying different Tripadvisor hotel reviews we are able to provide a sentiment for each review which can help both consumers and business owners understand how valuable a product or service is.


# Data & Data Preprocessing
The data in this project was pulled from Kaggle. It includes text review and a numbered rating (1 - 5) of over twenty-thousand different Tripadvisor hotel reviews. In order to prepare our data for modeling we used several preprocessing techniques:
* removing punctuation
* lower-cased words
* removing stop-words
* assigned part of speech tags
* lemmatizing words
* tokenized remaining words

# Exploratory Data Analysis
After we completed our preprocessing, we explored our cleaned & tokenized reviews in order to better understand the impact of certain words. 

<p float="left">
  <img src="https://github.com/rylewww/Phase4Project/blob/master/images/old_rating.png" width="450" height="400" />
  <img src="https://github.com/rylewww/Phase4Project/blob/master/images/new_rating.png" width="450" height="400" />
  </p>
  
  Due to the class imbalance displayed in the first graph above, we further grouped our review scores as shown in the second plot:
  * 1 & 2 -- 'poor'
  * 3 & 4 -- 'average'
  * 5 -- 'excellent'
  
  Based on our newly created target, the word clouds below show which words appear most frequently in each category.
  
<p float="left">
  <img src="https://github.com/rylewww/Phase4Project/blob/master/images/poor.png" width="310" height="300" />
  <img src="https://github.com/rylewww/Phase4Project/blob/master/images/average.png" width="310" height="300" />
  <img src="https://github.com/rylewww/Phase4Project/blob/master/images/excellent.png" width="310" height="300" />
</p>

We included the plot below to show the various parts of speech and other review characteristics per each target category. A key takeaway to note, is that the word count, character count and average length of sentence is higher for 'poor' reviews compared to others. 

<img src="https://github.com/rylewww/Phase4Project/blob/master/images/pos.png" >

# Vectorizing & Modeling 
In order for our model to be able to interpret the review data we needed to vectorize our processed reviews. We used the TF-IDF vectorizer which not only takes into account how frequent a word appears in a document, but also how unqiue the word is in the overall corpus. We set our paramters to only include words that appear in at least 5% and max 90% of the documents in the corpus.

After vectorization, we fit several different models to evaluate and compare which one outputs the highest accuracy & F-1 score. In order to accurately compare each model against one another, we performed a grid-search to determine the optimal hyperparameters for each model. Our results are as follows:

<img src="https://github.com/rylewww/Phase4Project/blob/master/images/models.png" >

Per the above, our top three models were:
* Logistic Regression w/ PCA
* Logistic Regression w/o PCA
* LightGBM

Confusion matrices for these three models are below:

<img src="https://github.com/rylewww/Phase4Project/blob/master/images/confusion.png" >

# Conclusion 
Our logistic regression with PCA model did the best at identifying the 'poor' reviews, whereas 'average' and 'excellent' were relatively similar across the three models. Therefore, the logistic regression model using PCA was our final model as it also has both the highest accuracy and F-1 scores and was not overfit to our training data.

# Next Steps
* Include exogenous variables (e.i. sentence length & subjectivity value)
* Utilize deep-learning to create potentially more accurate models
* Incorporate n-grams
* Try different preprocessing techniques
* Bring in new unseen data to assess our model performance

# Reference
* Dataset -- https://www.kaggle.com/andrewmvd/trip-advisor-hotel-reviews
* Tripadvisor -- https://tripadvisor.mediaroom.com/US-about-us

# Repository Structure
```
├── Data
├── Images
├── Notebooks
│   └── Data_Analysis.ipynb
│   └── Raw_Notebook.ipynb
│   └── Draft.ipynb
├── README.md
├── Final.ipynb
└── Tripadvisor_NLP.pdf
