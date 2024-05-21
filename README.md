# Recommender System 2023 Challenge - Polimi

<p align="center">
  <img width="100%" src="https://i.imgur.com/tm9mSuM.png" alt="header" />
</p>
<p align="center">
    <img src="https://i.imgur.com/mPb3Qbd.gif" width="180" alt="Politecnico di Milano"/>
</p>

This repo contains the code and the data used in the [Polimi's Recsys Challenge 2023](https://www.kaggle.com/competitions/recommender-system-2023-challenge-polimi)
<br>
The goal of the competition was to create a recommender system for books, providing 10 recommendations for each user.

## Results

* MAP@10 - private: &nbsp;0.14095
* MAP@10 - public: &nbsp;0.14147
* Ranked 10th

## Goal
The application domain is book recommendation. 
The datasets we provide contains interactions of users with books, in particular, if the user attributed to the book a rating of at least 4.
The main goal of the competition is to discover which items (books) a user will interact with.

## Data description
The datasets includes around 600k interactions, 13k users, 22k items (books).
The training-test split is done via random holdout, 80% training, 20% test.
The goal is to recommend a list of 10 potentially relevant items for each user. MAP@10 is used for evaluation. You can use any kind of recommender algorithm you wish written in Python. 

## Evaluation
The evaluation metric for this competition was MAP@10.

## Recommender
My best recommender is a hybrid composed of
* SLIM ElasticNet
* RP3Beta

In order to simulate test-case conditions more accurately, we adopted K-Fold cross-validation for both model validation and hyperparameter tuning.

Some interesting notebooks can be found in [Notebooks](/Notebooks)

## Hyperparameter Tuning

Hyperparameter tuning played a pivotal role in enhancing the performance of our recommender system. Initially, we employed skopt and the repository's provided classes, which encompassed common ranges for the various hyperparameters of the model. This approach allowed us to explore the hyperparameter space efficiently and improve the model's effectiveness.

However, to further optimize our model and leverage distributed training, we transitioned to Optuna. Optuna facilitated distributed training, initially on the network and subsequently utilizing a hosted MySQL database. This enabled us to distribute the workload among our personal computers and Kaggle's notebooks, harnessing the collective computing power for more extensive hyperparameter search and tuning. This transition significantly accelerated our optimization process and contributed to the refinement of our recommender system.

## Exploring XGBoost

In our pursuit of maximizing performance, we explored the possibility of integrating XGBoost into our recommender system. This endeavor involved retraining all our models and optimizing them for Recall@25 instead of MAP@10, aiming to leverage the strengths of XGBoost for improved recommendation accuracy. However, despite our efforts, we consistently obtained inferior results compared to our baseline hybrid model. This outcome suggests that we may have made some mistakes in the implementation or parameter tuning of the XGBoosted model. Nevertheless, this experience has provided valuable insights, and we remain commited to revisiting and refining the XGBoosted model in the future. An updated and correct version of the XGBoosted model may emerge in the coming months, reflecting our ongoing commitment to enhancing the performance and robustness of our recommender system.

## Notebooks
Useful notebooks should already be available in the Notebook folder.

## Team
* Jaskaran Ram

## Credits
This repository is based on [Maurizio Dacrema's repository](https://github.com/MaurizioFD/RecSys_Course_AT_PoliMi)
