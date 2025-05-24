# Spanish Word2Vec Model Analysis and Gradio App

This repository contains a Python project demonstrating the training and analysis of Word2Vec models (CBOW and Skip-gram architectures) on a Spanish assistant dataset. It includes functionalities for finding similar words, performing analogies, identifying "odd one out" words, and a Gradio web application for interactive exploration.

The dataset used is `Bluckr/assistant_spanish_pofi_v1` from the Hugging Face Hub.

---

## Table of Contents

1.  [Project Overview](#project-overview)
2.  [Getting Started](#getting-started)
    * [Prerequisites](#prerequisites)
    * [Installation](#installation)
    * [Running the Code (Google Colab)](#running-the-code-google-colab)
3.  [Core Functionalities](#core-functionalities)
    * [Dataset Loading & Preprocessing](#dataset-loading--preprocessing)
    * [Word2Vec Model Training (CBOW & Skip-gram)](#word2vec-model-training-cbow--skip-gram)
    * [Word Similarity Search](#word-similarity-search)
    * [Word Analogy Test](#word-analogy-test)
    * [Odd One Out](#odd-one-out)
    * [Model Performance Comparison](#model-performance-comparison)
4.  [Gradio Web Application](#gradio-web-application)
5.  [License](#license)

---

## 1. Project Overview

This project showcases the application of Word2Vec, a popular technique for learning word embeddings, to a specialized Spanish dataset. By training both CBOW and Skip-gram models, we can explore how different architectures capture semantic relationships. The included Gradio app provides an intuitive interface for users to input Spanish words and discover their most similar counterparts according to the trained models.

---

## 2. Getting Started

### Prerequisites

* Python 3.8+
* Google Colab (recommended for easy setup) or a local environment with sufficient resources.

### Installation

If you're using a Google Colab notebook, you can install the necessary libraries directly in your notebook cells:

```bash
!pip install datasets nltk gensim gradio matplotlib
