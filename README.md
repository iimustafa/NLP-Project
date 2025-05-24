# 🇪🇸 Spanish Word2Vec Model Analysis and Gradio App

This repository contains a Python project that demonstrates the training and analysis of Word2Vec models (CBOW and Skip-gram) on a Spanish assistant dataset. It supports word similarity, analogies, "odd one out" detection, and includes a **Gradio web application** for interactive exploration.

**Dataset Source:** [`Bluckr/assistant_spanish_pofi_v1`](https://huggingface.co/datasets/Bluckr/assistant_spanish_pofi_v1) from the Hugging Face Hub.

---

## 📑 Table of Contents

1. [Project Overview](#1-project-overview)  
2. [Getting Started](#2-getting-started)  
   - [Prerequisites](#prerequisites)  
   - [Installation](#installation)  
3. [Core Functionalities](#3-core-functionalities)  
   - [Dataset Loading & Preprocessing](#dataset-loading--preprocessing)  
   - [Word2Vec Training (CBOW & Skip-gram)](#word2vec-training-cbow--skip-gram)  
   - [Word Similarity Search](#word-similarity-search)  
   - [Word Analogy Test](#word-analogy-test)  
   - [Odd One Out](#odd-one-out)  
4. [Results and Analysis](#4-results-and-analysis)  
5. [Gradio Web App](#5-gradio-web-app)  
6. [License](#6-license)  

---

## 1. Project Overview

This project applies **Word2Vec** embeddings (CBOW & Skip-gram) to a Spanish conversational assistant dataset. It reveals how these models understand Spanish language semantics — from greetings and questions to abstract expressions.

Both models were trained on the same preprocessed dataset and evaluated using similarity and analogy tests. The included **Gradio app** allows anyone to interact with the models without writing code.

---

## 2. Getting Started

### Prerequisites

- Python 3.8+
- Google Colab (recommended)
- Alternatively, a local machine with sufficient memory and compute

### Installation (Colab Recommended)

```bash
!pip install datasets nltk gensim gradio matplotlib

## 3. Core Functionalities

Dataset Loading & Preprocessing
from nltk.tokenize import sent_tokenize, word_tokenize
from datasets import load_dataset
import nltk

def load_corpus_from_hf_dataset(dataset_name="Bluckr/assistant_spanish_pofi_v1", text_column="text"):
    sentences = []
    ds = load_dataset(dataset_name)

    for split in ds.keys():
        print(f"Processing split: {split}")
        for example in ds[split]:
            text = example[text_column]
            if isinstance(text, str):
                text = text.lower()
            else:
                continue
            for sent in sent_tokenize(text, language='spanish'):
                tokens = [w for w in word_tokenize(sent, language='spanish') if w.isalpha()]
                if tokens:
                    sentences.append(tokens)
    return sentences

# Run this to get the corpus
corpus = load_corpus_from_hf_dataset()
