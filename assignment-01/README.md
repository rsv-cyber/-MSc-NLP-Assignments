# NLP Assignment 1 - Report

## Overview

This repository contains the implementation of the first assignment for the Natural Language Processing (NLP) course. The assignment covers fundamental NLP concepts including Regular Expressions, Tokenization, Edit Distance, N-gram Language Models, and Perplexity.

---

## Assignment Structure

The assignment consists of four main questions, each focusing on different aspects of NLP fundamentals:

---

## Question 1: Regular Expressions & Text Processing (30 points)

### Part A: Named Entity Recognition (NER) with Regex

**Description**: NER is an information extraction task that identifies and classifies named entities in unstructured text into predefined categories such as person names, organizations, locations, time expressions, quantities, and percentages.

**Implementation**: Extracted URLs, emails, and phone numbers from the provided `ner.txt` file using regex patterns.

### Part B: Rule-based Tokenization

**Description**: Implemented a whitespace-based tokenizer on the dataset.

**Analysis**:

| Rule-based Tokenizers | ML-based Tokenizers |
|-----------------------|---------------------|
| Simple, fast | Adaptable |
| No training data needed | Handle complex patterns |
| Struggle with complex languages and informal text | Require large labeled datasets |
| | Computationally expensive |

### Part C: Edit Distance (Levenshtein & Damerau-Levenshtein)

**Implementation**:

- **Levenshtein Distance**: Calculates minimum operations (insertion, deletion, substitution) to transform one string to another
- **Damerau-Levenshtein Distance**: Extends Levenshtein by including transposition of adjacent characters

**Results**:

| Word Pair | Levenshtein | Damerau-Levenshtein |
|-----------|-------------|---------------------|
| kitten - sitting | 5.0 | 5.0 |
| saturday - sunday | 4.0 | 4.0 |
| book - back | 4.0 | 4.0 |
| algorithm - logarithm | 4.0 | 3.0 |
| "" - test | 4.0 | 4.0 |
| abc - acb | 2.0 | 1.0 |

---

## Question 2: Language Models (35 points)

### Part A: WordPiece Tokenizer Analysis

**Training Process**:

1. Initialize vocabulary with all characters/symbols
2. Calculate probabilities of token combinations
3. Merge most frequent token pairs
4. Stop when target vocabulary size is reached

**Notable Models**: BERT and BERT-based models use WordPiece

**Comparison with BPE**:
- **WordPiece**: Uses probability of co-occurrence for merging decisions
- **BPE**: Uses frequency count for merging decisions

### Part B: WordPiece Tokenizer Implementation

- Trained a WordPiece tokenizer on `Ferdowsi.txt` (Persian poetry)
- Vocabulary size: 30,000 tokens
- Applied tokenization to sample text

### Part C: N-gram Language Models

Implemented an N-gram class with the following components:

- N-gram generation from tokens
- Probability calculation
- Next word prediction
- Text generation

**N-gram Models Comparison**:

| Model | Generated Text Quality | Issues |
|-------|------------------------|--------|
| 2-gram | Repetitive, nonsensical | Limited context, token repetition |
| 4-gram | More coherent, varied | Some unrelated verses |
| 8-gram | Nearly exact original text | Overfitting |

**Key Observations**:

- Increasing n improves performance up to a point
- Higher n-grams (8-gram) tend to overfit training data
- 4-gram provided the best balance between coherence and generalization

### Part D: Perplexity Evaluation

**Definition**: Perplexity measures how well a language model predicts a sequence of words

- **Lower perplexity** indicates better predictive performance

**Results**:

| Dataset | Average Perplexity |
|---------|-------------------|
| Hafez Poems | 13,815.60 |
| Modern Poetry | 744,799.05 |

**Analysis**: The model trained on Ferdowsi's poetry performed significantly better on Hafez's poetry (similar classical style) compared to modern poetry, confirming the model learned domain-specific patterns.

---

## Question 3: N-gram Classification (35 points)

### Part A: N-gram as Classifier

N-grams can be used as classifiers by:

1. Extracting n-grams from training data for each class
2. Calculating frequency of each n-gram per class
3. Scoring new text based on n-gram frequencies
4. Assigning the class with the highest score

### Part B: BPE Tokenizer Implementation

- Trained a BPE tokenizer on Digikala dataset (Persian e-commerce reviews)
- Vocabulary size: 2,000 tokens
- Applied tokenization to dataset for model training

### Part C: Classification with N-grams

Implemented `NGramClassifier` class with evaluation metrics

**Results**:

| Model | Accuracy | Precision | Recall |
|-------|----------|-----------|--------|
| 2-gram | 0.73 | 0.58 | 0.34 |
| 3-gram | 0.75 | 0.73 | 0.42 |

**Analysis**:

- 3-gram model outperforms 2-gram across all metrics
- Higher n-grams capture more contextual information
- 3-gram provides better precision (higher confidence when predicting positive class)

**Advantages of N-gram Classifiers**:

- Fast training and prediction
- Work well with limited data (less overfitting)
- Highly interpretable
- Minimal preprocessing required
- Effective for specific tasks like sentiment analysis

---

## Question 4: Image Tokenization (Bonus)

### Part A: Image Tokenization with KMeans

**Process**:

1. Divide images into patches (9x9 pixels)
2. Flatten each patch into a vector
3. Train KMeans clustering with 256 clusters
4. Assign each patch to a cluster (token)

**Implementation**: Applied to MNIST dataset

**Result**: Each image tokenized into a sequence of cluster indices

### Part B: Classification with N-gram on Images

- Trained a 4-gram classifier on tokenized MNIST images
- **Accuracy**: 74.74%

| Metric | Value |
|--------|-------|
| Accuracy | 74.74% |

**Sample Predictions**:

- Displayed sample images with predicted labels
- Model performed significantly better than random (10%)

---

## Technical Stack

| Category | Tools |
|----------|-------|
| Language | Python 3.9+ |
| NLP Libraries | NLTK, Tokenizers, Regex |
| ML Libraries | Scikit-learn, Keras |
| Data Handling | NumPy, Pandas |
| Visualization | Matplotlib |

---

## Key Learnings

1. **Regex for NER**: Effective for structured entities but limited for complex named entities
2. **Tokenization Strategies**: Trade-off between rule-based simplicity and ML-based adaptability
3. **Edit Distance**: Valuable for spelling correction and string similarity tasks
4. **N-gram Models**: Performance varies with context length; higher n-grams risk overfitting
5. **Perplexity**: Useful metric for evaluating language model performance
6. **Classification**: N-gram classifiers are simple yet effective for text classification with limited data
7. **Image Tokenization**: Clustering-based tokenization can adapt NLP techniques to computer vision tasks

---

## Project Structure
.
├── assignment-01/
│ ├── NLP_CA1.ipynb # Main notebook with all implementations
│ ├── datasets/
│ │ ├── ner.txt # Input text file for Question 1
│ │ ├── ferdowsi.txt # Persian poetry corpus
│ │ ├── hafez.txt # Hafez poetry corpus
│ │ ├── modern_poet.txt # Modern Persian poetry
│ │ └── digikala.csv # E-commerce review dataset
│ └── README.md # This report

---

## Conclusion

This assignment provided comprehensive hands-on experience with fundamental NLP concepts. The progression from basic text processing through language modeling to classification demonstrated the evolution of NLP techniques. Key insights include understanding the trade-offs between different tokenization methods, the impact of n-gram size on model performance, and the application of NLP techniques to non-textual data through tokenization.
