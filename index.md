
layout: home
title: Anthony Eckmann


I am a **Machine Learning Engineer** at [Datamap](https://datamap.io) / [posmo.coop](https://posmo.coop), where I build production systems that turn smartphone movement into reliable mobility insights. My work spans the full stack; from real-time data ingestion and public-transport journey reconstruction to model development, validation, and the implementation of advanced machine learning models for continuous, real-time transport-mode detection in the Posmo Project App.

Before joining Datamap, I completed an **MSc in Statistics at ETH Zurich** (2025), where my thesis focused on virtual sample generation for small, high-dimensional datasets, with applications in sports analytics. I also hold a **BSc in Mathematics** from the University of Zurich. I enjoy translating messy real-world data into robust models and pipelines that uncover meaningful patterns and insights.

**Technical expertise:** Machine learning and statistical modelling · data engineering and pipeline development · feature engineering and ETL · Python, SQL and R · model validation and deployment.

**Languages:** German / Swiss German and French (native), English (C2).


## Projects

### Posmo streaming — real-time movement pipeline

Apache Flink backend that ingests live location streams, detects movement vs idle, and persists journeys for downstream analytics and ML.

- Hardened **moving / idle / open-idle** logic, including periodic idle extension without rerunning the full pipeline.
- Improved **incremental persistence** and guards against duplicate or premature writes.
- Refined edge-case handling (short noisy walk segments, static-point checks, car/unknown transitions) to reduce false mode switches.
- Documented pipeline architecture for onboarding and ops.

[github.com/datamapio/posmo_streaming](https://github.com/datamapio/posmo_streaming)


### Public transport map-matching & journey reconciliation

Work on the streaming stack to produce **continuous, map-aligned public-transport journeys** from fragmented GPS and sensor traces.

- **Merged incomplete PT segments** into single journeys and improved reconciliation when trips break across idle gaps.
- **Station detection and snapping** (including wait-at-station and walk-extension-to-snapped-idle cases).
- **PT hold guards** and network API integration (`user_id` on PT routing requests) for more stable transit inference.

Same codebase: [posmo_streaming](https://github.com/datamapio/posmo_streaming)


### Posmo ML microservice — transport-mode inference

FastAPI service ([ml.datamap.io](https://ml.datamap.io)) for hierarchical **UNet + XGBoost fusion**, sensor upload, denoising, and the primary `moving-classification` API used by Flink and the mobile apps.

- Cut **cold-start time** by downloading only the model artifacts required for each deployment.
- Fixed **prediction output mapping** so responses align with supported transport modes and downstream consumers.
- Contributed to **onboarding and inference documentation** for new engineers.

[github.com/datamapio/posmo-ml-microservice](https://github.com/datamapio/posmo-ml-microservice)


### Posmo model dev — training pipelines & experiments

Shared **conda-based training repo** for production Posmo models: U-Net segmentation, XGBoost segment classifiers, MiniRocket/CNN sequence models, GPS autoencoder denoising, and experimental pipelines. Preprocess pulls labels from Postgres and sensor traces from S3 / ML API / DynamoDB; artifacts feed **posmo-ml-microservice** via S3.

- **U-Net v2.0ae** — segment-level train/test split (no window leakage across movements), optional grouped K-fold CV by segment, and day-level inference notebooks; aligned with staged rollout paths in the microservice.
- **DeepViT** — whole-segment transport-mode experiment (GPS kinematics → DeepInsight images → ViT) with optional sensor scalars and grouped `user_id@date` evaluation.
- **MoISP** — GPS-only baseline adapted from Nawaz et al. (2020) to Posmo’s 5–10 s traces: movement stitching, walk/non-walk segmentation, grid features, and ablation/tuning stages (research benchmark, not a production replacement for U-Net + XGBoost).
- **Evaluation & iteration** — pointwise transport-mode comparison reports, U-Net + CRF segmentation experiments, tester-only preprocess filters for faster local runs, and project docs/onboarding for new experiments (`models/_template`).

[github.com/datamapio/posmo_model_dev](https://github.com/datamapio/posmo_model_dev)


### MSc thesis — managing data scarcity in sports analytics

**Managing Data Scarcity in Sports Analytics: Oversampling-Assisted Machine Learning for Forecasting Swiss Elite Climber Results**  
ETH Zurich, Seminar for Statistics · Advisor: Dr. Markus Kalisch · September 2025 · **Grade 6.0/6.0**

Elite climbing teams are small and competitions are few, so standard ML pipelines struggle. I built a **season-long performance score** (adapted IFSC ranking for national and international events), compared it to PageRank, Massey, Colley, and Elo, and used the IFSC-based score as the most stable target for forecasting.

To address limited training data, I implemented two **virtual sample generation (VSG)** methods—Gaussian-mixture sampling for mixed continuous–categorical features and **Bush-SMOTE** along Hamiltonian paths—and evaluated ten supervised learners on a held-out 2024 season.

**Headline results:** tree models gained most from Bush-SMOTE (gradient boosting **RMSE −20%**, **R² 0.17 → 0.58**; XGBoost **R² 0.62** on hold-out). Distance-based models benefited more from GMM augmentation. The work shows that careful augmentation can materially improve prediction when sports datasets are tiny—while noting limits around independence assumptions and over-smoothing.

[Download thesis (PDF)](/assets/MasterThesis_AEckmann.pdf)