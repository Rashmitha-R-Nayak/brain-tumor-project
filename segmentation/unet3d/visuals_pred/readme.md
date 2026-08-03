# 🧩 Brain Tumor Segmentation – Visual Predictions

This folder contains visual comparisons between the predicted segmentation masks and the ground truth annotations for the BraTS 2020 dataset.

Each image represents:
- A single 2D slice from a 3D brain MRI scan
- Model predictions overlaid on the corresponding modality (typically T1ce or FLAIR)
- Ground truth masks for reference

---

## 📁 Contents

The images in this folder follow the naming convention:

<case_id><slice_id><view>.png

yaml
Copy
Edit

Where:
- `case_id` is the subject/patient ID (e.g., `BraTS20_001`)
- `slice_id` is the index of the axial slice shown
- `view` can be one of:
  - `input` – MRI slice (e.g., T1ce)
  - `ground_truth` – Ground truth mask
  - `prediction` – Model prediction
  - `overlay_gt` – Overlay of GT mask on MRI
  - `overlay_pred` – Overlay of prediction on MRI

---

## 🎨 Class Color Mapping

| Label               | Class ID | Color (RGB)     |
|--------------------|----------|-----------------|
| Background          | 0        | Black `(0, 0, 0)`  
| NCR/NET (Core)      | 1        | Red `(255, 0, 0)`
| Edema (ED)          | 2        | Green `(0, 255, 0)`
| Enhancing Tumor (ET)| 4        | Blue `(0, 0, 255)`

*Note: Some tools might remap label 4 → 3 to keep labels contiguous.*

---

## 🧠 Examples

| Input (T1ce) | Ground Truth | Prediction |
|--------------|---------------|-------------|
| ![input](samples/input_example.png) | ![gt](samples/gt_example.png) | ![pred](samples/pred_example.png) |

---

## 📝 Notes

- Images are saved using matplotlib or OpenCV in PNG format.
- You can regenerate these using the `utils.py` or visualization code provided in the main repository.
- Visual inspection is useful for debugging segmentation errors or evaluating clinical relevance.

---

## 📌 Tip

To view all predictions as a slideshow:

```bash
# On Linux/macOS
xdg-open .
# On Windows
start .
