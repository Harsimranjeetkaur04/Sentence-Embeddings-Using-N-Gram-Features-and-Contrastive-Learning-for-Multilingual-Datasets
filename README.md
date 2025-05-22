# Sentence Embedding Model with N-Gram Word2Vec and Contrastive Learning

This project implements a custom sentence embedding model that generates sentence representations by aggregating embeddings of n-grams derived from Word2Vec. It also includes an unsupervised contrastive learning phase to improve embedding quality and supports evaluation on downstream text classification tasks.

---

## Table of Contents

- [Overview](#overview)  
- [Features](#features)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Code Structure](#code-structure)  
- [Parameters](#parameters)  
- [Evaluation](#evaluation)  
- [Dataset](#dataset) 

---

## Overview

This project leverages Word2Vec embeddings trained on n-grams (unigrams, bigrams, trigrams, up to 5-grams) extracted from sentences to build dense sentence embeddings. It includes:  

- Tokenization and n-gram generation  
- Word2Vec training on a custom dataset  
- Contrastive learning to improve embeddings using margin-based loss  
- Intrinsic evaluation via cosine similarity between sentence pairs  
- Downstream evaluation through a text classification task using Logistic Regression  

It is designed for easy use with text datasets uploaded via Google Colab or local environments.

---

## Features

- Flexible n-gram range for sentence embedding construction  
- Adjustable Word2Vec embedding size and training parameters  
- Unsupervised contrastive learning with customizable epochs and margin  
- Support for intrinsic and extrinsic evaluation metrics  
- Compatible with any plain text dataset for sentence embeddings  

---

## Installation

1. Clone the repository:  
   ```bash
   git clone https://github.com/yourusername/sentence-embedding-ngram-word2vec.git
   cd sentence-embedding-ngram-word2vec

Install required Python packages:

   Download NLTK data (optional if running the script which downloads 
   automatically)

---

## Usage

Run the main script in a Google Colab environment (recommended for easy dataset upload):

1. Upload your dataset file (text file with one sentence per line)
2. The script will:
   - Tokenize the sentences
   - Generate n-grams
   - Train a Word2Vec model
   - Perform unsupervised contrastive learning to fine-tune embeddings
   - Evaluate embeddings on a downstream text classification task (using example labels or your own)

Example to run in a Colab notebook cell:
```bash
!python sentence_embedding_model.py

---

## Code Structure

### SentenceEmbeddingModel class
Core class for:
- Preprocessing
- Word2Vec training
- Embedding generation
- Contrastive learning

### load_dataset_from_upload()
Utility function for:
- Uploading datasets in Colab

### Main script block
Demonstrates complete workflow:
1. Dataset loading
2. Model training
3. Contrastive learning
4. Evaluation

## Parameters

| Parameter       | Description                                | Default Value |
|-----------------|--------------------------------------------|---------------|
| `ngram_range`   | Tuple defining the range of n-grams        | `(1, 5)`      |
| `vector_size`   | Dimensionality of Word2Vec embeddings      | `100`         |
| `alpha`         | Word2Vec training learning rate           | `0.025`       |
| `epochs`        | Number of contrastive learning epochs      | `20`          |
| `margin`        | Margin parameter for contrastive loss      | `0.1`         |

*You can customize these when initializing the model.*

## Evaluation

### Intrinsic Evaluation
- Measures: Cosine similarity between sentence embeddings
- Purpose: Assess semantic similarity

### Extrinsic Evaluation
- Method: Logistic Regression classification
- Purpose: Test practical utility of embeddings

## Dataset Requirements

### Input Format
- Plain text file
- One sentence per line

### For Classification Evaluation
- Labels should be:
  - Provided, or
  - Generated automatically

### Recommendations
- Dataset size considerations:
  - Larger datasets → Better Word2Vec training quality
  - Larger datasets → Improved downstream performance
