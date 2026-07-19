# NLP Fundamentals: Tokenization, Language Modeling, and Text Classification

Implementation of fundamental Natural Language Processing (NLP) algorithms for the first course assignment of the **Natural Language Processing** course. The project covers regular expressions, tokenization, edit distance algorithms, subword tokenization, N-gram language models, text classification, and image tokenization.

---

## Overview

This project implements several core NLP techniques from scratch alongside widely used tokenization libraries. The assignment explores how traditional NLP methods work before applying them to practical tasks such as language modeling, text generation, sentiment classification, and even image tokenization.

---

## Features

- Regex-based Named Entity extraction
- Rule-based whitespace tokenizer
- Levenshtein Distance implementation
- Damerau-Levenshtein Distance implementation
- WordPiece tokenizer training
- Byte Pair Encoding (BPE) tokenizer training
- Custom N-gram Language Model
- Text generation using N-grams
- Perplexity evaluation
- Custom N-gram text classifier
- Image tokenization using KMeans clustering (Bonus)

---

## Project Structure

```text
.
├── NLP_CA1.ipynb              # Main notebook
├── datasets/
│   ├── ner.txt
│   ├── ferdowsi.txt
│   ├── hafez.txt
│   ├── modern_poet.txt
│   └── digikala.csv
└── README.md
```

---

## Technologies Used

| Category | Tools |
|----------|------|
| Language | Python 3 |
| NLP | NLTK, HuggingFace Tokenizers, Regex |
| Machine Learning | Scikit-learn, Keras |
| Data Processing | NumPy, Pandas |
| Visualization | Matplotlib |

---

# Question 1 — Regular Expressions and Text Processing

## Named Entity Recognition using Regular Expressions

Implemented regular expression patterns to extract:

- URLs
- Email addresses
- Phone numbers

from the provided text corpus.

### Discussion

Advantages of regex-based NER

- Fast
- Lightweight
- No training required
- Easy to customize

Limitations

- Limited generalization
- Difficult to maintain for complex patterns
- Cannot understand context

---

## Rule-based Tokenizer

Implemented a whitespace tokenizer from scratch and evaluated its strengths and weaknesses.

### Rule-based vs Machine Learning Tokenizers

| Rule-based | Machine Learning |
|------------|------------------|
| Fast | More flexible |
| No training data | Learns complex patterns |
| Easy to implement | Requires training |
| Limited language understanding | Better generalization |

---

## Edit Distance

Implemented from scratch

- Levenshtein Distance
- Damerau-Levenshtein Distance

### Results

| Word Pair | Levenshtein | Damerau-Levenshtein |
|-----------|------------:|--------------------:|
| kitten → sitting | 5 | 5 |
| saturday → sunday | 4 | 4 |
| book → back | 4 | 4 |
| algorithm → logarithm | 4 | 3 |
| "" → test | 4 | 4 |
| abc → acb | 2 | 1 |

---

# Question 2 — Language Modeling

## WordPiece Tokenizer

Trained a WordPiece tokenizer on the Persian **Ferdowsi** corpus.

### Vocabulary Size

**30,000 tokens**

### Comparison with BPE

| WordPiece | BPE |
|------------|-----|
| Probability-based merging | Frequency-based merging |
| Used by BERT | Simpler algorithm |
| Better linguistic segmentation | Faster training |

---

## N-gram Language Model

Implemented a custom N-gram language model supporting

- N-gram generation
- Probability estimation
- Next-token prediction
- Text generation

### Generated Text Comparison

| Model | Observation |
|--------|-------------|
| 2-gram | Repetitive, limited context |
| 4-gram | Most coherent generation |
| 8-gram | Closely memorizes training corpus |

### Observation

Increasing the context length generally improves fluency but also increases the risk of overfitting.

---

## Perplexity Evaluation

Evaluated the trained language model on two unseen poetry corpora.

| Dataset | Average Perplexity |
|---------|-------------------:|
| Hafez | 13,815.60 |
| Modern Persian Poetry | 744,799.05 |

### Analysis

The model achieved substantially lower perplexity on Hafez's poetry because both corpora share a similar classical writing style, whereas modern poetry differs significantly in vocabulary and structure.

---

# Question 3 — N-gram Text Classification

## BPE Tokenizer

Trained a Byte Pair Encoding tokenizer on the Digikala review dataset.

**Vocabulary Size:** 2,000 tokens

---

## N-gram Classifier

Implemented a custom classifier using N-gram statistics.

Evaluation metrics

- Accuracy
- Precision
- Recall

### Results

| Model | Accuracy | Precision | Recall |
|--------|----------:|----------:|-------:|
| 2-gram | 0.73 | 0.58 | 0.34 |
| 3-gram | 0.75 | 0.73 | 0.42 |

### Observations

- 3-gram captures more contextual information.
- Higher precision indicates more reliable positive predictions.
- Performance improves with additional context while maintaining good generalization.

---

# Bonus — Image Tokenization

Applied NLP concepts to computer vision.

## Image Tokenization

Pipeline

1. Divide each MNIST image into patches.
2. Flatten each patch.
3. Cluster patches using KMeans.
4. Represent each image as a sequence of visual tokens.

### Parameters

- Patch size: 9 × 9
- Number of clusters: 256

---

## Image Classification

Trained a custom 4-gram classifier on tokenized MNIST images.

### Performance

| Metric | Value |
|--------|-------:|
| Accuracy | **74.74%** |

The classifier significantly outperformed random guessing (10%), demonstrating that N-gram models can capture meaningful sequential patterns in tokenized image representations.

---

# Implemented From Scratch

The following algorithms were implemented without using ready-made implementations:

- Whitespace Tokenizer
- Levenshtein Distance
- Damerau-Levenshtein Distance
- N-gram Language Model
- Text Generation
- Perplexity Calculation
- N-gram Text Classifier

---

# Key Takeaways

- Regular expressions are effective for extracting structured patterns but are limited for general NER.
- Rule-based tokenization is simple and efficient but lacks robustness.
- Edit distance algorithms are fundamental for spelling correction and string similarity.
- WordPiece and BPE provide efficient subword representations.
- Increasing N improves language modeling until data sparsity causes overfitting.
- Perplexity effectively measures language model quality.
- N-gram classifiers remain competitive for small datasets due to their simplicity and interpretability.
- Tokenization concepts can be successfully transferred from text to image data.

---

# Future Improvements

- Add smoothing techniques (Laplace, Kneser-Ney) to the language model.
- Compare N-gram models with neural language models.
- Evaluate additional tokenization methods.
- Extend the classifier with TF-IDF or transformer-based embeddings.

---

# Running the Project

Clone the repository

```bash
git clone https://github.com/rsv-cyber/NLP-Assignment-1.git
cd NLP-Assignment-1
```

Install dependencies

```bash
pip install numpy pandas matplotlib nltk scikit-learn keras tokenizers
```

Launch Jupyter Notebook

```bash
jupyter notebook NLP_CA1.ipynb
```

---

# License

This repository is intended for educational purposes as part of a university Natural Language Processing course assignment.
