# NLP Assignment 2 - Report

## Overview

This repository contains the implementation of the second assignment for the Natural Language Processing (NLP) course. The assignment covers advanced foundational topics in vector space models, traditional information retrieval architectures, distribution-based word representations (Skip-gram and GloVe), and multi-modal alignment via Vision-Language Models (VLM).

---

## Assignment Structure

The assignment consists of three main questions, each focusing on explicit tasks within representation learning and information retrieval:

---

## Question 1: Text Representation & Information Retrieval (35 points)

### Part A: Term Frequency (TF) Embeddings

**Description**: Lexical document frequencies represent textual items by raw vocabulary dimensions. Punctuation characters are dynamically stripped using standard tokenizers to compile a distinct corpus-wide dictionary. 

**Implementation**: Text was tokenized via NLTK's `word_tokenize` after uniform casing and punctuation removal across all documents in the Cranfield dataset.
- **Vocabulary Summary**: Total identified unique vocabulary terms: `11,861`.

### Part B: TF-IDF Embedding Framework

**Description**: Term Frequency-Inverse Document Frequency scales vector magnitudes by applying a logarithmic frequency constraint balanced against the specificity of words over the entire collection.

**Implementation**: 
- **TF Calculation Formula**: $1 + \log_{10}(\text{term\_count})$ for occurring items, otherwise $0$.
- **IDF Constraints**: Constructed with smooth scaling denominators via $\log_{10}(N / (\text{df} + 1e-6))$.

### Part C: Positive Pointwise Mutual Information (PPMI)

**Description**: Word co-occurrence associations within a continuous context window are captured using Pointwise Mutual Information, thresholding negative relationships to $0$ to preserve explicitly positive structural associations.

### Part D: Information Retrieval Evaluation

**Implementation**: Formulated semantic similarity assessments using Cosine Similarity metrics matching query-to-document vector fields. Custom ranking algorithms evaluated system accuracy against the standard golden validation constraints using structural performance cutoffs.

**Information Retrieval Performance Results**:

| Model Embedding Setup | Mean Precision @ 5 (MP@5) | Mean Average Precision (MAP) |
|-----------------------|---------------------------|------------------------------|
| **Term Frequency (TF)**| 0.2361                    | 0.1845                       |
| **TF-IDF Matrix** | 0.4236                    | 0.3871                       |
| **PPMI Matrix** | 0.3122                    | 0.2648                       |

**Key Analysis Insights**:
- **TF-IDF Dominance**: TF-IDF significantly outperforms basic TF embeddings by dampening stop-words and highlighting highly descriptive domain-specific terms.
- **Sparse Limitations**: Raw TF suffers from term matching limitations, failing to account for corpus-wide statistical distributions.

---

## Question 2: Word Embeddings & Sentiment Analysis (40 points)

### Part A: Skip-gram Representation Learning (Word2Vec)

**Description**: The Skip-gram architecture maps structural center words to surrounding context distributions using sliding neighborhood windows, optimizing internal word weights using negative sampling approximations.

### Part B: Sentiment Classification with Skip-gram Embeddings

**Implementation**: Extracted averaged semantic word vectors across IMDB textual reviews to train explicit statistical learning classifiers.

**Results (Skip-gram Vector Embeddings)**:

| Model Backbone Classifiers | Precision | Recall | F1-Score | Accuracy |
|----------------------------|-----------|--------|----------|----------|
| **Logistic Regression** | 0.77      | 0.76   | 0.76     | 0.76     |
| **Gaussian Naïve Bayes** | 0.63      | 0.68   | 0.65     | 0.64     |

### Part C: Sentiment Classification with GloVe Embeddings

**Implementation**: Loaded pre-trained Global Vectors for Word Representation (`GloVe-100d`), mapping word matrices to optimize identical categorization frameworks.

**Results (GloVe Pre-trained Vectors)**:

