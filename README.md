# Network Security ML Project
  
**Description:**  
A Machine Learning pipeline and FastAPI web application to detect phishing websites using the UCI Phishing Websites dataset. The repository includes data ingestion, validation, transformation, model training, and deployment via Docker, ready for CI/CD integration with GitHub Actions.  

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Dataset](#dataset)  
- [Project Structure](#project-structure)  
- [Installation](#installation)  
- [Running the App with Docker](#running-the-app-with-docker)  
- [ML Pipeline](#ml-pipeline)  
- [Model Training](#model-training)  
- [CI/CD](#cicd)  
- [API Endpoints](#api-endpoints)  
- [Contributing](#contributing)  
- [License](#license)  

---

## Project Overview

This project aims to detect phishing websites using machine learning. It provides:  

- **Data ingestion, validation, and transformation**  
- **Multiple model training with hyperparameter tuning**  
- **MLflow experiment tracking**  
- **FastAPI web interface for training and predictions**  
- **Dockerized deployment** and CI/CD pipeline  

The solution is modular, maintainable, and ready for production use.

---

## Dataset

**Source:** [UCI Phishing Websites Dataset](https://archive.ics.uci.edu/dataset/327/phishing+websites)  

- Contains features extracted from websites (URL, HTML, and server features)  
- Goal: Classify websites as phishing (malicious) or legitimate  
- Preprocessing and transformation are handled in the pipeline  

---

## Project Structure

networksecurity/
│
├── app.py # FastAPI main application
├── requirements.txt # Python dependencies
├── Dockerfile # Docker configuration
├── templates/ # HTML templates for predictions
├── final_model/ # Saved models and preprocessor
├── networksecurity/
│ ├── components/
│ │ ├── data_ingestion.py
│ │ ├── data_validation.py
│ │ ├── data_transformation.py
│ │ └── model_trainer.py
│ ├── entity/ # Config and artifact entities
│ ├── exception/
│ ├── logging/
│ └── utils/
