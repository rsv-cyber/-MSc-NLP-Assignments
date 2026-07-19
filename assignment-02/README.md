# NLP: Information Retrieval, Word Embeddings, and Multimodal Retrieval

Implementation of classical and modern Natural Language Processing (NLP) techniques for the second course assignment of the **Natural Language Processing** course. This project covers information retrieval, dense word embeddings, sentiment analysis, and multimodal representation learning using CLIP.

---

## Overview

This project explores different approaches for representing text and measuring semantic similarity. It begins with sparse document representations for information retrieval, progresses to dense word embeddings for sentiment analysis, and concludes with multimodal representation learning using OpenAI's CLIP model for text-image retrieval.

---

## Features

- Information Retrieval on the Cranfield dataset
- Custom Term Frequency (TF) document representation
- Custom TF-IDF implementation
- Custom PMI and PPMI embeddings
- Information Retrieval evaluation using MP@5
- Skip-gram with Negative Sampling
- Sentiment Analysis using learned embeddings
- Comparison with pre-trained GloVe embeddings
- Multimodal retrieval using CLIP
- Cross-modal semantic similarity analysis

---

## Project Structure

```text
.
├── NLP_CA2.ipynb              # Main notebook
├── datasets/
│   ├── Cranfield Dataset
│   ├── IMDB Reviews
│   ├── GloVe Embeddings
│   └── CLIP Images
└── README.md
```

---

## Technologies Used

| Category | Tools |
|----------|------|
| Language | Python 3 |
| NLP | NLTK, HuggingFace Transformers |
| Deep Learning | PyTorch |
| Machine Learning | Scikit-learn |
| Embeddings | GloVe, CLIP |
| Data Processing | NumPy, Pandas |
| Visualization | Matplotlib |

---

# Question 1 — Information Retrieval

Implemented a classical Information Retrieval system using the Cranfield dataset and compared multiple document representation methods.

## Dataset

- 1,400 scientific documents
- 225 search queries
- Human relevance judgments
- Vocabulary size: **11,861** unique tokens

### Preprocessing

- Lowercasing
- Punctuation removal
- Tokenization using NLTK
- Binary relevance labels (relevance ≥ 2)

---

## Term Frequency (TF)

Implemented sparse document representations using raw term frequencies.

Implementation includes

- Vocabulary construction
- Document vectors
- Query vectors

---

## TF-IDF Representation

Implemented TF-IDF weighting from scratch.

Weighting scheme

- TF = `1 + log10(tf)`
- IDF = `log10(N / df)`
- TF-IDF = TF × IDF

---

## PMI & PPMI Embeddings

Implemented semantic word representations using word co-occurrence statistics.

Configuration

- Sliding window size: 2
- Total token pairs: 316,868

Generated document embeddings by averaging token-level PPMI representations.

---

## Information Retrieval Evaluation

Documents were ranked using cosine similarity and evaluated with Mean Precision at 5 (MP@5).

### Results

| Representation | MP@5 |
|---------------|------:|
| TF | 0.1316 |
| TF-IDF | **0.2409** |
| PPMI | 0.1627 |

### Observations

- TF-IDF achieves the highest retrieval performance.
- PPMI captures semantic relationships better than raw term frequencies.
- Simple TF representations are less effective because every term contributes equally regardless of importance.

---

# Question 2 — Word Embeddings for Sentiment Analysis

Implemented Skip-gram embeddings and compared them with pre-trained GloVe vectors for IMDB sentiment classification.

## Dataset

- IMDB movie reviews
- Top 10,000 vocabulary words
- 10,000 reviews used for Skip-gram training

---

## Skip-gram with Negative Sampling

Implemented a Skip-gram model using PyTorch.

### Configuration

| Parameter | Value |
|-----------|------|
| Embedding Dimension | 100 |
| Context Window | 2 |
| Negative Samples | 4 |
| Batch Size | 256 |
| Epochs | 10 |
| Optimizer | Adam |

Generated sentence embeddings by averaging word embeddings.

---

## Sentiment Classification

Evaluated sentence embeddings using

- Logistic Regression
- Gaussian Naïve Bayes

### Results

| Model | Accuracy | Weighted F1 |
|--------|----------:|------------:|
| Skip-gram + Logistic Regression | **0.79** | **0.79** |
| Skip-gram + Naïve Bayes | 0.64 | 0.64 |

### Observations

- Logistic Regression significantly outperformed Naïve Bayes.
- Averaged embeddings violate the independence assumption of Naïve Bayes.

---

## Pre-trained GloVe Embeddings

Used **glove.6B.100d** vectors to generate document embeddings.

### Results

| Model | Accuracy | Weighted F1 |
|--------|----------:|------------:|
| GloVe + Logistic Regression | **0.80** | **0.80** |
| GloVe + Naïve Bayes | 0.68 | 0.68 |

### Comparison

- GloVe consistently achieved better performance than Skip-gram.
- Large-scale pre-training produces richer semantic representations.
- Logistic Regression remained the strongest classifier.

---

# Question 3 — Multimodal Retrieval with CLIP

Explored multimodal representation learning using OpenAI's CLIP model.

---

## Text Embeddings

Generated normalized embeddings for

- king
- queen
- man
- woman

Performed vector arithmetic

```
king − man + woman
```

### Similarity Results

| Comparison | Cosine Similarity |
|------------|------------------:|
| queen | **0.972** |
| king | ~0.80 |
| woman | ~0.80 |
| man | ~0.70 |

The resulting vector closely matches **queen**, demonstrating that CLIP captures meaningful semantic relationships.

---

## Cross-modal Retrieval

Generated image embeddings and matched them with text embeddings.

### Retrieval Results

| Query | Retrieved Image |
|-------|-----------------|
| king | King |
| queen | Queen |
| man | Man |
| woman | Woman |
| king − man + woman | Queen |

### Observations

- CLIP successfully aligns text and image representations.
- Vector arithmetic in the text embedding space transfers effectively to image retrieval.
- The model demonstrates strong zero-shot reasoning capabilities.

---

# Implemented From Scratch

The following components were implemented without relying on ready-made implementations:

- Term Frequency document representation
- TF-IDF weighting
- PMI computation
- PPMI computation
- Document embedding generation
- Information Retrieval evaluation (MP@5)
- Skip-gram data generation
- Negative Sampling
- Skip-gram neural model
- Sentence embedding generation

---

# Key Takeaways

- TF-IDF provides a strong baseline for Information Retrieval.
- PPMI captures semantic relationships through word co-occurrence.
- Dense embeddings outperform sparse representations for downstream learning tasks.
- Pre-trained GloVe embeddings improve sentiment classification compared to embeddings trained on limited data.
- Logistic Regression consistently outperforms Gaussian Naïve Bayes on embedding-based representations.
- CLIP effectively learns a shared semantic space for text and images, enabling powerful zero-shot multimodal retrieval.

---

# Future Improvements

- Compare with BM25 retrieval.
- Evaluate contextual embeddings such as BERT.
- Train Skip-gram on the full IMDB corpus.
- Fine-tune CLIP for domain-specific retrieval tasks.
- Compare CLIP with newer multimodal foundation models.

---

# Running the Project

Clone the repository

```bash
git clone https://github.com/your-username/NLP-Assignment-2.git
cd NLP-Assignment-2
```

Install dependencies

```bash
pip install numpy pandas matplotlib nltk torch scikit-learn transformers
```

Launch Jupyter Notebook

```bash
jupyter notebook NLP_CA2.ipynb
```

---

# License

This repository is intended for educational purposes as part of a university Natural Language Processing course assignment.
