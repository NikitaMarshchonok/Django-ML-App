# 🐍 Django + scikit-learn: Iris Predictor

An end-to-end Django + scikit-learn app: train a model, serve predictions via a web form and a JSON API, and run basic tests.
The project trains a RandomForestClassifier on the Iris dataset and caches the loaded model for fast inference.

Quick start: train python train.py → run server python manage.py runserver → open http://127.0.0.1:8000/.


## 📋 Table of Contents

Features
Tech Stack
Project Structure
Setup
Model Training
Web UI
REST API
Tests
Environment Variables
Troubleshooting
Roadmap
License


## ✅ Features
  
  Train RandomForestClassifier on the Iris dataset (4 numeric features).
  
  Save a bundle (estimator, feature_names, target_names) using joblib.
  
  Django inference service with:
                            
                            Web form (4 numeric inputs).
                            
                            JSON API POST /api/predict/.
  
  In-process model caching (services.py) for low-latency predictions.
  
  Minimal tests: homepage renders, API returns valid prediction.


## 🛠 Tech Stack

Python 3.10+

Django 4/5

scikit-learn, joblib, numpy
