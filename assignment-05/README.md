# NLP: Prompt Engineering and Large Language Model Evaluation

Implementation of prompt engineering techniques and Large Language Model (LLM) evaluation for the fifth course assignment of the **Natural Language Processing** course. This project explores different prompting strategies for machine translation, structured information extraction, and text summarization, while comparing their effectiveness using both qualitative and quantitative evaluation metrics.

---

## Overview

This project investigates how different prompting strategies influence the performance of modern Large Language Models. Various prompt engineering techniques are applied to translation, information extraction, and summarization tasks, followed by a systematic evaluation using automatic metrics such as BLEU, BERTScore, and COMET.

The assignment demonstrates that prompt design plays a critical role in improving LLM performance without modifying model parameters.

---

## Features

- Prompt engineering for Large Language Models
- Structured JSON output generation
- Machine translation (Persian ↔ English)
- Comparison of multiple prompting strategies
- Chain-of-Thought reasoning
- Role prompting
- Few-shot prompting
- Guideline prompting
- Translation quality evaluation
- Text summarization
- Automatic evaluation using BLEU, BERTScore, and COMET
- Analysis of inference time and token usage

---

## Project Structure

```text
.
├── NLP_CA5.ipynb      # Main notebook
└── README.md
```

---

## Technologies Used

| Category | Tools |
|----------|------|
| Language | Python 3 |
| LLM API | OpenAI GPT Models |
| NLP | NLTK |
| Evaluation | BLEU, BERTScore, COMET |
| Data Processing | NumPy, Pandas |
| Visualization | Matplotlib |

---

# Question 1 — Prompt Engineering for Information Extraction

Implemented multiple prompting strategies for structured information extraction using a Large Language Model.

## Task

Extract structured information from natural language text and generate outputs in a predefined JSON format.

### Prompting Strategies

Implemented and compared:

- Simple Prompt
- Role Prompting
- Chain-of-Thought (CoT)
- Few-shot Prompting
- Guideline Prompting

Each strategy was evaluated based on

- Output correctness
- Completeness
- Response consistency
- Structured JSON generation

### Observations

- Structured prompts significantly improved output consistency.
- Chain-of-Thought prompts encouraged more reliable reasoning.
- Few-shot prompting improved adherence to the desired output format.
- Guideline prompts reduced formatting errors.

---

# Question 2 — Machine Translation

Evaluated different prompting strategies for bilingual translation.

## Translation Tasks

- Persian → English
- English → Persian

Each translation task was performed using

- Simple Prompt
- Role Prompting
- Chain-of-Thought
- Few-shot Prompting
- Guideline Prompting

---

## Evaluation Metrics

Translation quality was evaluated using three complementary metrics.

### BLEU

Measures n-gram overlap between generated and reference translations.

### BERTScore

Measures semantic similarity using contextual embeddings.

### COMET

Neural evaluation metric that estimates translation quality by considering both the source sentence and reference translation.

---

## Experimental Comparison

For each prompting strategy, the following were analyzed:

- Translation quality
- BLEU score
- BERTScore
- COMET score
- Input token count
- Output token count
- Inference time

### Observations

- Different prompting strategies produced noticeable differences in translation quality.
- Chain-of-Thought often generated more fluent and context-aware translations.
- Few-shot prompting improved consistency across multiple examples.
- BLEU did not always correlate with semantic evaluation metrics such as BERTScore and COMET.

---

# Question 3 — Text Summarization

Applied Large Language Models to abstractive text summarization.

## Task

Generate concise summaries while preserving the main information from the original document.

### Prompt Design

Summaries were generated using carefully designed prompts that emphasized

- Conciseness
- Information preservation
- Readability

### Evaluation

Generated summaries were compared qualitatively with reference summaries.

Performance was analyzed in terms of

- Coverage of key information
- Fluency
- Coherence
- Overall summary quality

---

# Prompt Engineering Techniques

The following prompting techniques were explored throughout the assignment:

- Simple Prompting
- Role Prompting
- Chain-of-Thought Prompting
- Few-shot Prompting
- Guideline Prompting

These strategies demonstrate how prompt design alone can significantly improve the performance of Large Language Models without additional training.

---

# Key Findings

- Prompt engineering substantially influences LLM output quality.
- Structured prompts improve consistency and formatting.
- Role prompting helps models better align with task-specific objectives.
- Chain-of-Thought prompting improves reasoning for complex tasks.
- Few-shot prompting increases robustness by providing examples.
- COMET and BERTScore provide more reliable semantic evaluation than BLEU alone.
- Translation quality should be assessed using multiple complementary metrics rather than relying on a single score.

---

# Implemented Components

The project includes the implementation of

- Prompt templates for multiple prompting strategies
- Structured JSON response generation
- Translation evaluation pipeline
- Automatic computation of BLEU scores
- Automatic computation of BERTScore
- Automatic computation of COMET
- Token usage analysis
- Inference time analysis
- Comparative evaluation of prompting strategies

---

# Future Improvements

- Compare additional prompting strategies such as Self-Consistency and Tree-of-Thought.
- Evaluate larger multilingual datasets.
- Compare different commercial and open-source LLMs.
- Explore Retrieval-Augmented Generation (RAG) for translation and summarization.
- Investigate automatic prompt optimization techniques.

---

# Running the Project

Clone the repository

```bash
git clone https://github.com/your-username/NLP-Assignment-5.git
cd NLP-Assignment-5
```

Install dependencies

```bash
pip install openai nltk bert-score unbabel-comet sacrebleu numpy pandas matplotlib
```

Launch Jupyter Notebook

```bash
jupyter notebook NLP_CA5.ipynb
```

---

# License

This repository is intended for educational purposes as part of a university Natural Language Processing course assignment.
