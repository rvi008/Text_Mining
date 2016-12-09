# Report of Text Mining workshop

## First question
<p align="justify">
See the implementation in the notebook.
We choosed to use a dict in order to have the word as a key and the index in the counts matrix as a value.
</p>
The algorithm works as follow :
* Iterate over all the documents
* Normalize and tokenize each word in the document
* Add every new word to the vocabulary and store it's index if it's a new word
* Increment the count for the word in counts at row : document column : word index given by the key word in dict of vocabulary
* /!\ This implementation could be optimized and takes quite a while to generate the counts matrix
* The step of adding a new column in counts was to expensive so we modified the function by first getting the total number of words and initialize the counts matrix


## Second question
<p align="justify">
The negative/positive classification was done this way :
</p>
* Search in each review any form of grading e.g look for x/5, x/4, A-F Grading, stars grading etc..
* "Normalize" all this different gradings system applying "business" rules like in four stars system 2 stars or below is negative and 3 stars and above is positive and so on
* As it's difficult to capture half points grading (because there are many ways to specify it, for example : 1/2, 0.5, half) there are occasional losses but this isn't significant, a "neutral" review might be classified as negative which is reasonable. 

## Third question
### Implementation of the NB class and it's Train / Predict functions
<p align="justify">
We choose to redeclare the count_words function into the NB class.
The TrainMultinomialNB function was implemented this way : 
</p>
* Start with the collection of counts matrix from the training corpus using the count_word function
* Compute the prior probabilities e.g the frequencies of positive / negative documents over the whole corpus
* Compute for each word the conditional probability of belonging to a class
* Return a dict containing for each class the conditional probabilities

The ApplyMultinomialNB was implemented this way :
* Extract all the words from the test set and keep only those already in vocabulary
* Predict the class for each document in the test set according to the prior distribution and the class associated to each term contained in the document 
