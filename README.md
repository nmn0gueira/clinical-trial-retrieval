# Clinical Trial Information Retrieval System
This project aims to develop an **Information Retrieval (IR) system** that matches patient cases with clinical trials using ranking models. This project was implemented in three phases, each building upon the previous one to enhance the retrieval process.

**Note**: This repository started with the development of the third phase of the project and this README file functions as a high-level overview of the project.


## Project Overview
### Phase 1: Traditional Retrieval Models
The first phase of the project involved implementing traditional retrieval models, specifically the **Vector Space Model (VSM)** and the **Language Model with Jelinek-Mercer Smoothing (LMJM)**. These models were used to establish a baseline for the retrieval process. The VSM model represents documents and queries as vectors in a high-dimensional space, while LMJM uses probabilistic methods to rank documents based on their relevance to a given query.

### Phase 2: Learning to Rank Models
The second phase of the project focused on implementing **Learning to Rank (LETOR)** models. These models leverage logistic regression to learn a ranking function from labeled training data. The goal was to improve the ranking of documents based on their relevance to a given query. 

#### Training the model
The LETOR model was trained using features extracted from the VSM and LMJM models and using the `qrels-clinical_trials.txt` for reference on document relevance to a given clinical trial. While this file labels most query-document pairs, it does not provide a complete set of labels and is not exhaustive so different variants of the model were trained with different datasets using different strategies to handle the missing labels.

The training data was split into a training set and a validation set, and the model was evaluated using metrics such as Mean Average Precision (MAP) and Normalized Discounted Cumulative Gain (NDCG).

### Phase 3: Contextual Embeddings
In the third phase, a new Learning to Rank model was implemented using **BioBERT**, a pre-trained transformer model specifically designed for biomedical text mining. 

BioBert extracted contextual embeddings from the clinical trial documents and queries, which were then used to train a new Learning to Rank model. The embeddings would capture the semantic meaning of the text, allowing for more accurate matching of patient cases with clinical trials.

#### Embedding Visualization
This phase of the project also involved analyzing the embeddings generated by BioBERT. Different visualizations were created to analyze the embeddings and their impact on the retrieval process. 

The tokens visualized were the 10 tokens with the highest attention weights averaged across all heads in the last layer for a selected query-document pair of relevance to each other. **This is not a perfect representation of the embeddings, but it provides some insight into the transformer's focus.**

Visualizations included:
- Scatter plot of the tokens in layer one against layer 12. Data is represented as a 2D scatter plot using PCA for dimensionality reduction.
- Heatmap of the attention weights for the top 10 tokens in the last layer.
- Self-attention visualization of the top 10 tokens in a given layer/head.

## Download Data
The clinical trials archive can be downloaded [here](https://drive.google.com/file/d/1NxJotBxAcjib8XXgz_hseSIQSNsdu4HX/view?usp=sharing).


## About
This project was developed as part of the Information Retrieval (2023/2024) course at FCT-UNL.