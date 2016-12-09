# Report of Text Mining workshop

## First question
<p text-align="justify">
See the implementation in the notebook.
We choosed to use a dict in order to have the word as a key and the index in the counts matrix as a value.
The algorithm works as follow :
* Iterate over all the documents
* Normalize and tokenize each word in the document
* Add every new word to the vocabulary and store it's index if it's a new word
* Increment the count for the word in counts at row : document column : word index given by the key word in dict of vocabulary
</p>
