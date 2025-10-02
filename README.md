#🐍 Django + scikit-learn: Iris Predictor

An end-to-end Django + scikit-learn app: train a model, serve predictions via a web form and a JSON API, and run basic tests.
The project trains a RandomForestClassifier on the Iris dataset and caches the loaded model for fast inference.

Quick start: train python train.py → run server python manage.py runserver → open http://127.0.0.1:8000/.
