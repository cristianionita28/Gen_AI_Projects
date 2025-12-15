# Face Recognition on LFW dataset: PCA+SVC vs DLIB Embeddings + LinearSVC

This project compares two approaches for recognizing people in images using the **LFW (Labeled Faces in the Wild)** dataset:

1. **Classic ML pipeline:** flatten images ➜ PCA dimensionality reduction ➜ Linear SVC classifier  
2. **Modern face embeddings:** DLIB (`face_recognition`) ➜ face embeddings ➜ Linear SVC classifier

The notebook trains both models and evaluates accuracy on a held-out test set.
Note: face_recognition is a Python wrapper over the C++ library DLIb. 
face_recognition includes dlib.
---

## What the code does (quick)
- Loads LFW people faces from `sklearn.datasets.fetch_lfw_people`
- We use the Labeled Faces in the Wild (LFW) people dataset from sklearn, which is a database of aligned grayscale face photographs. 
- It contains 13,233 images of 5,749 people. 
- Each image is centered on a single face. 
- Splits into train/test
- Trains:
  - **PCA + LinearSVC** on image features
  - **DLIB embeddings + LinearSVC** on 128D face encodings
- Prints accuracy and lets you visualize predictions on example images

---

## Results
Accuracy on face recognintion with SVC model = 48%
Accuracy on face recognintion with dlib and face_recognition model = 48%

---

## Repository contents
- `face_recognition_SVC_vs_DLIB_plus_SVC.ipynb` — main notebook containing:
  - dataset loading
  - visualization
  - PCA+SVC training
  - DLIB embeddings extraction
  - evaluation + accuracy printing

---

## Run the notebook online

### ▶️ Binder (recommended)

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/cristianionita28/Gen_AI_Projects/HEAD?urlpath=%2Fdoc%2Ftree%2FAI_Project_5_Face_Recognition%2FFace_recognition_SVC_vs_DLB.ipynb)

https://mybinder.org/v2/gh/cristianionita28/Gen_AI_Projects/HEAD?urlpath=%2Fdoc%2Ftree%2FAI_Project_5_Face_Recognition%2FFace_recognition_SVC_vs_DLB.ipynb

### ▶️ Google Colab
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](
https://colab.research.google.com/github/USERNAME/REPO_NAME/blob/main/facerec.ipynb
)



## Requirements for local running
Recommended environment (Python 3.9+):

- numpy
- matplotlib
- scikit-learn
- face_recognition *(DLIB wrapper)*


Install dependencies:

conda/mamba env create -f environment.yaml
conda/mamba activate base
pip install -r requirments.txt

Note: mamba is exactly like conda but has a solver which is 100 times faster. 
Mamba uses the same syntax and the same channels and libraries as conda. 
So it is a good practice to install and always use mamba!