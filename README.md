![SXSW Picture]()

# South by Southwest Tweet Content

### Author: [Elizabeth Webster](https://github.com/elizabeth524)

## Overview

Analysis and natural language processing in order to create a model that will accurately predict the sentiment of a tweet.

## Business Problem

South by Southwest (SXSW) is an annual conference and festival that showcases innovations in technology and the creative arts.  In order to enhance the experience for future attendees, this company is looking to analyze the sentiments of tweets from previous years. This will give them insight on the public opinion on the conference and the brands in attendance.

Our task is to build a model that can correctly identify the sentiment of a tweet based on it's text.

## Dataset

We will be using a dataset from CrowdFlower that includes 9000 tweets relating to previous South by Southwest events. The dataset is made up of three columns, 'text', 'product', and 'sentiment'. 
The text is the written tweet.
The product identifies Apple or Google brand/product that the text is related to.
The 'sentiments' are labeled as:

* 'Negative' 
* 'Positive'
* 'No Emotion' 
* 'I can't tell' (*removed from our dataset)

## Data Cleaning

Before beginning Natural Language Processing, we needed to clean our dataset.  The steps we took were:

### Dealing with missing values
There was one missing value in our 'text' column.  We dropped this entry.
There were 5800 missing vlues in the 'product' column.  To begin with, we changed the values to reflect only 'Google' or 'Apple'.  Next, we iterated through the data to find words in the tweets relating to Google or Apple and changed their 'product' values accordingly.  This reduced our missing values to 756.  Finally, we filled the 756 missing values with 'Unknown'.
There were no missing values in our 'senitment' column.

### Removed Unnecessary Data
We also removed the entries that were labeled 'I can't tell' for their sentiment.

Final distribution of target ('sentiment') labels:
![Tweets by Sentiment](https://github.com/elizabeth524/Phase-4-Project/blob/main/Images/Sentiment%20Distribution.png)
The overwhelming majority of tweets have no emotion as their label.  By randomly assigning 'No Emotion' to all the tweets, we would be correct 60% of the time.

### Train Test Split and Baseline Model
Before performing any language processing, we split our data and created a baseline Multinomial Bayes model.  Our baseline model had a score of 60.2%, approximately the same as assigning all the tweets 'No Emotion'.  To increase the accuracy of our model, we will perform natural language processing on our text.

## Natural Language Processing

For each natural language processing step, we evaluated a new model to see if the step was helping to increase our accuracy.

### Removing Punctuation and Stopwords

By removing punctuation and stopwords, we are left with the words in the tweet that hold more semantic value.  For example, the Top 20 words in the tweets before removing stopwords were:
![Top 20 with Stopwords](https://github.com/elizabeth524/Phase-4-Project/blob/main/Images/Top20withstopwords.png)
None of these words would tell us much about the sentiment of the tweet.  However, once those stopwords are removed, our Top 20 looks like this:
![Top 20 without Stopwords](https://github.com/elizabeth524/Phase-4-Project/blob/main/Images/Top20withoutstopwords.png)
These words are more likely to have semantic meaning and influence our target('sentiment').

Our model without stopwords had a score of 60.8%, an increase, but not a substantial one.

### Lemmatization

Lemmatization reduces each token down to it's root word (for example, 'texts' and 'texting' would both be reduced to 'text'). This helps to concentrate our tweets down even further to get to the most important words.

Our model with lemmatized text had a score of 60.7%, higher than our baseline, but lower than our model without stopwords.  However, I believe it will be important to keep this step as we increase our number of features used.

### Adding Features

Finally, we increased the number of features used when we vectorized our text.  By vectorizing, we are putting our data into a format that is usable for our model.  We want to increase the number of features used, but not so much that our model becomes overfit to the training set.

The number of features that we used was three hundred.  Increasing the features increase our model score to 64%.

## Final Model

Finally, we fit our model on the entire training dataset with stopwords and punctuation removed and text lemmatized.  We used 300 features when we vectorized this data and ended up with the following scores:

Training: 66.2%
Test: 64%

We also created a confusion matrix to evaluate how well our model is performing:
![Confusion Matrix]()
Our model is currently not predicting that any tweets are negative.  This is most likely because there were relatively so few negative tweets in our training and test sets.  With so few tweets, our model could not accurately identify them.

## Recommendations



## Next Steps



## For More Information

See the full analysis in the [Jupyter Notebook](https://github.com/elizabeth524/Phase-4-Project/blob/main/SXSW_Data.ipynb) or review my [presentation]().

For additional information, contact Elizabeth Webster at [eaw524@gmail.com](eaw524@gmail.com)