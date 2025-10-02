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



## 📁 Project Structure
django-ml-app/
├─ mlapp/
│  ├─ settings.py
│  ├─ urls.py
│  └─ ...
├─ predictor/
│  ├─ model/                # created by train.py
│  │  └─ iris_rf.joblib     # trained model
│  ├─ forms.py              # 4 numeric inputs
│  ├─ services.py           # load/cache model + predict()
│  ├─ urls.py               # app routes
│  ├─ views.py              # web views + API
│  └─ tests.py              # minimal tests
├─ templates/
│  └─ predictor/
│     └─ predict_form.html  # HTML form template
├─ manage.py
├─ train.py                 # training & saving model bundle
└─ requirements.txt         # optional dependencies file




## ⚡ Setup

# 1) clone (or copy)
# git clone <this-repo> && cd django-ml-app

# 2) virtualenv
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate

# 3) dependencies
pip install -U pip
pip install Django scikit-learn joblib numpy

# 4) migrations
python manage.py migrate

# 5) (optional) admin user
# python manage.py createsuperuser



## 🧠 Model Training

Run the training script to fit the model and save the bundle:
    python train.py
        
         -> Saved model to .../predictor/model/iris_rf.joblib


## 🌐 Web UI

Start the dev server:
    
    python manage.py runserver



## 🔗 REST API

Endpoint: POST /api/predict/
Content-Type: application/json (preferred) or application/x-www-form-urlencoded.

Required fields:

  sepal_length — float

  sepal_width — float

  petal_length — float

  petal_width — float

Example (curl):

        curl -X POST http://127.0.0.1:8000/api/predict/ \
         -H "Content-Type: application/json" \
         -d '{"sepal_length":5.1,"sepal_width":3.5,"petal_length":1.4,"petal_width":0.2}'


Response:

    {
    "class_index": 0,
    "class_name": "setosa",
    "probabilities": {
      "setosa": 1.0,
      "versicolor": 0.0,
      "virginica": 0.0
    }
    }


Core inference logic lives in predictor/services.py → predict_iris().



