# 🧠 DenseNet Pipeline

This folder contains all scripts, models, and outputs related to the **DenseNet** model used for brain tumor classification .

---

## 📂 Contents

- `densenet_train.ipynb` — Full training notebook for DenseNet
- `densenet_utils.py` — Custom model/metrics/dataloaders
- `densenet_best_model.pth` — Best saved model (not on GitHub if >100MB)
- `densenet_logs.csv` — Training logs
- `densenet_predictions/` — Folder for test-time results & visualizations

---
# 🧠 DenseNet for Brain Tumor Classification

This folder contains all code and outputs related to the **DenseNet-based classification model** used for identifying brain tumor types from MRI scans.

---


## 🧠 Classification Task

- **Input**: T1-weighted MRI brain images (size: 256×256)
- **Output**: Tumor Class (Multi-class)
  - `0`: No Tumor
  - `1`: Glioma
  - `2`: Meningioma
  - `3`: Pituitary

---

## ⚙️ Model Configuration

- Architecture: `DenseNet121` (pretrained)
- Loss: `CrossEntropyLoss`
- Optimizer: `Adam`
- Learning Rate: e.g., `1e-4`
- Dataset: BRISC (or your dataset name)

---

## 📊 Output

- Classification report
- Confusion matrix
- Grad-CAM visualizations
- Accuracy / loss curves

---

> 💡 Refer to the main project README for environment setup and dataset instructions.

## 🔧 Model Info

- Architecture: DenseNet-121
- Input Size: 256x256
- Optimizer: Adam / SGD
- Loss: CrossEntropy + Dice (for segmentation)

---

## 📝 Notes


- Model trained on BrainMRI dataset.
- See main `README.md` for how to run this pipeline.

---

> 📌 Tip: You can download large files (models, data) from linked Google Drive if needed.
