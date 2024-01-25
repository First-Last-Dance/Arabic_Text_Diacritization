# Arabic Diacritization Model

This repository contains a LSTM seq2seq model for Arabic text diacritization. The goal is to add diacritics to Arabic text, aiding in pronunciation and understanding.

## Table of Contents
- [Overview](#overview)
- [Data Preprocessing](#data-preprocessing)
- [Feature Extraction](#feature-extraction)
- [Model Architecture](#model-architecture)
- [Evaluation](#evaluation)

## Overview

The project aims to build and train a diacritization model for Arabic text using deep learning techniques. The model includes components for word and character embeddings, bidirectional LSTMs, and a linear layer for final classification.


## Data Preprocessing

- Read the dataset and remove from it the non arabic letter like ( numbers, brackets, ..) 
- split to sentances on (. , ? , \n, … ) and make all sentences with same size. This size choose according to the dataset. In the dataset average number of words in sentence is 18 so we choose the max words to be 20 and the max number of chars in sentence is the max length sentence to avoid split words
- Take each sentence, tokenize it and separate the diacritization from the words.
- Convert words and diacritics in sentences to numbers (ID)
- finaly we have list of numbers represent words in sentence and another two lists, list of chars in sentence and the corresponding diacritics

## Feature Extraction
- CountVectorizer, TfidfVectorizer: we use sklearn to get this features
- Embedding: that we used in model


## Model Architecture
- Embedding layer for words in sentence
- Embedding layer for chars in sentence
- Bidirectional LSTM for words and take the last hidden state to the next LSTM
- Bidirectional LSTM for chars that take the hidden state of the previous LSTM and the output feed to Linear layer to out the probability of each class


## Evaluation
We use embedding for chars and 3 layer LSTM with drop out 0.1 and get accuracy around 95.5% 
