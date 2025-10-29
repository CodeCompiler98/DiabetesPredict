# Diabetes Prediction API

## Overview
This project provides a machine learning API for predicting diabetes outcomes.
The API is built with FastAPI and containerized with Docker.

## Project Structure
- `train_model.py` → Train and save the ML model.
- `app/main.py` → FastAPI application exposing prediction endpoints.
- `models/` → Directory to store the trained model.
- `requirements.txt` → Python dependencies.
- `Dockerfile` → Docker configuration.

## Setup & Run

### 1. Train the model
```bash
python train_model.py
```

### 2. Run API locally
```bash
uvicorn app.main:app --reload --port 8000
```

### 2a. Test the API locally 
- Go to http://localhost:8000/ to check if the app is running
- Test with CURL to get a response (curl command shown later)

### 3. Build Docker image
```bash
docker build -t diabetes-predictor .
```

### 4. Run Docker container
```bash
docker run -d -p 8000:8000 diabetes-predictor
```
- Test with CURL to get a response (curl command shown later)

## Example Request
```
curl -X POST "http://localhost:8000/predict" \
  -H "Content-Type: application/json" \
  -d '{
    "age": 0.05,
    "sex": 0.05,
    "bmi": 0.06,
    "bp": 0.02,
    "s1": -0.04,
    "s2": -0.04,
    "s3": -0.02,
    "s4": -0.01,
    "s5": 0.01,
    "s6": 0.02
  }'
```
## Example response
{"predicted_progression_score":213.34,
"interpretation":"Above average progression"}

## Troubleshooting
- Ensure the up-to-date WSL version is installed on the system to run Docker
- Check firewall rules to ensure the port is accessible when running the local test
- Verify the Docker Desktop is running and that the path is configured correctly
