# 🧠 Classification Ensemble Pipeline

This folder contains scripts and outputs for ensembling multiple classification models (e.g., DenseNet121, InceptionV4, CustomCNN) for **brain tumor classification** from MRI images.

---

## 📂 Contents

- `ensemble_predict.py` — Inference script to run and combine predictions
- `ensemble_utils.py` — Utilities for soft-voting / averaging
- `ensemble_output.csv` — Final prediction results on test set
- `confusion_matrix.png` — Ensemble confusion matrix
- `classification_report.txt` — Final report with precision/recall/F1
- `README.md` — This file

---

# 🧠 Ensemble Classification of Brain Tumors

This setup combines multiple trained models to improve brain tumor classification performance by using soft voting or probability averaging.

---

## 🧠 Classification Task

- **Input**: T1-weighted MRI brain images (size: 256×256)
- **Output**: Tumor Class (Multi-class)
  - `0`: No Tumor  
  - `1`: Glioma  
  - `2`: Meningioma  
  - `3`: Pituitary

---

## 🤖 Models Used in Ensemble

- ✅ DenseNet121 (`densenet_best_model.pth`)
- ✅ InceptionV4 (`inceptionv4_best_model.pth`)
- ✅ CustomCNN (`custom_model.pth`)
- (Optional) EfficientNet-B4, ResNet, etc.

Each model outputs per-class probabilities which are averaged during inference.

---

## ⚙️ Ensemble Strategy

- **Type**: Soft Voting Ensemble
- **Mechanism**: Average class probabilities from each model
- **Final Prediction**: Class with highest averaged probability

---

## 📊 Output

- Combined classification report (precision, recall, F1-score)
- Confusion matrix visualization
- CSV file of final predictions
- Optionally: Per-model performance comparison

---

## 🧪 Inference Example

```python
from ensemble_utils import load_models, predict_ensemble

models = load_models([
    'densenet_best_model.pth',
    'inceptionv4_best_model.pth',
    'custom_model.pth'
])

preds = predict_ensemble(models, test_loader, device="cuda")
