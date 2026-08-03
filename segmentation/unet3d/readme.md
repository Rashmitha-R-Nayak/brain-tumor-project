
## 🧠 Brain Tumor Segmentation (BraTS 2020) using 3D U-Net (PyTorch)

This repository contains a full deep learning pipeline to perform brain tumor segmentation on the BraTS 2020 dataset using a 3D U-Net implemented in PyTorch.

---

## 🗂️ Project Structure

```

.
├── preprocessing/          # NIfTI → NumPy conversion, normalization, cropping
├── dataset.py              # Custom PyTorch Dataset class for BraTS
├── model.py                # 3D U-Net architecture
├── train.py                # Training + validation loop
├── test.py                 # Evaluation on test set
├── losses\_and\_metrics.py   # Dice Loss, Focal Loss, IoU, etc.
├── utils.py                # Logging, checkpointing, visualization
├── survival\_prediction/    # (Optional) Survival prediction pipeline
├── README.md
└── requirements.txt

````

---

## 🧪 Dataset

- **BraTS 2020 (MICCAI Brain Tumor Segmentation Challenge)**
- Each subject contains 4 MRI modalities: `flair`, `t1`, `t1ce`, `t2`, and a ground truth `seg` mask.
- Segmentation labels:
  - **Label 1**: Necrotic and non-enhancing tumor core (NCR/NET)
  - **Label 2**: Peritumoral edema (ED)
  - **Label 4**: Enhancing tumor (ET)
  - (Note: Label 3 is unused.)

### 🔗 Dataset Link

You can download BraTS 2020 from [https://www.med.upenn.edu/cbica/brats2020/data.html](https://www.med.upenn.edu/cbica/brats2020/data.html)

---

## 🧼 Preprocessing

- Used modalities: `flair`, `t1ce`, `t2`
- Steps:
  - Load `.nii` files
  - Normalize each modality (z-score or min-max)
  - Center crop to `128×128×128`
  - Save as `.npy` arrays
  - One-hot encode segmentation masks
  - Split into `train/val/test` using `splitfolders` (e.g., 70/15/15)

---

## 🧠 Model Architecture

A modified 3D U-Net with configurable input/output channels. The base network includes:

- Encoder with 3D convolutions and max pooling
- Bottleneck layer
- Decoder with upsampling and skip connections
- Final output: softmax over 4 classes

---

## 🏋️ Training Pipeline

- **Losses**: Dice loss, Focal loss, or a combination of both
- **Metrics**: Dice score, mean IoU for WT, TC, and ET
- **Augmentations**: TorchIO (random flip, affine, elastic, intensity)
- **Logging**: TensorBoard and/or CSV
- **Checkpointing**: Saves best model (based on validation Dice)

---

## 📈 Evaluation

- Computed Dice score and mean IoU for:
  - **Whole Tumor (WT)** = label 1 + 2 + 4
  - **Tumor Core (TC)** = label 1 + 4
  - **Enhancing Tumor (ET)** = label 4
- Visualizations of predictions vs ground truth
- Slice-wise and volume-wise evaluation supported

---

## 🧬 (Optional) Survival Prediction

- Extracts deep features from preprocessed MRI scans
- Combines with clinical features (e.g., age, resection status)
- Predicts patient survival days (regression) or survival class (classification)
- Optionally uses pre-trained CNNs or handcrafted features

---

## 🛠️ Requirements

- Python 3.8+
- PyTorch 1.12+
- TorchIO
- NumPy
- nibabel
- scikit-learn
- pandas
- matplotlib
- tensorboard
- tqdm
- splitfolders

Install all dependencies using:

```bash
pip install -r requirements.txt
````

---

## 🚀 How to Run

### 1. Preprocess the Data

```bash
python preprocessing/preprocess.py --data_dir /path/to/BraTS2020_TrainingData/
```

### 2. Train the Model

```bash
python train.py --config config.yaml
```

### 3. Evaluate the Model

```bash
python test.py --weights checkpoints/best_model.pth
```

### 4. (Optional) Survival Prediction

```bash
python survival_prediction/train_regressor.py --features_dir features/ --labels_csv survival_labels.csv
```

---

## 📸 Sample Results

| Modality   | Ground Truth          | Prediction                |
| ---------- | --------------------- | ------------------------- |
| T1ce Slice | ![gt](samples/gt.png) | ![pred](samples/pred.png) |

---

## 📌 Acknowledgments

* [BraTS 2020 Challenge](https://www.med.upenn.edu/cbica/brats2020/)
* CBICA @ University of Pennsylvania
* MICCAI community
* 3D U-Net inspiration: \[Isensee et al., nnU-Net]

---

## 📄 License

This project is licensed under the MIT License. See `LICENSE` for more details.

```




