# Network Security ML Project
  
**Description:**  
A Machine Learning pipeline and FastAPI web application to detect phishing websites using the UCI Phishing Websites dataset. The repository includes data ingestion, validation, transformation, model training, and deployment via Docker, ready for CI/CD integration with GitHub Actions.  

---

## Table of Contents

- [Project Overview](#project-overview)  
- [Dataset](#dataset)    
- [Installation](#installation)  
- [Running the App with Docker](#running-the-app-with-docker)  
- [ML Pipeline](#ml-pipeline)
- [Usage Example](#usage-example)
- [CI/CD](#cicd)  
- [API Endpoints](#api-endpoints)  
- [Contributing](#contributing)   

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


---

## Installation

1. Clone the repository:

```bash
git clone https://github.com/ManelHjaoujia/networksecurity.git
cd networksecurity
```

2. Create a virtual environment and activate it
```bash
python -m venv venv         
source venv/bin/activate  # Linux/Mac           
venv\Scripts\activate     # Windows
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

## Running the App with Docker

You have **two options** to use Docker with this project:

---

### **Option 1: Build and Run Locally**

1. Build the Docker image:
```bash
docker build -t manelhjaoujia07/networksecurity:latest .
```

2. Run the container:
```bash
docker run -p 8000:8000 -e MONGODB_URL_KEY="<your_mongo_uri>" manelhjaoujia07/networksecurity:latest
```

3. Access the FastAPI Swagger UI:
```bash
http://localhost:8000/docs
```

### **Option 2: Pull the Image from Docker Hub**

1. Pull the image from Docker Hub:
```bash
docker pull manelhjaoujia07/networksecurity:latest
```

2.Run the container:
```bash
docker run -p 8000:8000 -e MONGODB_URL_KEY="<your_mongo_uri>" manelhjaoujia07/networksecurity:latest
```

3. Access the FastAPI Swagger UI:
```bash
http://localhost:8000/docs
```

## ML Pipeline

The pipeline consists of the following steps:

### 1. Data Ingestion
- Downloads and stores the dataset in MongoDB.

### 2. Data Validation
- Ensures features and labels meet quality requirements.

### 3. Data Transformation
- Handles missing values.
- Scales numerical features.
- Encodes categorical features.

### 4. Model Training
- Trains multiple classifiers:
  - Random Forest
  - Decision Tree
  - Gradient Boosting
  - Logistic Regression
  - AdaBoost
- Performs hyperparameter tuning.
- Logs metrics with MLflow:
  - F1 Score
  - Precision
  - Recall
- Saves the best model and preprocessor.

## Usage Example

Predict phishing websites using a CSV file:
```bash
curl -X POST "http://localhost:8000/predict" -F "file=@sample.csv"
```

## CI/CD

The project is ready for **GitHub Actions CI/CD**:

### GitHub Secrets

| Secret Name        | Value                          |
|-------------------|--------------------------------|
| `DOCKERHUB_USERNAME` | Your Docker Hub username       |
| `DOCKERHUB_TOKEN`    | Docker Hub access token       |

### Workflow

- Runs unit tests.
- Builds the Docker image.
- Pushes the image to Docker Hub.

  ## API Endpoints

| Endpoint    | Method | Description                                           |
|------------|--------|-------------------------------------------------------|
| `/`        | GET    | Redirects to `/docs`                                  |
| `/train`   | GET    | Runs the full ML pipeline and trains models          |
| `/predict` | POST   | Upload CSV and get predictions (returns HTML table)  |

## Contributing

1. Fork the repository.  
2. Create a feature branch:
```bash
git checkout -b feature/xyz
```
3. Commit your changes:
```bash
git commit -m "Add feature"
```
4. Push to your branch:
 ```bash
git push origin feature/xyz
```
5. Create a Pull Request

