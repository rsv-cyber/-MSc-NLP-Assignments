# NLP: Sequence Labeling and Abstractive Text Summarization

Implementation of deep learning approaches for two fundamental Natural Language Processing (NLP) tasks as part of the third course assignment of the **Natural Language Processing** course. This project covers sequence labeling for Named Entity Recognition (NER) using recurrent neural networks and abstractive text summarization using an Attention-based Encoder-Decoder architecture.

---

## Overview

This project explores the transition from traditional NLP techniques to deep learning models. The first part focuses on sequence labeling using Bidirectional RNN, LSTM, and GRU architectures for Named Entity Recognition. The second part implements an Attention-based Seq2Seq model with pre-trained GloVe embeddings for abstractive text summarization and evaluates the generated summaries using the ROUGE metric.

---

## Features

- Custom vocabulary construction
- Dynamic batching with custom collate function
- Named Entity Recognition (NER)
- Bidirectional RNN implementation
- Bidirectional LSTM implementation
- Bidirectional GRU implementation
- Sequence masking for padded tokens
- Attention mechanism implementation
- Encoder-Decoder summarization model
- Pre-trained GloVe embeddings
- ROUGE evaluation
- Training and validation visualization

---

## Project Structure

```text
.
├── NLP_CA3.ipynb              # Main notebook
├── datasets/
│   ├── CoNLL-2003
│   ├── XSum
│   └── GloVe Embeddings
└── README.md
```

---

## Technologies Used

| Category | Tools |
|----------|------|
| Language | Python 3 |
| Deep Learning | PyTorch |
| NLP | Hugging Face Datasets, NLTK |
| Pre-trained Embeddings | GloVe |
| Evaluation | Scikit-learn, ROUGE |
| Data Processing | NumPy, Pandas |
| Visualization | Matplotlib |

---

# Question 1 — Named Entity Recognition

Implemented a sequence labeling system for Named Entity Recognition (NER) using recurrent neural networks on the CoNLL-2003 dataset.

## Dataset

- CoNLL-2003 NER dataset
- Pre-tokenized sentences
- Named Entity labels
- Part-of-Speech tags
- Chunk tags

---

## Vocabulary Construction

Implemented a custom vocabulary class supporting

- Vocabulary creation
- Token-to-ID conversion
- ID-to-token conversion
- Vocabulary size retrieval

### Configuration

- Minimum token frequency (cutoff): **5**
- Special tokens:
  - `<pad>`
  - `<unk>`
  - `<s>`
  - `</s>`

---

## Dataset & DataLoader

Implemented custom Dataset and DataLoader classes.

Features

- Dynamic padding
- Custom `collate_fn`
- Variable-length sentence handling
- Efficient mini-batch generation

Padding is applied only within each batch to reduce unnecessary computation and memory usage.

---

## Bidirectional RNN

Implemented a Bidirectional RNN encoder consisting of

- Embedding layer
- Bidirectional RNN
- Linear classification layer

Training configuration

| Parameter | Value |
|-----------|------|
| Embedding Size | 64 |
| Hidden Size | 64 |
| Batch Size | 32 |
| Epochs | 10 |
| Learning Rate | 1e-3 |

During training, padded tokens were masked to ensure they did not contribute to the loss or evaluation metrics.

---

## Bidirectional LSTM

Replaced the recurrent layer with a Bidirectional LSTM while keeping the remaining architecture unchanged.

Generated

- Training loss curves
- Validation loss curves
- Accuracy curves
- Classification report

---

## Bidirectional GRU

Implemented a Bidirectional GRU model using the same experimental setup.

Compared its performance with the RNN and LSTM models.

---

## Model Comparison

Compared the three recurrent architectures using

- Training loss
- Validation loss
- Validation accuracy
- Per-class precision
- Per-class recall
- Per-class F1-score

### Observations

- Bidirectional models significantly improve sequence understanding by incorporating both past and future context.
- LSTM and GRU generally outperform vanilla RNNs due to their ability to capture longer dependencies.
- GRU provides competitive performance while requiring fewer parameters than LSTM.

---

# Question 2 — Abstractive Text Summarization

Implemented an Attention-based Encoder-Decoder architecture for abstractive text summarization using the XSum dataset.

## Dataset

- XSum news summarization dataset
- 30% of the training split
- 10% of the validation split

### Preprocessing

- Lowercasing
- Punctuation removal
- Whitespace tokenization
- Custom vocabulary generation

Vocabulary configuration

- Minimum token frequency (cutoff): **10**

---

## Pre-trained GloVe Embeddings

Initialized the embedding layer using pre-trained GloVe vectors.

Configuration

| Parameter | Value |
|-----------|------|
| Embedding Dimension | 100 |

Special tokens were initialized with zero vectors.

---

## Dataset & DataLoader

Implemented custom Dataset and DataLoader classes supporting

- Variable-length documents
- Variable-length summaries
- Dynamic padding
- Batch processing

---

## Attention Mechanism

Implemented an additive attention mechanism for the decoder.

The attention layer enables the decoder to focus on different parts of the input sequence during summary generation.

---

## Encoder-Decoder Architecture

Implemented an Attention-based Seq2Seq model consisting of

- Pre-trained GloVe embedding layer
- Bidirectional GRU encoder
- Attention mechanism
- GRU decoder
- Linear output layer

### Training Configuration

| Parameter | Value |
|-----------|------|
| Embedding Size | 100 |
| Hidden Size | 100 |
| Batch Size | 32 |
| Epochs | 10 |
| Learning Rate | 1e-3 |

---

## Evaluation

Evaluated the summarization model using

- Training Loss
- Validation Loss
- ROUGE Score

Generated

- Loss curves
- ROUGE curves
- Sample generated summaries after each training epoch

---

## ROUGE Metric

ROUGE measures the overlap between generated summaries and reference summaries.

The evaluation considers

- Word overlap
- Recall-oriented matching
- Quality of generated summaries

ROUGE is one of the standard evaluation metrics for text generation and summarization tasks.

---

# Implemented From Scratch

The following components were implemented without relying on ready-made implementations:

- Vocabulary class
- Dataset class
- Dynamic padding with custom `collate_fn`
- Bidirectional RNN model
- Bidirectional LSTM model
- Bidirectional GRU model
- Attention mechanism
- Encoder-Decoder architecture
- Training and validation loops
- Sequence masking for padded tokens

---

# Key Takeaways

- Bidirectional recurrent networks improve sequence labeling by utilizing both past and future context.
- LSTM and GRU effectively mitigate the vanishing gradient problem encountered by vanilla RNNs.
- Dynamic padding significantly improves training efficiency for variable-length sequences.
- Attention enables the decoder to focus on the most relevant encoder states during text generation.
- Pre-trained GloVe embeddings accelerate convergence and improve semantic representations.
- ROUGE provides an effective automatic evaluation metric for abstractive summarization.

---

# Future Improvements

- Replace recurrent models with Transformer-based architectures such as BERT for NER.
- Fine-tune pretrained encoder-decoder models such as T5 or BART for summarization.
- Experiment with beam search decoding.
- Compare different attention mechanisms.
- Evaluate using additional summarization metrics such as BERTScore.

---

# Running the Project

Clone the repository

```bash
git clone https://github.com/your-username/NLP-Assignment-3.git
cd NLP-Assignment-3
```

Install dependencies

```bash
pip install numpy pandas matplotlib nltk torch datasets rouge-score scikit-learn
```

Launch Jupyter Notebook

```bash
jupyter notebook NLP_CA3.ipynb
```

---

# License

This repository is intended for educational purposes as part of a university Natural Language Processing course assignment.
