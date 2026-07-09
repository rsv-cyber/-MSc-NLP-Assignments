# NLP Assignment 2: Information Retrieval, Word Embeddings, and Multimodal Retrieval

This repository contains the implementation and evaluation of three key Natural Language Processing tasks: building an Information Retrieval system, training and applying word embeddings for sentiment analysis, and performing multimodal retrieval using CLIP.

## Table of Contents
- [Question 1: Information Retrieval on the Cranfield Dataset](#question-1-information-retrieval-on-the-cranfield-dataset)
  - [Dataset Preparation](#dataset-preparation)
  - [Part I: Document and Query Embedding (Term Frequency)](#part-i-document-and-query-embedding-term-frequency)
  - [Part II: TF-IDF Embedding](#part-ii-tf-idf-embedding)
  - [Part III: PMI and PPMI Embedding](#part-iii-pmi-and-ppmi-embedding)
  - [Part IV: Evaluation using MP@K](#part-iv-evaluation-using-mpk)
- [Question 2: Word Embeddings for Sentiment Analysis](#question-2-word-embeddings-for-sentiment-analysis)
  - [Dataset Preparation](#dataset-preparation-1)
  - [Part I: Training Skip-gram Embeddings](#part-i-training-skip-gram-embeddings)
  - [Part II: Extracting and Applying Skip-gram Embeddings](#part-ii-extracting-and-applying-skip-gram-embeddings)
  - [Part III: Applying Pre-trained GloVe Embeddings](#part-iii-applying-pre-trained-glove-embeddings)
- [Question 3: Multimodal Retrieval with CLIP](#question-3-multimodal-retrieval-with-clip)
  - [Part I: Textual Representation and Analogies](#part-i-textual-representation-and-analogies)
  - [Part II: Cross-Modal Retrieval](#part-ii-cross-modal-retrieval)
- [Conclusion](#conclusion)

---

## Question 1: Information Retrieval on the Cranfield Dataset

Implementation of a classic information retrieval system using the Cranfield dataset with three different document and query representation methods.

### Dataset Preparation

**Loading the Dataset:**
- `cran.all.1400`: 1400 scientific documents
- `cran.qry`: 225 queries
- `cranqrel`: Relevance judgments (score 0-3)

**Data Preprocessing:**
- **Relevance Binarization**: Documents with relevance score >= 2 are considered relevant
- **Text Preprocessing**: Punctuation removal and lowercasing
- **Tokenization**: Using NLTK's `word_tokenize`
- **Vocabulary**: 11,861 unique tokens

### Part I: Document and Query Embedding (Term Frequency)

Basic vector representations using term frequency:

- Created frequency dictionaries for documents and queries
- Converted to dense vectors of length 11,861
- Each element represents the term frequency for a corresponding token

### Part II: TF-IDF Embedding

Enhanced term frequency vectors with TF-IDF weighting:

**Implementation:**
- **Term Frequency (tf)**: `1 + log10(frequency)` if term appears, else 0
- **Document Frequency (df)**: Number of documents containing the term
- **Inverse Document Frequency (idf)**: `log10(N / (df + 1e-6))`
- **TF-IDF Weight**: `tf * idf`

### Part III: PMI and PPMI Embedding

Pointwise Mutual Information embeddings based on word co-occurrence:

**Implementation:**
- Sliding window of size 2 for context
- Calculated single and pair frequencies
- **PMI**: `log2((pair_count/total_freq) / (product_of_individual_freqs))`
- **PPMI**: `max(PMI, 0)`
- Total token pairs: 316,868

**Conversion to Embeddings:**
- For each document, computed mean PPMI score for each vocabulary token
- Tokens not appearing in document get value 0

### Part IV: Evaluation using MP@K

Performance evaluation using Mean Precision at K (K=5):

**Results:**
| Method | MP@K |
|--------|------|
| TF | 0.1316 |
| TF-IDF | 0.2409 |
| PPMI | 0.1627 |

**Analysis:**
- **TF-IDF** performs best, balancing term frequency with term rarity
- **PPMI** outperforms TF by capturing semantic relationships
- **TF** performs worst due to equal weighting of all terms

---

## Question 2: Word Embeddings for Sentiment Analysis

Sentiment classification of IMDB movie reviews comparing learned vs. pre-trained embeddings.

### Dataset Preparation

- IMDB dataset from Keras (top 10,000 words)
- First 10,000 training samples selected for efficiency
- Data preprocessed as sequences of word indices

### Part I: Training Skip-gram Embeddings

**Negative Sampling Setup:**
- Unigram probability with smoothing (α=0.75)
- Generated 4 negative samples per positive pair

**Training Data Generation:**
- Window size of 2 for context
- Generated pairs: (target_word, context_word, label)
- Labels: 1 for positive pairs, 0 for negative pairs

**Model Architecture:**
- PyTorch `nn.Module` with two embedding layers
- Target and context embeddings (dimension: 100)
- Sigmoid activation for probability prediction

**Training:**
- Batch size: 256
- Epochs: 10
- Optimizer: Adam
- Loss: Binary Cross-Entropy

### Part II: Extracting and Applying Skip-gram Embeddings

**Document Embedding:**
- Averaged word embeddings for each review
- Final dimension: 100

**Classification Results:**

**Logistic Regression:**
- Accuracy: 0.79
- Weighted F1-Score: 0.79

**Naïve Bayes:**
- Accuracy: 0.64
- Weighted F1-Score: 0.64

**Analysis:**
- Logistic Regression significantly outperforms Naïve Bayes
- Naïve Bayes' independence assumptions unsuitable for averaged vectors

### Part III: Applying Pre-trained GloVe Embeddings

**GloVe Details:**
- `glove.6B.100d.txt`: 100-dimensional vectors
- Trained on Wikipedia and Gigaword corpus

**Document Embedding:**
- Averaged GloVe embeddings for each decoded review
- Unknown words ignored

**Classification Results:**

**Logistic Regression:**
- Accuracy: 0.80
- Weighted F1-Score: 0.80

**Naïve Bayes:**
- Accuracy: 0.68
- Weighted F1-Score: 0.68

**Analysis:**
- GloVe outperforms Skip-gram due to global co-occurrence statistics
- Logistic Regression consistently outperforms Naïve Bayes

---

## Question 3: Multimodal Retrieval with CLIP

Zero-shot learning and multimodal retrieval using OpenAI's CLIP model.

### Part I: Textual Representation and Analogies

**Implementation:**
- CLIP model: `openai/clip-vit-base-patch32`
- Normalized text embeddings via `get_text_features`

**Word Analogy Test:**
- Computed: `king - man + woman`
- Compared with embeddings of "king", "queen", "man", "woman"

**Results:**
| Vector | Similarity |
|--------|------------|
| king - man + woman vs. queen | 0.972 |
| king - man + woman vs. king | ~0.8 |
| king - man + woman vs. man | ~0.7 |
| king - man + woman vs. woman | ~0.8 |

**Conclusion:** CLIP captures analogical relationships effectively.

### Part II: Cross-Modal Retrieval

**Implementation:**
- Image embeddings via `get_image_features`
- Cosine similarity between text and image embeddings
- Retrieved image with highest similarity

**Results:**
| Query | Retrieved Image |
|-------|-----------------|
| "king" | Image of king |
| "queen" | Image of queen |
| "man" | Image of man |
| "woman" | Image of woman |
| "king - man + woman" | Image of queen |

**Key Finding:** CLIP generalizes textual analogies to the visual domain, demonstrating powerful cross-modal understanding.

---

## Conclusion

This assignment demonstrates the effectiveness of various NLP and multimodal techniques:

1. **Information Retrieval**: TF-IDF weighting provides superior retrieval performance compared to simple term-frequency and PMI-based methods.

2. **Sentiment Analysis**: Pre-trained embeddings (GloVe) outperform embeddings trained from scratch on limited data, highlighting the value of large-scale pre-training.

3. **Multimodal Retrieval**: CLIP shows impressive zero-shot capabilities, capturing complex semantic relationships across text and images, and enabling effective cross-modal retrieval.

These findings underscore the importance of appropriate feature representation and the power of pre-trained models in modern NLP and multimodal applications.
