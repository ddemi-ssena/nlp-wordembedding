# Twitter Sentiment Analysis: TF-IDF vs. Word Embeddings

## Project Overview

This project explores and compares two distinct approaches for performing sentiment analysis on a large dataset of Twitter messages: using **TF-IDF (Term Frequency-Inverse Document Frequency)** and **Word Embeddings (specifically Word2Vec)**. The primary objective is to classify tweets as either positive or negative and evaluate the effectiveness of each text representation method.

## Problem Definition

The core task is **Sentiment Analysis**, a fundamental Natural Language Processing (NLP) problem. We aim to build models that can automatically determine the emotional tone of a tweet, classifying it into one of two categories: **positive** or **negative**. This binary classification is relevant for applications such as social media monitoring, customer feedback analysis, and trend detection.

## Dataset

The project utilizes the **Sentiment140 dataset**, which consists of 1.6 million tweets collected via the Twitter API. Each tweet is labeled with a sentiment:
* `0`: Negative
* `4`: Positive
* `2`: Neutral (These tweets were removed for this binary classification task).

The dataset can be accessed from [Kaggle](https://www.kaggle.com/datasets/kazanova/sentiment140).

## Methodology

The project follows a comparative methodology:

1.  **Data Loading and Preprocessing:** The raw tweet data is loaded and cleaned. Preprocessing steps include:
    * Lowercasing
    * Removing URLs, mentions (`@`), and hashtag symbols (`#`).
    * Removing punctuation and numbers.
    * Handling extra whitespaces.
    * Tokenization (splitting text into words).
    * Removing common English stop words.
    * Applying Lemmatization to reduce words to their base form.

2.  **Approach 1: TF-IDF Vectorization**
    * Cleaned text is converted into numerical vectors using `TfidfVectorizer`. This method represents text based on the frequency of words, weighted by their inverse document frequency.
    * A classification model (e.g., Logistic Regression) is trained on these TF-IDF vectors.

3.  **Approach 2: Word Embeddings (Word2Vec)**
    * A Word2Vec model is trained on the corpus to learn dense vector representations (embeddings) for words, capturing semantic relationships.
    * Tweet-level vectors are created by averaging the Word2Vec vectors of the words within each tweet.
    * A classification model (e.g., Logistic Regression, Simple MLP) is trained on these average Word2Vec vectors.

4.  **Evaluation and Comparison:** The performance of the models from both approaches is evaluated using standard metrics such as Accuracy, Precision, Recall, and F1-Score. The results are compared to highlight the differences between TF-IDF and Word Embedding based representations for this task.

5.  **Word Embedding Visualization:** The learned Word2Vec embeddings are prepared for visualization using the [TensorFlow Projector](https://projector.tensorflow.org/) to explore the learned word relationships in a lower-dimensional space.

## Repository Contents

* `nlp_wordembedding.ipynb`: The main Google Colab notebook containing all the code for data loading, preprocessing, model training (TF-IDF and Word2Vec), evaluation, and generating files for the Projector.
* `Report.pdf`: The detailed project report (to be added) covering the problem, methodology, theoretical background (Word Embeddings, TF-IDF, Word2Vec, GloVe, FastText), Projector visualization analysis, results, comparison, and conclusions.
* `vectors.tsv`: File containing the Word2Vec vectors for visualization (generated by the notebook).
* `metadata.tsv`: File containing the corresponding words for the vectors (generated by the notebook).
* (Optional) `sentiment140.zip`: The original dataset file (or instructions on how to download it, as it's large).

## How to Run the Code

The project is implemented as a Google Colab notebook.

1.  Open the `nlp_wordembedding.ipynb` file in Google Colab.
2.  Execute the cells sequentially. The notebook includes steps for:
    * Installing necessary libraries.
    * Downloading and extracting the Sentiment140 dataset using the Kaggle API (requires uploading your `kaggle.json` file).
    * Performing data preprocessing.
    * Splitting data into training and testing sets.
    * Training and evaluating the TF-IDF based model.
    * Training the Word2Vec model.
    * Creating tweet vectors from Word2Vec embeddings.
    * Training and evaluating the Word2Vec based model.
    * Generating `vectors.tsv` and `metadata.tsv` for Projector visualization.

## Results and Evaluation



Initial experiments show that the models achieved an accuracy of approximately **~0.79**. The detailed comparison of TF-IDF and Word2Vec approaches, including Precision, Recall, and F1-Score for both positive and negative classes, can be found in the `Report.pdf`. We observed that [Briefly state a key finding, e.g., "the Word2Vec approach generally performed slightly better, likely due to its ability to capture semantic relationships." or "TF-IDF performed competitively, especially with N-grams."].

## Word Embedding Visualization

The learned Word2Vec embeddings can be visualized using the [TensorFlow Projector](https://projector.tensorflow.org/). Upload the `vectors.tsv` and `metadata.tsv` files generated by the notebook to explore the vector space and observe how words with similar meanings cluster together.


## References


* Sentiment140 Dataset: [https://www.kaggle.com/datasets/kazanova/sentiment140](https://www.kaggle.com/datasets/kazanova/sentiment140)

(https://www.kaggle.com/datasets/kazanova/sentiment140
https://en.wikipedia.org/wiki/Word_embedding
https://aistudio.google.com/prompts/new_chat
https://chatgpt.com/
https://gemini.google.com/app?hl=tr
https://www.ibm.com/think/topics/word-embeddings
https://www.geeksforgeeks.org/word-embeddings-in-nlp/
https://machinelearningmastery.com/what-are-word-embeddings/
https://claude.ai/new
https://stackoverflow.com/questions/68106023/tensorflow-2-5-0-and-gensim-4-0-1-compatibility-with-numpy
https://stackoverflow.com/questions/46168600/gensim-error-importerror-no-module-named-gensim
https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.TfidfVectorizer.html
)

