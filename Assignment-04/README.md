# NLP: Multilingual Named Entity Recognition and Large Language Model Fine-tuning

Implementation of transformer-based Natural Language Processing (NLP) techniques for the fourth course assignment of the **Natural Language Processing** course. This project covers multilingual Named Entity Recognition (NER) using XLM-RoBERTa and instruction tuning of Large Language Models (LLMs) using parameter-efficient fine-tuning techniques.

---

## Overview

This project explores modern transformer-based NLP models for sequence labeling and text generation. The first part implements multilingual Named Entity Recognition using XLM-RoBERTa on combined Persian and English datasets. The second part focuses on instruction tuning of a Large Language Model using LoRA, quantization, and pruning techniques to improve efficiency while maintaining performance.

---

## Features

- Multilingual Named Entity Recognition
- English and Persian dataset integration
- Token-label alignment for subword tokenization
- XLM-RoBERTa Token Classification
- Hugging Face Trainer API
- LoRA parameter-efficient fine-tuning
- 4-bit model quantization
- Instruction tuning
- Large Language Model evaluation
- Weight pruning
- Model optimization and compression

---

## Project Structure

```text
.
├── NLP_CA4.ipynb      # Main notebook
└── README.md
```

---

## Technologies Used

| Category | Tools |
|----------|------|
| Language | Python 3 |
| Deep Learning | PyTorch |
| Transformers | Hugging Face Transformers |
| Datasets | Hugging Face Datasets |
| Parameter-Efficient Fine-tuning | PEFT (LoRA) |
| Quantization | BitsAndBytes |
| Evaluation | SeqEval, Scikit-learn |
| Visualization | Matplotlib |

---

# Question 1 — Multilingual Named Entity Recognition

Implemented a multilingual Named Entity Recognition (NER) system using **XLM-RoBERTa** on combined Persian and English datasets.

## Dataset

The project combines two publicly available Hugging Face datasets:

- Persian NER dataset
- English CoNLL-style NER dataset

### Preprocessing

- Removed unnecessary columns
- Unified label space
- Converted labels to a common format
- Merged both datasets into a multilingual corpus

---

## Tokenization & Label Alignment

Implemented subword tokenization using the XLM-RoBERTa tokenizer.

Since each word may be split into multiple subword tokens, labels were aligned with tokenized outputs using a custom alignment function.

Features include

- Subword tokenization
- Label alignment
- Padding
- Attention masks
- Ignoring padded labels during loss computation

---

## XLM-RoBERTa Token Classification

Implemented a token classification model consisting of

- Pre-trained XLM-RoBERTa encoder
- Dropout layer
- Linear classification head

Training configuration included

- AdamW optimizer
- Cross-Entropy loss
- Hugging Face Trainer
- Validation during training

---

## Evaluation

Model performance was evaluated on the test dataset using

- Precision
- Recall
- F1-score

Predictions were also visualized by comparing predicted and ground-truth entity labels on sample sentences.

### Observations

- XLM-RoBERTa successfully generalizes across multiple languages.
- Proper token-label alignment is essential for subword-based transformer models.
- Multilingual pretraining enables effective cross-lingual sequence labeling.

---

# Question 2 — Instruction Tuning of Large Language Models

Implemented instruction tuning and efficient adaptation of a pre-trained Large Language Model.

---

## Dataset Preparation

Loaded instruction-following datasets from the Hugging Face Hub.

Preprocessing included

- Dataset loading
- Sample selection
- Prompt formatting
- Train-validation split

---

## Parameter-Efficient Fine-tuning (LoRA)

Fine-tuned the language model using Low-Rank Adaptation (LoRA).

### Configuration

- LoRA adapters
- Frozen backbone model
- Trainable low-rank matrices
- Reduced memory consumption

LoRA enables efficient fine-tuning while updating only a small fraction of the model parameters.

---

## 4-bit Quantization

Applied 4-bit quantization using BitsAndBytes.

Configuration included

- 4-bit weight quantization
- NF4 quantization type
- bfloat16 computation

### Benefits

- Lower GPU memory usage
- Faster inference
- Efficient training on limited hardware

---

## Instruction Tuning

Fine-tuned the quantized model on instruction-response pairs.

Generated responses were evaluated qualitatively on unseen prompts to assess instruction-following capability.

---

## Model Pruning

Applied weight pruning to further reduce model complexity.

Pruning removes low-importance weights while attempting to preserve model performance.

### Observations

- Quantization significantly reduces memory requirements.
- LoRA enables efficient fine-tuning with minimal trainable parameters.
- Moderate pruning can compress the model with limited performance degradation.

---

# Implemented From Scratch

The following components were implemented without relying on ready-made pipelines:

- Dataset preprocessing
- Dataset merging
- Label mapping
- Token-label alignment
- Custom token classification model
- Training pipeline
- Evaluation pipeline
- Prompt formatting for instruction tuning
- Model pruning workflow

---

# Key Takeaways

- Multilingual transformer models effectively transfer knowledge across languages.
- Subword tokenization requires careful label alignment for sequence labeling tasks.
- LoRA dramatically reduces the number of trainable parameters while preserving performance.
- Quantization enables deployment of large models on limited hardware.
- Model pruning provides an additional method for reducing computational cost.
- Combining quantization and LoRA allows efficient fine-tuning of modern Large Language Models.

---

# Future Improvements

- Compare XLM-RoBERTa with mBERT for multilingual NER.
- Evaluate larger multilingual datasets.
- Explore QLoRA for more efficient fine-tuning.
- Compare different pruning strategies.
- Evaluate instruction-tuned models using automatic benchmarks such as MT-Bench or AlpacaEval.

---

# Running the Project

Clone the repository

```bash
git clone https://github.com/your-username/NLP-Assignment-4.git
cd NLP-Assignment-4
```

Install dependencies

```bash
pip install torch transformers datasets peft bitsandbytes accelerate seqeval scikit-learn matplotlib
```

Launch Jupyter Notebook

```bash
jupyter notebook NLP_CA4.ipynb
```

---

# License

This repository is intended for educational purposes as part of a university Natural Language Processing course assignment.
