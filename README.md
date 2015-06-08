# word2vec

Originally from https://code.google.com/p/word2vec/

## Changes

- Mac OS X compilation
- CMake support
- Outputs the SoftMax classifier

# Outputs

Notations:

- The number of words is denoted *N*.
- The dimension is denoted *D*.

## Words

In text or binary the first line contains the number of words and the dimension separated by a space.

### Binary

- A list of *N* words and their vectors, i.e.:
    - a string terminated by a space
    - a lists of *D* floats

## SoftMax classifier output

As this is a binary tree, the classifier is represented as a list of parents (one for each node).

- The *N* first nodes correpond to the leaves (the words)
- The *N* - 1 next nodes correspond to the inner nodes of the tree (the last node being the root)

### Binary

- The list of parents (64 bits ints) for the 2 * *N* - 2  nodes of the tree (the root of the tree is not listed)
- A list of *N* - 1 vectors (one for each inner node) of dimension *D*

# Tools for computing distributed representation of words

We provide an implementation of the Continuous Bag-of-Words (CBOW) and the Skip-gram model (SG), as well as several demo scripts.

Given a text corpus, the word2vec tool learns a vector for every word in the vocabulary using the Continuous
Bag-of-Words or the Skip-Gram neural network architectures. The user should to specify the following:
 - desired vector dimensionality
 - the size of the context window for either the Skip-Gram or the Continuous Bag-of-Words model
 - training algorithm: hierarchical softmax and / or negative sampling
 - threshold for downsampling the frequent words
 - number of threads to use
 - the format of the output word vector file (text or binary)

Usually, the other hyper-parameters such as the learning rate do not need to be tuned for different training sets.

The script demo-word.sh downloads a small (100MB) text corpus from the web, and trains a small word vector model. After the training
is finished, the user can interactively explore the similarity of the words.

More information about the scripts is provided at https://code.google.com/p/word2vec/
