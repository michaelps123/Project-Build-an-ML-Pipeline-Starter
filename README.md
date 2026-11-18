# NYC Short-Term Rental Price Prediction — ML Pipeline

A configurable machine-learning pipeline for predicting short-term rental prices in New York City.

Developed as part of the WGU/Udacity Machine Learning DevOps coursework, this project demonstrates how to organize data preparation, validation, model training, and experiment tracking into a repeatable ML workflow.

## Project Overview

Short-term rental pricing depends on property characteristics, location, and market conditions. As new rental listing data becomes available, an ML workflow should support consistent data processing, model evaluation, and retraining.

This project implements a multi-stage workflow using **Python, MLflow, Weights & Biases, Hydra, and scikit-learn**.

## ML Pipeline

The workflow contains five main stages:

1. **Data Acquisition** — Retrieve rental listing data and register the input artifact.
2. **Data Cleaning** — Filter records and remove prices outside configured thresholds.
3. **Data Validation** — Perform data quality and distribution checks.
4. **Data Splitting** — Create training, validation, and test datasets.
5. **Model Training** — Train a Random Forest regressor and export the resulting model artifact.

The pipeline uses MLflow to orchestrate individual components and Weights & Biases to track experiments and data artifacts.

Hydra configuration allows pipeline parameters to be changed without modifying the orchestration code.

## Technologies

| Technology | Purpose |
|---|---|
| Python | Data processing and ML development |
| scikit-learn | Random Forest regression |
| MLflow | Pipeline component orchestration |
| Weights & Biases | Experiment and artifact tracking |
| Hydra | Configuration management |
| pandas | Data manipulation |

## Configuration and Reproducibility

The `config.yaml` file defines configurable elements including:

- Data filtering thresholds
- Training and validation splits
- Random seed
- Random Forest hyperparameters
- Pipeline execution steps

The pipeline supports running the entire workflow or selecting individual processing stages.

The default configuration uses an 80/20 train-test split, with a further validation split from the training portion, and random seed `42`.

## Experiment Tracking

The project was developed using Weights & Biases for experiment and artifact tracking.

**[View the NYC Airbnb project on Weights & Biases](https://wandb.ai/mpschneider/nyc_airbnb)**

Model evaluation and experiment history can be reviewed through the associated tracking project, subject to artifact availability and access permissions.

## Running the Pipeline

The provided environment configuration specifies Python 3.13 and Conda.

```bash
git clone https://github.com/michaelps123/Project-Build-an-ML-Pipeline-Starter.git
cd Project-Build-an-ML-Pipeline-Starter

conda env create -f environment.yml
conda activate nyc_airbnb_dev

wandb login
mlflow run .
```

Run selected stages:

```bash
mlflow run . -P steps=download,basic_cleaning
```

Additional options and model parameters are maintained in `config.yaml`.

**Environment note:** The workflow uses Conda-managed MLflow components. This repository documents the original project environment; the complete pipeline has not been revalidated on the current development machine.

## Project Scope and Limitations

This is an educational MLOps workflow, not a deployed rental pricing service.

The project demonstrates configurable pipeline execution, model development, and experiment tracking. Automated scheduling, production monitoring, and live inference deployment are outside its scope.

Model performance depends on the underlying dataset, sampling, preprocessing, and training configuration.

## Attribution

Developed as part of the Udacity Machine Learning DevOps curriculum completed through WGU.

Based on the [Udacity Project Build an ML Pipeline Starter](https://github.com/udacity/Project-Build-an-ML-Pipeline-Starter), which supplies the project structure and reusable components.

The completed coursework implementation includes configuration and integration of the data-processing, validation, and training stages.

This repository is retained as a portfolio demonstration of foundational data engineering and MLOps concepts.