| Model Backbone Classifiers | Precision (Class 0 / 1) | Recall (Class 0 / 1) | F1-Score (Macro Avg) | Overall Accuracy |
|----------------------------|-------------------------|----------------------|----------------------|------------------|
| **Logistic Regression** | 0.80 / 0.80             | 0.81 / 0.80          | 0.80                 | **80.00%** |
| **Gaussian Naïve Bayes** | 0.66 / 0.71             | 0.75 / 0.61          | 0.68                 | **68.00%** |

**Comparative Analysis Breakdown**:
- **Classifier Superiority**: Logistic Regression shows clear advantages over Gaussian Naïve Bayes across both embedding styles due to better handling of dense, continuous feature correlations.
- **GloVe vs. Skip-gram**: Pre-trained GloVe vectors outshine dynamically trained local Skip-gram architectures. GloVe models structural co-occurrence probabilities globally across a massive external corpus, providing richer semantic signals for downstream sentiment analysis tasks.

---

## Question 3: Vision-Language Alignment (VLM Latent Space) (25 points)

### Part A-C: Structural Arithmetic Validation

**Description**: Evaluated semantic vector consistency within multi-modal environments using the pre-trained `openai/clip-vit-base-patch32` Vision-Language foundation framework.

**Implementation**: Evaluated classic semantic analogies in shared embedding vector space through targeted algebraic verification tasks.

**Analogy Query Result**:  
$$\vec{v}_{\text{Result}} = \vec{v}_{\text{king}} - \vec{v}_{\text{man}} + \vec{v}_{\text{woman}}$$

**Cosine Similarity Match Matrix**:

| Comparison Word Match | Cosine Similarity Score |
|-----------------------|-------------------------|
| $\text{Similarity}(Result, \text{king})$   | 0.9417                  |
| $\text{Similarity}(Result, \text{queen})$  | **0.9721 (Top Match)** |
| $\text{Similarity}(Result, \text{man})$    | 0.8606                  |
| $\text{Similarity}(Result, \text{woman})$  | 0.9225                  |

*Observed Gender Vector Alignment*: Subtracting the masculine concept vector from "king" and adding the feminine vector automatically shifts the alignment vector directly onto **queen**, demonstrating robust semantic geometric properties in multi-modal vector spaces.

### Part D: Cross-Modal Cross-Matching Selection

- **Task**: Cross-matched text strings to candidate physical image targets stored in Google Drive.
- **Result Output Matrix**:
  - Word Entry `king` $\rightarrow$ Correctly identified **Image 1** (Monarch Image Asset)
  - Word Entry `man` $\rightarrow$ Correctly identified **Image 2** (Male Image Asset)
  - Formula `king - man + woman` $\rightarrow$ Correctly mapped onto **Image 3** (Queen Image Asset)
  - Word Entry `woman` $\rightarrow$ Correctly identified **Image 4** (Female Image Asset)

---

## Technical Stack

| Category | Tools |
|----------|-------|
| Foundation Frameworks | PyTorch, Hugging Face Transformers (`CLIPModel`, `CLIPProcessor`) |
| Machine Learning | Scikit-learn (`LogisticRegression`, `GaussianNB`) |
| NLP Support Tools | NLTK Vectorizations, Collection Counters, Regex Parsing |
| Matrix Computations | NumPy Arrays, Pandas structures |

---

## Key Learnings

1. **TF-IDF Scaling Utility**: Simply monitoring raw occurrences introduces frequency biases. Balancing values using document frequencies provides robust baselines for dense information search pipelines.
2. **Global Co-occurrence Modeling**: GloVe's global log-bilinear matrix factorization captures semantic structural contexts more effectively than simple local context skip-grams.
3. **Multi-Modal Multi-Space Vector Properties**: CLIP's shared embedding engine successfully maps textual semantic properties directly onto corresponding visual assets, demonstrating powerful vector arithmetic properties across distinct modalities.

---

## Project Structure

```text
.
├── assignment-02/
│   ├── NLP_CA2.ipynb       # Main execution notebook for representations and IR
│   └── README.md          # This descriptive report file
└── requirements.txt       # Project constraints and module packages
