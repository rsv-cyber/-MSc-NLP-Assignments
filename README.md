# Natural Language Processing Assignments

> A collection of implementations covering fundamental and modern Natural Language Processing (NLP) techniques, completed as part of my Master's course in Artificial Intelligence Engineering.

---

## Overview

This repository contains five course assignments that progressively explore Natural Language Processing, from classical text processing techniques to modern transformer-based models and Large Language Models (LLMs).

Throughout these assignments, I implemented and evaluated a wide range of NLP methods, including language modeling, information retrieval, sequence labeling, text summarization, multilingual transformers, prompt engineering, and efficient fine-tuning of large language models.

The repository serves as both a record of my coursework and a portfolio showcasing practical NLP implementations using PyTorch and the Hugging Face ecosystem.

---

## Repository Structure

```text
.
├── assignment-01/
│   ├── NLP_CA1.ipynb
│   ├── datasets/
│   │   ├── ner.txt
│   │   ├── ferdowsi.txt
│   │   ├── hafez.txt
│   │   ├── modern_poet.txt
│   │   └── digikala.csv  
│   └── README.md
├── assignment-02/
│   ├── NLP_CA2.ipynb
│   └── README.md
├── assignment-03/
│   ├── NLP_CA3.ipynb
│   └── README.md
├── assignment-04/
│   ├── NLP_CA4.ipynb
│   └── README.md
├── assignment-05/
│   ├── NLP_CA5.ipynb
│   └── README.md
└── README.md
```

Each assignment contains a dedicated README describing the implementation details, datasets, experimental setup, and results.

---

# Assignment Summary

| Assignment | Main Topics | Key Techniques |
|------------|-------------|----------------|
| **Assignment 1** | Text Processing & Language Modeling | Regular Expressions, Tokenization, Levenshtein Distance, Damerau-Levenshtein Distance, WordPiece, BPE, N-gram Language Models, Perplexity |
| **Assignment 2** | Information Retrieval & Word Embeddings | TF, TF-IDF, PMI, PPMI, Skip-gram, GloVe, Sentiment Analysis, CLIP, Information Retrieval Evaluation |
| **Assignment 3** | Deep Learning for NLP | BiRNN, BiLSTM, BiGRU, Named Entity Recognition, Seq2Seq, Attention Mechanism, Text Summarization |
| **Assignment 4** | Transformers & Efficient Fine-tuning | XLM-RoBERTa, Token Classification, LoRA, Quantization, Pruning, Instruction Tuning, Large Language Models |
| **Assignment 5** | Prompt Engineering & LLM Applications | Prompt Engineering, Chain-of-Thought, Few-shot Learning, Role Prompting, Multi-Agent Translation, Translation Evaluation |

---

# Skills Demonstrated

### Classical NLP

- Regular Expressions
- Tokenization
- Edit Distance Algorithms
- Language Modeling
- Information Retrieval
- Word Embeddings
- Text Classification

### Deep Learning for NLP

- Recurrent Neural Networks (RNN, LSTM, GRU)
- Sequence Labeling
- Attention Mechanisms
- Encoder–Decoder Architectures
- Text Summarization

### Transformer-based NLP

- XLM-RoBERTa
- CLIP
- Hugging Face Transformers
- Multilingual NLP
- Instruction Tuning

### Large Language Models

- Prompt Engineering
- Zero-shot Learning
- Few-shot Learning
- Chain-of-Thought Prompting
- Role Prompting
- Multi-Agent Systems
- LoRA Fine-tuning
- Model Quantization
- Model Pruning

---

# Tech Stack

| Category | Technologies |
|----------|--------------|
| Programming Language | Python 3 |
| Deep Learning | PyTorch |
| Transformers | Hugging Face Transformers |
| NLP Libraries | NLTK, SpaCy, Gensim, Hugging Face Datasets |
| Machine Learning | Scikit-learn |
| Word Embeddings | Word2Vec (Skip-gram), GloVe, TF-IDF, PPMI |
| Large Language Models | Llama-3.2, SmolLM2, XLM-RoBERTa, CLIP |
| Data Processing | NumPy, Pandas, ir_datasets |
| Evaluation | ROUGE, BERTScore, BLEU, COMET, SeqEval, MP@5, Classification Metrics |
| Development Environment | Jupyter Notebook, Kaggle, Google Colab |

---

# Highlights

Across these assignments, I implemented and evaluated:

- Classical Information Retrieval systems
- N-gram Language Models
- WordPiece and BPE Tokenizers
- Skip-gram Word2Vec with Negative Sampling
- Sentiment Analysis using learned and pre-trained embeddings
- Named Entity Recognition with recurrent neural networks and transformers
- Attention-based Seq2Seq models for text summarization
- Multilingual NLP using XLM-RoBERTa
- Parameter-efficient fine-tuning using LoRA
- Model compression using Quantization and Pruning
- Prompt Engineering strategies for Large Language Models
- Multi-Agent translation workflows

---

# Future Work

Possible extensions to this repository include:

- Retrieval-Augmented Generation (RAG)
- Vector Databases
- Agentic AI frameworks
- Vision-Language Models
- Retrieval-based Question Answering
- Reinforcement Learning from Human Feedback (RLHF)
- Modern reasoning models

---

# License

This repository is intended for educational purposes as part of the Natural Language Processing course in the Master's program in Artificial Intelligence Engineering.
