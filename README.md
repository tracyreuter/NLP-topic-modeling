# NLP Topic Modeling Demo

A brief demo of topic modeling using Latent Dirichlet Allocation (LDA) on the 20 Newsgroups dataset.

## Overview

This project showcases how **topic modeling** works in Natural Language Processing. Topic modeling is an unsupervised machine learning technique that automatically discovers abstract "topics" within a collection of documents.

## What is Topic Modeling?

Topic modeling algorithms analyze a corpus of text documents to identify patterns of word co-occurrence and group them into interpretable themes or "topics." Unlike supervised learning, topic modeling doesn't require labeled training data. Rather, it discovers topics purely from the statistical patterns in the text.

### Key Concepts:

- **Document**: A piece of text (article, email, post, etc.)
- **Corpus**: A collection of documents
- **Topic**: A distribution over words that frequently co-occur
- **LDA (Latent Dirichlet Allocation)**: A popular topic modeling algorithm

## Dataset

This demo uses the **20 Newsgroups dataset**, a publicly available corpus that contains approximately 20,000 newsgroup documents partitioned across 20 different categories. This demo uses 5 categories:

- `rec.sport.baseball` - Baseball discussions
- `sci.med` - Medical science topics
- `comp.graphics` - Computer graphics
- `talk.politics.guns` - Gun politics debates
- `sci.space` - Space exploration and astronomy

## Walkthrough

### Step 1: Load and Explore Data

The notebook begins by importing necessary libraries and loading the 20 Newsgroups dataset. We remove headers, footers, and quotes to focus on the core content of each document.

### Step 2: Text Preprocessing

Before modeling, we transform raw text into a numerical representation:

1. **Tokenization**: Split text into individual words
2. **Lowercasing**: Convert all text to lowercase
3. **Stop word removal**: Remove common words like "the," "and," "is"
4. **Filtering**: Remove very rare and very common terms
5. **Vectorization**: Create a document-term matrix

**Why CountVectorizer?** LDA expects word counts (not TF-IDF weights), as it models the generative process of how documents are created.

### Step 3: Build and Train the LDA Model

We initialize an LDA model specifying the number of topics we want to discover. The model learns:
- Which words belong to which topics
- Which topics appear in which documents

**Output shape:** `(n_documents, n_topics)` - each document represented as a probability distribution over topics.

### Step 4: Examine Discovered Topics

Each topic is characterized by its top words. By examining these words, we can interpret what each topic represents.

**Example output:**
```
Topic 1: game team baseball season players year games hit runs ball
Topic 2: space nasa launch orbit shuttle mission earth moon satellite data
Topic 3: gun guns people crime weapons law firearms government control police
```

The model discovers coherent, interpretable topics even though it never saw the category labels!

### Step 5: Visualize Topic Distributions

We create visualizations to understand:
- How topics are distributed across documents (heatmap)
- Which topic is most dominant across the corpus (bar chart)
- How individual documents map to multiple topics

**Insights:**
- Some documents are dominated by a single topic (high certainty)
- Other documents are mixtures of multiple topics (more ambiguous)

### Step 6: Analyze Sample Documents

We examine specific documents and their topic distributions to verify that the model is making sensible assignments. This helps validate that discovered topics align with document content.

### Step 7: Visualize Word Importance

Bar charts show the relative importance of top words within each topic, helping understand topic coherence and quality.
