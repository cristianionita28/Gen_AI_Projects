
# BERT IMDB Sentiment Classifier

Proiect Generative AI cu BERT
Autor: Prof. Cristian

## 📌 Descriere
Acest proiect antrenează și evaluează un model BERT pentru clasificarea sentimentului în dataset-ul IMDB.  
Modelul poate determina dacă o recenzie de film este **pozitivă** sau **negativă**.
in al 2lea exercitiu sunt clasificate o lista de SMS-uri text in spam si not spam. 

## 🧠 Tehnologii folosite
- Python 3.10  
- PyTorch  
- HuggingFace Transformers  
- HuggingFace Datasets  
- Scikit-learn  
- NumPy / Pandas  

## 📦 Instalare

### 1. Creează environment-ul conda:
```bash
mamba env create -f environment.yaml
mamba activate udacity-genai
pip install -r requirements.txt

### Rulare
python Exercise2-BERT-IMDB-sentiment-classifier.py
