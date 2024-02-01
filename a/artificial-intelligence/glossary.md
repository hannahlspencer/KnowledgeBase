# Glossary

#### Chunking

The identifying and extracting of short phrases or chunks of words from sentences based on their syntactic structure.

For example, in the sentence "The cat sat on the mat," a chunking algorithm might identify the chunks as follows:

* Noun Phrase (NP): "The cat"
* Verb Phrase (VP): "sat"
* Prepositional Phrase (PP): "on the mat"

#### Corpus

A large and structured collection of text documents or other forms of data that are used for training, testing, or evaluating NLP and machine learning models

#### Embedding

An embedding is data represented by a large array of numbers called a vector that helps compare patterns of relationships.

The numbers link together as a multidimensional map for relationships. For example, dog and puppy are similar words so would be represented by vectors that are close together:

* Dog: \[0.1, 0.51, 0.6, 0.2, 0.8]
* Puppy: \[0.3, 0.5, 0.9, 0.8, 0.4]

Vectors have hundreds of points. A database full of embeddings is called a vector database which can be used to search, cluster, and classify.&#x20;

#### Ground Truth

The actual or real-world data that is used to evaluate the performance of a machine learning model. Ground truth is considered the correct information about the target variable or outcome that the model is trying to predict. For example in image classification**:**

* Ground truth: Labels or categories assigned to each image in the dataset by human annotators.
* Example: If the model is trained to classify images of animals, the ground truth would indicate the correct animal category for each image.

#### Model Context Window

This is the range of input elements or tokens that a model considers when making predictions. For example, in a language model, the context window determines how many previous and/or future words or tokens the model takes into account when predicting the next word in a sequence. The choice of the context window size can impact the model's ability to understand long-range dependencies in the data.

#### MRC - Machine Reading Comprehension

Machine Reading Comprehension involves training models to understand the context of a passage or document and to be able to extract relevant information to answer questions accurately.

#### Negative Sample

An instance that represents the absence of a particular characteristic. In binary classification problems, negative samples are typically instances that do not exhibit the behavior or characteristic of interest. For example, in spam detection:

* Positive sample: An email that is classified as spam.
* Negative sample: An email that is not spam.

#### &#x20;QA Pair

A QA pair, short for Question-Answer pair, is a pair of related elements in which a question is accompanied by its corresponding answer.

For example, in a QA dataset:

* **Question:** "What is the capital of France?"&#x20;
* **Answer:** "The capital of France is Paris."

#### RAG

RAG stands for Retrieval Augmented Generation. It is an AI design pattern that combines an LLM and external knowledge retrieval. More information in a Microsoft context: [https://learn.microsoft.com/en-us/azure/databricks/generative-ai/retrieval-augmented-generation](https://learn.microsoft.com/en-us/azure/databricks/generative-ai/retrieval-augmented-generation#What%20is%20Retrieval%20Augmented%20Generation?)

#### Stop word list

A stop word list is a collection of common words that are often filtered out or excluded from text data during the preprocessing phase in NLP and information retrieval tasks because they are not meaningful on their own eg. articles (e.g., "a," "an," "the"), prepositions (e.g., "in," "on," "under"), conjunctions (e.g., "and," "but," "or"), and other frequently occurring words that don't carry significant semantic meaning on their own.

#### Topic Modelling

Topic modeling is a frequently used approach to discover hidden semantic patterns portrayed by a text corpus and automatically identify topics that exist inside it.

Namely, it’s a type of statistical modeling that leverages unsupervised machine learning to analyze and identify clusters or groups of similar words within a body of text.
