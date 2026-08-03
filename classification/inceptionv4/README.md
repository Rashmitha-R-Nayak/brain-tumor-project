# 🧠 InceptionNet V4 Pipeline

This folder contains all scripts, models, and outputs related to the **InceptionNet V4** model used for brain tumor classification.

---

## 📂 Contents

- `inceptionv4_train.ipynb` — Full training notebook for InceptionNet V4
- `inceptionv4_utils.py` — Custom model/metrics/dataloaders
- `inceptionv4_best_model.pth` — Best saved model (not on GitHub if >100MB)
- `inceptionv4_logs.csv` — Training logs
- `inceptionv4_predictions/` — Folder for test-time results & visualizations

---

# 🧠 InceptionNet V4 for Brain Tumor Classification

This folder contains all code and outputs related to the **InceptionNet V4-based classification model** used for identifying brain tumor types from MRI scans.

---

## 🧠 Classification Task

- **Input**: T1-weighted MRI brain images (size: 256×256 or 299×299)
- **Output**: Tumor Class (Multi-class)
  - `0`: No Tumor
  - `1`: Glioma
  - `2`: Meningioma
  - `3`: Pituitary

---

## ⚙️ Model Configuration

- Architecture: `InceptionNet V4` (pretrained)
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

---

## 🔧 Model Info

- Architecture: InceptionNet V4
- Input Size: 299x299 (resized to 256x256 if needed)
- Optimizer: Adam / SGD
- Loss: CrossEntropyLoss

---

## 📝 Notes

- Model trained on BrainMRI dataset.
- Results may vary based on augmentation and data balancing.
- See main `README.md` for how to run this pipeline.

---

> 📌 Tip: You can download large files (models, data) from linked Google Drive if needed.
