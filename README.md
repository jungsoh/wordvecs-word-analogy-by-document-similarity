# Word vectors: Word analogy by document similarity
We will use word embeddings (word vectors) to represent words and use document similarity measures to solve word analogy problems. An example of a word analogy problem is to fill in the blank:
> *Man* is to *Woman* as *King* is to ______`.

Because word embeddings (i.e. word vectors) are very computationally expensive to train, most machine learning practitioners will load a pre-trained set of embeddings. We will load a collection of pre-trained embeddings and measure similarity between word embeddings, and use the similarity measures to solve word analogy problems.

## Pre-trained word vectors
We will use 50-dimensional [GloVe](https://nlp.stanford.edu/projects/glove) vectors to represent words.

## Document similarity
To measure the similarity between two words, we need a way to measure the degree of similarity between two embedding vectors for the two words. Given two vectors *u* and *v*, the cosine similarity between *u* and *v* is the cosine of the angle between the two vectors. Some examples of measuring the similarity are shown below:

![cosine similarity](images/cosine_sim.png)

## Solving word analogy problem
A word analogy problem asks you to complete this sentence: 
> *a* is to *b* as *c* is to **____**.
    
An example is: 
> *man* is to *woman* as *king* is to *queen*.

To solve this problem, we try to find a word *d*, such that the associated word vectors are related as follows:
>  (embedding of *b* - embedding of *a*) is very similar to (embedding of *d* - embedding of *c*)

We measure the cosine similarity between (embedding of *b* - embedding of *a*) and (embedding of *d* - embedding of *c*), and seardh for the word *d* that minimizes the similarity. 

## Some results
The algorithm finds correct analogy pairs most of time, but sometimes finds wrong analogy pairs: 
```
italy -> italian :: spain -> spanish
india -> delhi :: japan -> tokyo
man -> woman :: boy -> girl
small -> smaller :: large -> smaller
```
