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

Sentiment analysis as such can be viewed as just another form of classification, in its simplest form a binary classification between "positive" and "negative". Twitter is valuable source of data since it covers a broad range of topics and at different levels of formality. It's also very abundant, with 500 million new tweets being sent out every day (internetlivestats.com, 2020). The sentiments uncovered can for example be used for companies to analyze how people perceive their products or services and overall customer satisfaction. 

Among the first researchers to explore sentiment analysis on Twitter data were Go et al. (2009), who also created the data set used in this project. They introduced the idea of using tweets with emoticons for *distant supervised learning*, i.e. automatic generation of datasets through already existing labels (e.g. emoticons for polarity in this case). Using Naive Bayes, Maximum Entropy and SVM as classifiers and unigrams as well as bigrams for features, they obtained 80 % accuracy when training on this kind of data.

Pak & Paroubek (2010) collected a corpus of 300,000 tweets following the same method as Go et al. (2009). However, they also added a neutral/objective class by collecting tweets from newspaper accounts, and according to them, the method from Go et al. performed badly when used on these three classes. Training a Naive Bayes model on n-grams and POS tags (unlike Go et al. they find the POS tags useful) yielded good experimental results. 
 
Agarwal et al. (2011) show -- by experimenting with tree kernel and feature-based models -- *"[...] that a tree kernel model performs roughly as well as the best feature based models, even though it does not require detailed feature engineering"*. They use about 12,000 manually annotated tweets from a commercial source, some of them translated from other languages into English via Google Translate. For the feature-based approach, one of the 100 features used consists of looking at the prior polarity scaling of words by refering to the Dictionary of Affect in Language (DAL) and WordNet, which turn out to cover almost 90 % of the words in their training set. They achieve an avg. accuracy of up to 75 % for 2-way classification, and 61 % for 3-way classification.

Mohammad et al. (2013) also used sentiment lexicon features along with ngrams to create state-of-the-art SVM classifiers for sentiment detection in tweets. [UUMMM....]

[INSERT PROBLEMS WITH LEXICON-BASED UNSUPERVISED SENTIMENT ANALYSIS]

In 2014, the first paper to use word embeddings for sentiment analysis on Twitter data was published. Tang et al. (2014:1) introduced a special method for creating word embeddings for tweets, arguing that existing word embedding learning algorithms like word2vec aren't suitable for capturing sentiment: *"These methods typically only  model the  context  information of words so that they cannot distinguish words with similar context but opposite sentiment polarity (e.g. good and bad)."* They incorporated sentiments into the embeddings by  mapping  each  n-gram to the sentiment polarity of the sentences in 10 million automcatically collected and annotated tweets. When applying their embeddings to a binary classification task, they achieve around the same accuracy as hand-crafted SOTA models (~ 85 %), which increases to 86.58% when combined with existing feature sets. 

FUN FACTS:<br>
- "Surprisingly though, the word *for* appeared as a top feature. A preliminary analysis revealed that the word *for* appears as frequently in positive tweets as it does in negative tweets. However, tweets containing phrases like *for you* and *for me* tend to be positive even in absence of of any other explicit prior polarity words" (Agarwal et al. 2011:36). <br>
- "Emoticons also appear as important unigrams" (ibid)        

TUTORIALS:<br>
MEDIUM:<br>
Sentiment Analysis from Tweets using Recurrent Neural Networks: https://medium.com/@gabriel.mayers/sentiment-analysis-from-tweets-using-recurrent-neural-networks-ebf6c202b9d5 <br>
OTHER:<br>

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

Wikipedia: "Even though in most statistical classification methods, the neutral class is ignored under the assumption that neutral texts lie near the boundary of the binary classifier, several researchers suggest that, as in every polarity problem, three categories must be identified. Moreover, it can be proven that specific classifiers such as the Max Entropy[9] and SVMs[10] can benefit from the introduction of a neutral class and improve the overall accuracy of the classification."    
 
### 3. Methods

3.1 Train-test-split

3.2 Tokenization
As discussed by Long (2020) in a Towards data science article, the word_tokenize tokenizer from NLTK is simply too slow when dealing with large amounts of data. Instead I settled for a combination of split() and regular expressions for removing the punctuation. 

3.3 Word embeddings

3.4 Padding
Current word limit on Twitter: 280 characters

3.5 Basline
Naive Bayes?

3.6 Model
LSTM?

### 4. Results

### 5. Discussion

5.1 Limitations
- emoticons are **not perfect** at defining the correct sentiment of a tweet
- the data used for training and testing is collected by search queries and therefore **biased** (Agarwal et al. 2011)
- 

### 6. Conclusion

### 7. References
## Papers:<br>
- Agarwal, A., Xie, B., Vovsha, I., Rambow, O. and Passonneau, R., 2019. Sentiment analysis of twitter data, 2014. URL http://www. cs. columbia. edu/~ julia/papers/Agarwaletal11. pdf.
- Go, A., Bhayani, R. and Huang, L., 2009. Twitter sentiment classification using distant supervision. CS224N project report, Stanford, 1(12), p.2009.
- Pak, A. and Paroubek, P., 2010, May. Twitter as a corpus for sentiment analysis and opinion mining. In LREc (Vol. 10, No. 2010, pp. 1320-1326).
- Tang, D. & Wei, F. & Yang, N. & Zhou, M. & Liu, T. & Qin, B., 2014. Learning Sentiment-Specific Word Embedding for Twitter Sentiment Classification. 52nd Annual Meeting of the Association for Computational Linguistics, ACL 2014 - Proceedings of the Conference. 1. 1555-1565. 10.3115/v1/P14-1146

## Other sources:<br>
Long, A., 2019. Benchmarking Python NLP Tokenizers. Towards data science. URL: https://towardsdatascience.com/benchmarking-python-nlp-tokenizers-3ac4735100c5 (Accessed 24-10-2020)<br>
Internet live stats, 2020. Twitter Usage Statistics. *internetlivestats.com*. URL: https://www.brandwatch.com/blog/twitter-stats-and-statistics/ (Accessed 28-10-2020)<br>