---
layout: home
title: Anthony Eckmann
---

I am a **Machine Learning Engineer** at [Datamap](https://datamap.io) / [posmo.coop](https://posmo.coop), where I build production systems that turn smartphone movement into reliable mobility insights. My work spans the full stack; from real-time data ingestion and public-transport journey reconstruction to model development, validation, and the implementation of advanced machine learning models for continuous, real-time transport-mode detection in the Posmo Project App.

Before joining Datamap, I completed an **MSc in Statistics at ETH Zurich** (2025), where my thesis focused on virtual sample generation for small, high-dimensional datasets, with applications in sports analytics. I also hold a **BSc in Mathematics** from the University of Zurich. I enjoy translating messy real-world data into robust models and pipelines that uncover meaningful patterns and insights.

**Technical expertise:** Machine learning and statistical modelling · data engineering and pipeline development · feature engineering and ETL · Python, SQL and R · model validation and deployment.

**Languages:** German / Swiss German and French (native), English (C2).


## Projects

### Real-time data pipeline

I maintain and optimize the streaming pipeline behind the [Posmo Project App](https://apps.apple.com/app/posmo-project/id1619128694) ([Android](https://play.google.com/store/apps/details?id=io.datamap.posmoproject)) and [Posmo](https://posmo.coop). The goal of the app is to create a continuous, automated mobility diary that fills itself in: GPS and onboard sensor data — motion and activity signals — are collected throughout the day by the phone. The pipeline’s job is to turn that raw stream into recognizable trips including GPS traces and transport mode information.

Traces are processed per person on Apache Flink as they arrive. The stream is segmented into stays and movements, denoised, and passed to the transport-mode detection models for inference, including trace routing for public transport. What comes back is a continuous timeline a participant can correct and validate, and the (anonymized) mobility record a [Posmo Tracking](https://posmo.coop/products/tracking) project analyses.


### Transport-mode detection models

I develop new segmentation and classification models for the transport-mode detection in the [Posmo Project App](https://apps.apple.com/app/posmo-project/id1619128694). Segmentation splits a trace into movements. Classification assigns each movement its transport mode. I train and evaluate both on labelled traces from the live system, and compare candidates with the models the app currently runs.



### Mobility dashboards

I build analytics dashboards for customers working with mobility data from a [Posmo Tracking](https://posmo.coop/products/tracking) project. A dashboard reads the journeys the app has collected — distance, mode, time of day, and how the study is filling in — so a city or a research group can analyse the data on [posmo.coop](https://posmo.coop).



### MSc thesis

**Managing Data Scarcity in Sports Analytics: Oversampling-Assisted Machine Learning for Forecasting Swiss Elite Climber Results**  
ETH Zurich, Seminar for Statistics · Advisor: Dr. Markus Kalisch · September 2025

Elite climbing teams are small and competitions are few, so standard ML pipelines struggle. I built a **season-long performance score**, compared it to state of the art ranking algorithms (Google PageRank, Massey, Colley and Elo) and used the score as the most stable target for forecasting.

To address limited training data, I implemented two **virtual sample generation (VSG)** methods; Gaussian-mixture sampling for mixed continuous–categorical features and an adapted **SMOTE** for continuous features (which i developed) along Hamiltonian paths, and evaluated ten supervised learners on a held-out 2024 season.

**Headline results:** tree models gained most from my adapted SMOTE (gradient boosting **RMSE −20%**, **R² 0.17 → 0.58**; XGBoost **R² 0.62** on hold-out). Distance-based models benefited more from GMM augmentation. The work shows that careful augmentation can materially improve prediction when datasets are tiny while noting limits around independence assumptions and over-smoothing.

[Download thesis (PDF)](/assets/MasterThesis_AEckmann.pdf)