

---

The analysis presented in this notebook revolves around the [Jigsaw Toxic Comment Classification Challenge](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge) hosted on [Kaggle](https://www.kaggle.com/). The objective is a **multi-label text classification** problem, where each user comment must be assigned one or more labels from the following categories:

* `toxic`
* `severe_toxic`
* `obscene`
* `threat`
* `insult`
* `identity_hate`

For example, if a comment is both `toxic` and `obscene`, the values under those two categories would be marked as `1`, while the remaining labels would be set to `0`.

---

## Dataset

* The dataset used for this task is the [Jigsaw toxic comment dataset](https://www.kaggle.com/competitions/jigsaw-toxic-comment-classification-challenge/data) provided as part of the competition.
* Specifically, we work with three CSV files: `train.csv`, `test.csv`, and `test_labels.csv`.
* Since the competition has concluded, the labels for the test data have now been made available, allowing us to evaluate model performance on unseen data.

---

## Models Used

To tackle the classification problem, I implemented three different models using TensorFlow:

* **Model 1**: A basic model that leverages a **Bidirectional LSTM** network with **randomly initialized word embeddings** trained from the ground up.
* **Model 2**: An enhanced version of Model 1, where the LSTM network is paired with **pre-trained GloVe embeddings** instead of training embeddings from scratch.
* **Model 3**: A more advanced model based on **BERT**, a transformer-based architecture known for achieving state-of-the-art results on various NLP tasks including classification.

These three approaches were tested and compared to identify which model performs best on the toxic comment classification task.

---


# **Evaluation metric**
For the evaluation of my models in the Toxic Comment Challenge competition, I opted to use the **macro-averaged F1 score** as the reference.
<div align="center">
  
| Model Name         | toxic | severe_toxic | obscene | threat | insult | identity_hate | F1 macro avg |
|--------------------|-------|--------------|---------|--------|--------|---------------|--------------|
| Model I (Baseline) | 0.65  | 0.40         | 0.68    | 0.45   | 0.64   | 0.56          | 0.56         |
| Model II (Glove)   | 0.67  | 0.38         | 0.68    | 0.42   | 0.64   | 0.51          | 0.55         |
| Model III (BERT)   | 0.67  | 0.42         | 0.70    | 0.59   | 0.70   | 0.62          | 0.62         |
  
</div>

<p align="center">
  <img src="img/toxicity_results.png" alt="F1 Score Performance by Label and Model" width="820"/>
</p>


