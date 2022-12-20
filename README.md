# Text-Mining-Final-Project--Gender-Classification
Final Project for my text mining class. All students were given the exact same dataset and were asked to answer either the research question, What preprocessing methods are most important for improving gender bias detection? Or their own question, the question I decided to answer was Which classification method most accurately defines text as female or male. The dataset used for this study comes from the study Collecting a Large-Scale Gender Bias Dataset for Coreference Resolution and Machine Translation (S. Levy, K. Lazar, G. Stanvosky, Collecting a Large-Scale Gender Bias
Dataset for Coreference Resolution and Machine Translation, 2021)

## Methodology
● 60-40 Train Test split
● Preprocessing
● Convert datasets to numeric values
● Import Google News corpus
● Check dataset against Google News corpus
● Apply classification models on new data
● Select model with highest f1 score

### 60-40 Train Test split
Everyone in our class decided to split the data their own way. I decided to go with a 60-40 train test split. There wasn't any real reason for me choosing a 60-40 split other than the fact that most of the class was going with more aggressive splits like 80-20 or even 90-10, I was curious to see how an even split would affect things.

### Preprocessing
After the dataset has been split To preprocess the text we write a function that uses regex to remove whitespace, punctuation, or anything with digits from the input. We then tokenized the input into sentences, then tokenized that into word tokens. Next, we loop through the word tokens and remove stopwords, convert them to lowercase and then remove tokens smaller than 3 characters. After that we call our preprocessing function twice, passing in Xtrain first and Xtest second. This leaves us with a list of lists with each list inside the list containing the word tokens. We then loop through the list of lists and within each list we join the words together with whitespace. Finally, we turn our preprocessed Xtrain and Xtest into data frames.

### Convert datasets to numeric values
To represent Xtrain and Xtest Numerically we create a count vectorizer. We then use that vectorizer to fit() or data frames. From fit() we are able to calculate the features. Then we use a temp variable to get the vocabulary from fit(). Once we have the vocabulary, we fit transform() our Xtrain and transform() our Xtest. Next using the vocabulary we create a list with each element of the list being a key from the vocabulary. Finally, we create new data frames containing our fit transform() for Xtrain, and transform() for Xtest, while each column for the data frames contains a key from their vocabularies.

### Import Google News corpus
After Xtrain and Xtest have been represented numerically we now import the Google News, a model by google that contains 300-dimensional vectors for 3 million words and phrases.

### Check dataset against Google News corpus
After the dataset has been converted into its numeric representation, we then import the Google News corpus. Once it has been successfully imported we can now check to see which words in our original dataset are represented in the Google News Corpus. To do so we write a function that takes in an input, creates an empty data frame, loops through the input, and for each element in our input, loop through our vocabulary and see if the current word is represented in the Google news Corpus. If it is, we can add it to our sentence. After looping through an input, we append a data frame containing our sentence into the empty data frame we created at the beginning of the function.

### Apply classification models on new data
After the dataset has been checked against the Google News corpus we now apply our classification methods. 5 have been selected, they are Naive Bayes, K-Nearest Neighbors (5 Neighbors), Logistic Regression, Multilayer Perceptron (MLP), and Decision Tree.

### Select Model With Highest f1 Score
K-Nearest Neighbors gives us the highest accuracy score, tied with Naive Bayes. Unlike our Naive Bayes classifier, the f1 scores for female and male are close in value. Therefore this model will be selected as our final classifier.


