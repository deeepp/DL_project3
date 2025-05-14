# Deep Learning Project: Adversarial Attacks

This project investigates how deep neural networks can be fooled using adversarial examples. Using a pretrained ResNet-34, we apply three popular attack techniques—FGSM, PGD, and Patch Attack—and evaluate their impact on classification accuracy.

## 📁 File: `Adversarial_Attacks_Final.ipynb`

This notebook contains:
- Setup and evaluation of ResNet-34 on clean data.
- Implementation of:
  - **FGSM (Fast Gradient Sign Method)**
  - **PGD (Projected Gradient Descent)**
  - **Patch-Based Attack**
- Visual comparison of original vs adversarial images.
- Transferability analysis of adversarial examples to DenseNet-121.

---

## 📊 Key Results

| Attack Type     | Accuracy (↓) | Accuracy Drop | Transferability to DenseNet-121 |
|-----------------|--------------|----------------|-------------------------------|
| Clean Images    | **70.40%**   | —              | —                             |
| FGSM Attack     | 39.00%       | ↓ 44.60%       | 94.37%                         |
| PGD Attack      | 38.80%       | ↓ 44.89%       | 84.33%                         |
| Patch Attack    | 27.20%       | ↓ 61.36%       | 61.47%                         |

> ✅ **Observation:** The Patch Attack was highly effective, reducing accuracy the most despite modifying only a small image region.

---

## 🛠️ Technologies Used

- Python 3.x
- PyTorch
- Torchvision
- Matplotlib
- NumPy

---

## ▶️ How to Run

### ✅ Option 1: Google Colab (Recommended)
1. Open [Google Colab](https://colab.research.google.com/).
2. Upload `Adversarial_Attacks.ipynb`.
3. Go to **Runtime > Change runtime type**, and select **GPU**.
4. Run all cells sequentially.

**To unzip and load a dataset in Colab:**
```python
from zipfile import ZipFile
zip_path = "/content/your_dataset.zip"
with ZipFile(zip_path, 'r') as zip_ref:
    zip_ref.extractall("/content/")

### ✅ Option 2: Jupyter Notebook (Local)

```bash
# 1. Install dependencies
pip install torch torchvision matplotlib

# 2. Open the notebook
jupyter notebook Adversarial_Attacks_Final.ipynb

# 3. Run each cell sequentially.
# GPU acceleration is recommended for PGD and Patch attacks


## 🎯 Project Goals

- Demonstrate the vulnerability of image classifiers to adversarial attacks.
- Compare different attack strategies.
- Measure how attacks transfer across architectures.

## 📎 Notes

- Models and datasets are handled via `torchvision`

## 🔍 Attack Parameters
- **FGSM**: ε = 0.02
- **PGD**: ε = 0.02, α = 0.005, iterations = 20
- **Patch Attack**: 32×32 pixel patch, ε = 0.5

## 📊 Dataset
- 500 images subset from ImageNet-1K (100 classes)
- Images preprocessed with ImageNet normalization

