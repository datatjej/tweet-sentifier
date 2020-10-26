# tweet-sentifier
Final project for Machine Learning (LT2316). Autumn semester of 2020. 

- [1. Background](#1-background)
- [2. Data resource](#2-data-resource)
- [3. Methods](#3-methods)
- [4. Results](#4-results)
- [5. Discussion](#5-discussion)
- [6. Conclusion](#6-conclusion)
- [7. References](#7-references)

### 1. Background
My motivation for doing a sentiment analysis-based project was to familiarize myself with an area of NLP that we haven't really had so much hands-on experience of in the program so far. I also thought it would be interesting and useful to see how one would best go about to extract tweets from Twitter and save them in a data-processing-friendly way. 

Sentiment analysis as such can be viewed as just another form of classification, in it's simplest form a binary classification between "positive" and "negative". Twitter is valuable source of data since it covers a broad range of topics and at different levels of formality. The sentiments uncovered can for example be used for companies to analyze how people perceive their products or services and overall customer satisfaction. 

Wikipedia: "Even though in most statistical classification methods, the neutral class is ignored under the assumption that neutral texts lie near the boundary of the binary classifier, several researchers suggest that, as in every polarity problem, three categories must be identified. Moreover, it can be proven that specific classifiers such as the Max Entropy[9] and SVMs[10] can benefit from the introduction of a neutral class and improve the overall accuracy of the classification."      

### 2. Data resource
My resource for this project has been the [Sentiment140 dataset](https://www.kaggle.com/kazanova/sentiment140). It's a corpus of 1.6 million tweets which have been automatically annotated (0 = negative or 4 = positive) through a method described by Go et al. (2019), by which they have specifically searched tweets with emoticons in them and labeled them accordingly. The emoticons themselves have been removed from the version of the corpus used here. 

The CSV data has the following format:<br>
The data is a CSV with emoticons removed. Data file format has 6 fields:<br>
0 - the polarity of the tweet (0 = negative, 4 = positive)<br>
1 - the id of the tweet (2087)<br>
2 - the date of the tweet (Sat May 16 23:58:44 UTC 2009)<br>
3 - the query (lyx). If there is no query, then this value is NO_QUERY.<br>
4 - the user that tweeted (robotickilldozr)<br>
5 - the text of the tweet (Lyx is cool)<br>

### 3. Methods

Basline: Naive Bayes?

### 4. Results

### 5. Discussion

### 6. Conclusion

### 7. References
Go, A., Bhayani, R. and Huang, L., 2009. Twitter sentiment classification using distant supervision. CS224N project report, Stanford, 1(12), p.2009.<br>