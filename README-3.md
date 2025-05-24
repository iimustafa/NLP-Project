# 🇪🇸 Spanish Word2Vec Model Training and Gradio App

This repository contains a Python project that trains and analyzes Word2Vec models (CBOW and Skip-gram) on a Spanish conversational assistant dataset. It includes semantic tasks like word similarity, analogies, odd-one-out detection, and provides a **Gradio web app** for interactive exploration.

**Dataset Source:** [`Bluckr/assistant_spanish_pofi_v1`](https://huggingface.co/datasets/Bluckr/assistant_spanish_pofi_v1) from the Hugging Face Hub.

---

## 📑 Table of Contents

1. [Project Overview](#1-project-overview)  
2. [Getting Started](#2-getting-started)  
   - [Prerequisites](#prerequisites)  
   - [Installation](#installation)  
3. [Core Functionalities](#3-core-functionalities)  
   - [Data Loading & Preprocessing](#data-loading--preprocessing)  
   - [Word2Vec Model Training](#word2vec-model-training)  
   - [Semantic Tasks](#semantic-tasks)  
   - [Gradio Web Application](#gradio-web-application)  
4. [Usage](#4-usage)  
5. [License](#5-license)  

---

## 1. Project Overview

This project demonstrates training two Word2Vec models (CBOW and Skip-gram) on Spanish assistant conversation text. It evaluates these embeddings by performing word similarity, analogy, and odd-one-out detection tasks. A Gradio app allows easy interactive querying of the models.

---

## 2. Getting Started

### Prerequisites

- Python 3.8 or higher  
- Internet connection to download datasets and NLTK tokenizer models  
- Recommended: Virtual environment or Conda environment for dependencies

### Installation

Install required Python packages via pip:

```bash
pip install nltk gensim datasets gradio scikit-learn
```

The project also downloads the NLTK Spanish tokenizer if not already installed.

---

## 3. Core Functionalities

### Data Loading & Preprocessing

- Loads the Spanish dataset from Hugging Face `Bluckr/assistant_spanish_pofi_v1`.
- Tokenizes text into sentences and words, filtering alphabetic tokens.

### Word2Vec Model Training

- Trains two Word2Vec models with Gensim:  
  - CBOW (Continuous Bag of Words)  
  - Skip-gram  
- Parameters: 100-dimensional vectors, window size 5, minimum word frequency 5.

### Semantic Tasks

- Compute cosine similarity between words.  
- Perform word analogies (e.g., "buenas - noches + días = ?").  
- Detect the odd word out in a list.  
- Cluster the top frequent words with KMeans.

### Gradio Web Application

- Interactive interface to input a Spanish word and select model type (CBOW or Skip-gram).  
- Returns top 10 most similar words based on selected model.  
- Handles out-of-vocabulary gracefully.

---

## 4. Usage

Run the main script (e.g., `python main.py`) to:

- Load and preprocess the dataset.  
- Train Word2Vec models (CBOW and Skip-gram).  
- Launch the Gradio web app on a local server.  

The app will be accessible in your browser for interactive exploration.

---

## 5. License

This project is licensed under the MIT License.

---

## Additional Notes

- Training on large datasets may take time depending on your hardware.  
- Models can be saved and loaded later to avoid retraining.  
- You can customize parameters like `vector_size`, `window`, and `min_count` as needed.

---

## Contact

For questions or contributions, feel free to reach out.
