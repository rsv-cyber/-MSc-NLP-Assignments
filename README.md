# NLP Assignments

> Natural Language Processing — Master's Course Assignments

---

## Overview

This repository contains my submitted assignments from the NLP course during my Master's program. It serves as:
- A record of my coursework and learning journey
- A reference for NLP techniques and implementations
- A portfolio piece demonstrating practical NLP skills

**Topics covered:**
- Regular Expressions and Text Preprocessing
- N-gram Language Models and Perplexity
- Word Embeddings (TF-IDF, PPMI, Word2Vec, GloVe)
- Text Classification and Sentiment Analysis
- Named Entity Recognition (NER)
- Sequence Labeling with RNNs/LSTMs
- Text Summarization (Seq2Seq with Attention, Transformers)
- Prompt Engineering (Zero-shot, Few-shot, Chain of Thought)
- Multi-Agent Systems for Translation
- Large Language Models (LLMs) and Fine-tuning
- Model Compression (Pruning, Quantization)
- Information Retrieval and Evaluation Metrics

---

## Repository Structure

.
├── assignment-01/
│ ├── NLP_CA1.ipynb # Main notebook with all implementations
│ ├── datasets/
│ │ ├── ner.txt # Input text file for Question 1
│ │ ├── ferdowsi.txt # Persian poetry corpus (Ferdowsi)
│ │ ├── hafez.txt # Hafez poetry corpus
│ │ ├── modern_poet.txt # Modern Persian poetry
│ │ └── digikala.csv # E-commerce review dataset
│ └── README.md # Assignment report
├── assignment-02/ # Placeholder for future assignments
├── assignment-03/ # Placeholder for future assignments
├── assignment-04/ # Placeholder for future assignments
├── assignment-05/ # Placeholder for future assignments
└── requirements.txt # Project dependencies







---

## Assignments Overview

| # | Assignment | Topics | Key Techniques | Status |
|---|------------|--------|----------------|--------|
| 1 | Text Processing & Language Models | Regex for NER, Tokenization, Edit Distance, N-gram LMs, Perplexity, WordPiece Tokenizer | Regex, Levenshtein/Damerau-Levenshtein, N-gram (2,4,8-gram), Perplexity, BPE/WordPiece | ✅ Submitted |
| 2 | Word Representations & Information Retrieval | TF, TF-IDF, PPMI, Skip-gram, GloVe, Sentiment Analysis, Bias Analysis | TF-IDF, PPMI, Cosine Similarity, Precision@k (MP@5), Skip-gram, Logistic Regression, Naïve Bayes, CLIP | ✅ Submitted |
| 3 | Deep Learning for NLP | Sequence Labeling (NER), Seq2Seq Summarization with Attention | LSTM, BiLSTM, BiGRU, Encoder-Decoder, Attention Mechanism, ROUGE, GloVe Embeddings | ✅ Submitted |
| 4 | Transformers & Model Optimization | NER with XLM-RoBERTa, Summarization with LLMs (LLAMA, SmolLM), Pruning, Fine-tuning | XLM-RoBERTa, TokenClassification, HuggingFace Transformers, Zero/Few-shot, 4-bit Quantization, Unstructured Pruning, SFTTrainer, ROUGE, BERTScore | ✅ Submitted |
| 5 | Prompt Engineering & Multi-Agent Systems | Translation, Prompting Strategies, Agent-based Systems | Simple Prompt, Role Play, Chain of Thought (CoT), Few-shot, Guidelines, Context-aware Prompting, Critique Agent, Multi-Agent System | ✅ Submitted |

---

## Tech Stack

| Category | Tools |
|----------|-------|
| Deep Learning | PyTorch, Hugging Face Transformers, PyTorch Pruning |
| NLP Libraries | NLTK, SpaCy, Gensim, HuggingFace Datasets |
| ML Frameworks | Scikit-learn, Logistic Regression, Naïve Bayes |
| Word Embeddings | Word2Vec (Skip-gram), GloVe, PPMI, TF-IDF |
| LLMs | Llama-3.2-1B, SmolLM2-360M, XLM-RoBERTa, CLIP |
| Data Handling | NumPy, Pandas, ir_datasets |
| Evaluation | ROUGE, BERTScore, Classification Report, MP@k |
| Environment | Python 3.9+, Jupyter Notebook, Kaggle/Colab |

