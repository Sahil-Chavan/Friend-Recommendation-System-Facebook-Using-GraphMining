# Friend-Recommendation-System-Facebook-Using-GraphMining
This project is based on the problem statement provided by Facebook on kaggle -> https://www.kaggle.com/c/FacebookRecruiting/overview

### Problem statement:
Given a directed social graph, have to predict missing links to recommend users (Link Prediction in graph)

### About Dataset:
- Our dataset is directed graph data
- We have approx. 1.86M nodes and 9.43M edges.
- Data was obtained from kaggle. You can get data from here https://www.kaggle.com/c/FacebookRecruiting/data
- We have provided only connected nodes. i.e. 9.43M edges. But for each user among n user's, there is n-1 edges. So, for n nodes total possible edges are of 10^12 order.

### Performance metric:

- Both precision and recall is important so F1 score is good choice
- Confusion matrix

### Training Dataset preperation:

If we consider y= 1 , if edge is present in between two nodes.

We will assume y = 0 , if no edge is present.

Generated Bad links from graph which are not in graph and whose shortest path is greater than 2

### Featurization:

Featurization is the most important part of this case study. Below is the list of extracted features


- Similarity measures
- Jaccard Distance
- Cosine distance
- Ranking Measure
- Page Ranking (https://en.wikipedia.org/wiki/PageRank)
- Graph Features
- Shortest Path
- Checking for same community
- Adamic/Adar Index
- Is following back
- Katz Centrality
- Hits Score
- num followers
- num followees
- Weight Features
- weight of incoming edges
- weight of outgoing edges
- weight of incoming edges + weight of outgoing edges
- weight of incoming edges * weight of outgoing edges
- 2*weight of incoming edges + weight of outgoing edges
- weight of incoming edges + 2*weight of outgoing edges
- SVD features using Adjancy matrix. (n_components = 6)
- All the features are calculated for both Followers and Followees

### Models:

We have used two models. RandomForest and XGBOOST. For both one, Follows_back is the most important feature found. Here is the summary result,

| Model | n_estimators | max_depth | Train f1-Score | Test f1-Score |

| Random Forest | 72 | 14 | 0.964 | 0.926 |

| XGBOOST | 76 | 14 | 0.996 | 0.927 |

### Observations:

Understanding of graph and feature engineering was the most important part of this case study.

For Random Forest, Follow_back was the most important feature found, followed by weight, inter_follower and shortest_path.

For XGBOOST, page_rank followed by shortest_path was the most important feature.

Best result was obtained in case of XGBOOST.

XGBOOST took most of time.

For XGBOOST, follows_back was the most important feature. Followed by cosine_follower and weight_f1.
