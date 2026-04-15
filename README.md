# NLP Topic Modeling Demo

## Overview

This project demonstrates how **topic modeling** works in Natural Language Processing (NLP). Topic modeling algorithms like **Latent Dirichlet Allocation (LDA)** analyze a text corpus. Topic modeling is an unsupervised ML technique, meaning it does not require labeled training data. Rather, the algorithm discovers topics based on statistical patterns of word co-occurrences.

### Key Concepts

- **Document**: A piece of text (article, email, post, etc.)
- **Corpus**: A collection of documents
- **Topic**: A distribution over words that frequently co-occur
- **LDA (Latent Dirichlet Allocation)**: A popular topic modeling algorithm; Each topic is a mixture of words and each document is a mixture of topics

## Dataset

This demo uses the **20 Newsgroups dataset**, a publicly available corpus of ~20,000 newsgroup documents across 20 different categories. For simplicity, this demo uses 3 categories:

- `rec.sport.baseball` - Baseball discussions
- `talk.politics.guns` - Gun politics debates
- `sci.space` - Space exploration and astronomy

## Method

### Step 1: Load Data

- Import libraries and load the sklearn 20 Newsgroups dataset.
- Remove headers, footers, and quotes.

### Step 2: Text Preprocessing

Transform raw text into a numerical representation:

- **Tokenization**: Split text into individual words
- **Lowercasing**: Convert all text to lowercase
- **Stop word removal**: Remove common words like "the"
- **Filtering**: Remove very rare and very common terms
- **Vectorization**: Create a document-term matrix

**Note:** Use CountVectorizer because LDA expects word counts (not TF-IDF weights).

### Step 3: Build and Train the LDA Model

- Initialize an LDA model specifying the number of topics to discover (3, for this demo).
- The model learns which words belong to which topics and which topics appear in which documents.
- Each document is represented as a probability distribution over topics.

### Step 4: Examine Discovered Topics

- The model discovers topics within the corpus, but it does not name those topics. Topics can be quite abstract.
- By checking the top words for each topic, we can figure out a coherent name for each topic.
- For example, if the topic's top words are like "game, hit, team, baseball..." then we might call the topic "baseball."
- In this demo, you can see that LDA discovers the 3 topics (baseball, guns, space) even though it never saw those category labels. Neat!

### Step 5: Visualize Topic Distributions

- Use a heatmap to visualize how topics are distributed across documents.
- Some documents are mostly a single topic (less ambiguous) and others are a mixture of topics (more ambiguous).