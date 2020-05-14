# Sentiment-Analysis-Movie-review
The Movie Review Data is a collection of movie reviews retrieved from the imdb.com website in the early 2000s by Bo Pang and Lillian Lee. The reviews were collected and made available as part of their research on natural language processing. The reviews were originally released in 2002, but an updated and cleaned up version was released in 2004, referred to as v2.0. The dataset is comprised of 1,000 positive and 1,000 negative movie reviews drawn from an archive of the rec.arts.movies.reviews newsgroup hosted at IMDB. The authors refer to this dataset as the polarity dataset.
Our data contains 1000 positive and 1000 negative reviews all written before 2002, with a cap of 20 reviews per author (312 authors total) per category. We refer to this corpus as the polarity dataset.
The data has been cleaned up somewhat, for example:
- The dataset is comprised of only English reviews.
- All text has been converted to lowercase.
- There is white space around punctuation like periods, commas, and brackets.
- Text has been split into one sentence per line.
After unzipping the ﬁle, you will have a directory called txt sentoken with two subdirectories containing the text neg and pos for negative and positive reviews. Reviews are stored one per ﬁle with a naming convention from cv000 to cv999 for each of neg and pos. Next, let’s look at loading the text data.
## Loading Text Data
We have two directories each with 1,000 documents each. We can process each directory in turn by ﬁrst getting a list of ﬁles in the directory using the listdir() function, then loading each ﬁle in turn. For example, we can load each document in the negative directory using the load doc() function to do the actual loading.
## Clean Text Data
Just looking at the raw tokens can give us a lot of ideas of things to try, such as:
- Remove punctuation from words (e.g. ‘what’s’).
- Removing tokens that are just punctuation (e.g. ‘-’).
- Removing tokens that contain numbers (e.g. ‘10/10’).
- Remove tokens that have one character (e.g. ‘a’).
- Remove tokens that don’t have much meaning (e.g. ‘and’).

Some ideas:
- We can ﬁlter out punctuation from tokens using regular expressions.
- We can remove tokens that are just punctuation or contain numbers by using an isalpha() check on each token.
- We can remove English stop words using the list loaded using NLTK.
- We can ﬁlter out short tokens by checking their length.

## Develop Vocabulary
When working with predictive models of text, like a bag-of-words model, there is a pressure to reduce the size of the vocabulary. The larger the vocabulary, the more sparse the representation of each word or document. A part of preparing text for sentiment analysis involves deﬁning and tailoring the vocabulary of words supported by the model. We can do this by loading all of the documents in the dataset and building a set of words. We may decide to support all of these words, or perhaps discard some. The ﬁnal chosen vocabulary can then be saved to ﬁle for later use, such as ﬁltering words in new documents in the future. 
We can keep track of the vocabulary in a Counter, which is a dictionary of words and their count with some additional convenience functions. We need to develop a new function to process a document and add it to the vocabulary. The function needs to load a document by calling the previously developed load doc() function. It needs to clean the loaded document using the previously developed clean doc() function, then it needs to add all the tokens to the Counter, and update counts. We can do this last step by calling the update() function on the counter object. Below is a function called add doc to vocab() that takes as arguments a document ﬁlename and a Counter vocabulary.

