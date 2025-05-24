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
4. [Comparasion](#4-Comparasion)  

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

- Compute cosine similarity between `asistencia` and `pregunta` words.  
- Perform word analogies (e.g., "buenas - noches + días = ?").  
- Detect the odd word out in a list [`hola`, `gracias`, `ayuda`, `pregunta`, `mesa`,`amigo`,`hi`]  
- Cluster the top frequent words with KMeans.
- Cluster 0: [`tus`, `realizar`, `calculadora`, `cálculos`]
- Cluster 1: [`para`, `y`, `los`, `con`,`hacer`,`son`,`significado`,`persona`,`personas`,`ser`]


### Gradio Web Application

- Interactive interface to input a Spanish word and select model type (CBOW or Skip-gram).  
- Returns top 10 most similar words based on selected model.  
- Handles out-of-vocabulary gracefully.

---

## 4. Comparasion

# Word Similarity Comparison: CBOW vs Skip-gram

| Rank | CBOW ("hola")    | Score  | Skip-gram ("hola") | Score  | CBOW ("gracias")  | Score  | Skip-gram ("gracias") | Score  |
|-------|-----------------|--------|--------------------|--------|-------------------|--------|-----------------------|--------|
| 1     | puedes          | 0.9731 | alguna             | 0.8368 | carolina          | 0.9175 | regalo                | 0.9329 |
| 2     | pofi            | 0.9434 | estás              | 0.8352 | enviando          | 0.9107 | incondicional         | 0.9144 |
| 3     | guardar         | 0.9167 | buenas             | 0.8224 | esto              | 0.9062 | envíale               | 0.9005 |
| 4     | ayudar          | 0.8994 | tal                | 0.8072 | regalo            | 0.9050 | felicidades           | 0.8963 |
| 5     | esta            | 0.8863 | dice               | 0.8071 | mensaje           | 0.9041 | ahí                   | 0.8955 |
| 6     | dónde           | 0.8777 | decir              | 0.8055 | siempre           | 0.9019 | nuevo                 | 0.8925 |
| 7     | cómo            | 0.8751 | reproduce          | 0.8031 | dile              | 0.9006 | amistad               | 0.8886 |
| 8     | obtener         | 0.8736 | ayudar             | 0.8001 | agradecido        | 0.8965 | encantó               | 0.8879 |
| 9     | encontrar       | 0.8698 | ha                 | 0.7994 | felicidades       | 0.8939 | carolina              | 0.8828 |
| 10    | funcionamiento  | 0.8600 | tardes             | 0.7993 | mándale           | 0.8924 | daniel                | 0.8822 |

---

## CBOW's Functional Insight

- For **"hola"** (hello), CBOW directly connects to words like **"puedes"** (you can) and **"pofi"** (the assistant's name), indicating an understanding of common commands and direct interaction.
- For **"gracias"** (thank you), CBOW links to **"carolina"** (a likely named entity) and action-oriented terms like **"enviando"** (sending) and **"mensaje"** (message), suggesting a strong grasp of transactional gratitude.
- **Strength:** Excellent at discerning direct, local context and operational language.

## Skip-gram's Broader Semantic View

- For **"hola"**, Skip-gram generates more general conversational words like **"estás"** (you are) and **"tal"** (how), reflecting general pleasantries.
- For **"gracias"**, it associates with words like **"amistad"** (friendship) and **"incondicional"** (unconditional), pointing to wider emotional or social nuances.
- **Strength:** Better at learning abstract semantic similarities and capturing broader conceptual relationships.



---

## Additional Notes

- Training on large datasets may take time depending on your hardware.  
- Models can be saved and loaded later to avoid retraining.  
- You can customize parameters like `vector_size`, `window`, and `min_count` as needed.
