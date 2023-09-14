---
layout: post
title:  "Bag of n-gram and collocation"
date:   2023-04-09 21:48:43 +0530
categories: ml, ai, notes
---
### Bag of N-Grams

We’ve broken down the sentence into single words or “tokens” as of now. The meaning of n-grams is that you take n consecutive words in a sentence and create a set of those.

A sentence “get me some strong coffee” can be tokenised simply as “get”, “me”, “some”, “coffee”. With n-grams where n=2 the tokens would be: “get me”, “me some”, “some coffee”.

It’s quite intuitive to understand what it is. It's important to understand what it does though - n-grams capture more of the meaning or information from the sentence. These are generally used for language modelling, sentiment analysis, etc., where you need more context than just the word.

Here’s what each n-gram is referred to as:  
n=1 : unigram  
n=2: bigram  
n=3: trigram  
n=4: four-gram  
n=5: five gram

Theoretically, for [latex]k[/latex] words you would have [latex]k^n[/latex] possible n-grams. But since it's not likely that each word would follow every other word, we have fewer n-grams in practice.

However, n-grams are computationally expensive and need more storage the more significant the n is - but it also means more information is retained.

#### Code

# N-Grams demo[¶](#N-Grams-demo)

Here we use the nltk library to create n-grams. Its important to know how to install nltk though since we are using miniconda.

From your terminal run:

> conda activate
> 
> conda install -c anaconda nltk

Once this is done, you will need to install nltk data. Open up the python terminal from within your conda environment.

> python -m nltk.downloader all

In [ ]:

```
from nltk.util import ngrams
from nltk.tokenize import word_tokenize, sent_tokenize
```

nltk has a built-in function called split() that can be used but word_tokenizer handles things like punctuations.

In [ ]:

```
s = "Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications. It provides a way to run applications in a consistent, reliable environment, without the need to worry about the underlying infrastructure."
tokenized_words = word_tokenize(s)
print(tokenized_words)
```

```
['Kubernetes', 'is', 'an', 'open-source', 'platform', 'for', 'automating', 'the', 'deployment', ',', 'scaling', ',', 'and', 'management', 'of', 'containerized', 'applications', '.', 'It', 'provides', 'a', 'way', 'to', 'run', 'applications', 'in', 'a', 'consistent', ',', 'reliable', 'environment', ',', 'without', 'the', 'need', 'to', 'worry', 'about', 'the', 'underlying', 'infrastructure', '.']
```

sent_tokenize function will tokenize based on sentences instead of words. Very handy.

In [ ]:

```
tokenized_sentences = sent_tokenize(s)
print(tokenized_sentences)
```

```
['Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications.', 'It provides a way to run applications in a consistent, reliable environment, without the need to worry about the underlying infrastructure.']
```

Finally, we can use the ngrams function to get the n-grams we need. Here we get bigrams.

In [ ]:

```
list(ngrams(tokenized_words, 2))
```

Out[ ]:

```
[('Kubernetes', 'is'),
 ('is', 'an'),
 ('an', 'open-source'),
 ('open-source', 'platform'),
 ('platform', 'for'),
 ('for', 'automating'),
 ('automating', 'the'),
 ('the', 'deployment'),
 ('deployment', ','),
 (',', 'scaling'),
 ('scaling', ','),
 (',', 'and'),
 ('and', 'management'),
 ('management', 'of'),
 ('of', 'containerized'),
 ('containerized', 'applications'),
 ('applications', '.'),
 ('.', 'It'),
 ('It', 'provides'),
 ('provides', 'a'),
 ('a', 'way'),
 ('way', 'to'),
 ('to', 'run'),
 ('run', 'applications'),
 ('applications', 'in'),
 ('in', 'a'),
 ('a', 'consistent'),
 ('consistent', ','),
 (',', 'reliable'),
 ('reliable', 'environment'),
 ('environment', ','),
 (',', 'without'),
 ('without', 'the'),
 ('the', 'need'),
 ('need', 'to'),
 ('to', 'worry'),
 ('worry', 'about'),
 ('about', 'the'),
 ('the', 'underlying'),
 ('underlying', 'infrastructure'),
 ('infrastructure', '.')]
```

Then we get trigrams.

In [ ]:

```
list(ngrams(tokenized_words, 3))
```

Out[ ]:

```
[('Kubernetes', 'is', 'an'),
 ('is', 'an', 'open-source'),
 ('an', 'open-source', 'platform'),
 ('open-source', 'platform', 'for'),
 ('platform', 'for', 'automating'),
 ('for', 'automating', 'the'),
 ('automating', 'the', 'deployment'),
 ('the', 'deployment', ','),
 ('deployment', ',', 'scaling'),
 (',', 'scaling', ','),
 ('scaling', ',', 'and'),
 (',', 'and', 'management'),
 ('and', 'management', 'of'),
 ('management', 'of', 'containerized'),
 ('of', 'containerized', 'applications'),
 ('containerized', 'applications', '.'),
 ('applications', '.', 'It'),
 ('.', 'It', 'provides'),
 ('It', 'provides', 'a'),
 ('provides', 'a', 'way'),
 ('a', 'way', 'to'),
 ('way', 'to', 'run'),
 ('to', 'run', 'applications'),
 ('run', 'applications', 'in'),
 ('applications', 'in', 'a'),
 ('in', 'a', 'consistent'),
 ('a', 'consistent', ','),
 ('consistent', ',', 'reliable'),
 (',', 'reliable', 'environment'),
 ('reliable', 'environment', ','),
 ('environment', ',', 'without'),
 (',', 'without', 'the'),
 ('without', 'the', 'need'),
 ('the', 'need', 'to'),
 ('need', 'to', 'worry'),
 ('to', 'worry', 'about'),
 ('worry', 'about', 'the'),
 ('about', 'the', 'underlying'),
 ('the', 'underlying', 'infrastructure'),
 ('underlying', 'infrastructure', '.')]
```

### Collocation - extracting more meaning out of our sentences

Let’s look at the idea of Collocation.

Consider the phrase “deep sleep”. It is made of two words “deep” and “sleep”. The meaning of the phrase however is different from the literal meaning of its constituent parts.

So how do we know that our sentence hints towards “good sleep” instead of “sleeping on the ocean bed”?

### Techniques to extract collocations from text data

We could use bag-of-n-grams, to begin with, but that gives a ton of useless sequences like “is the”, “but then”, etc. We could obviously filter these common words - we will come to this later.

Another way is to have a master list with all the collocations in a given context. Then we could use the master list to look up if the collocations in our text have any significant meaning.  
This would however be computationally expensive and also we need a list of collocations that are high-quality and relevant.  
Having said that this can be a useful technique in some contexts where the domain is narrow.

#### statistical collocation extraction methods

##### Frequency based methods

In this method you look at the most frequently occuring n-grams. As you would think, this method would give us a ton of phrases like “of the”, “is the”, etc. because these are naturally used more.

##### Hypothesis testing for collocation extraction

Hypothesis testing deserves a post of its own but here is what I gathered so far.

In hypothesis testing we make a null-hypothesis and an alternative-hypothesis for our current data population. Then we figure out statistically whether the hypothesis is true.  
In case of collocation extraction, for a phrase, we make a null hypothesis that these words together are not a significant case. The alternative hypotheiss is naturally that the words being together have a significant meaning.  
Then we use statistics to find if the null hypothesis is correct or not.

Will deep dive into the math of this with some examples in another post.

##### Point-wise mutual information criterion

In this method we calculate the likelihood to two words being together. In this method we take into account the fact that the likelihood could be influenced by the frequency of occurence of the individual words. This method also deserves a post of its own.