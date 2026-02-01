# H&E Histopathology Tissue Classification with Explainable AI

**Multi-class classification of colorectal cancer tissue from H&E stained microscopy images**

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red.svg)
![Accuracy](https://img.shields.io/badge/Accuracy-99.77%25-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

## Project Overview

This project demonstrates an end-to-end deep learning pipeline for classifying tissue types from H&E (Hematoxylin & Eosin) stained histopathology images. The approach is directly applicable to **pediatric cancer research**, where accurate tissue classification supports diagnosis and treatment selection.

### Key Features
- 9-class tissue classification (tumor, stroma, lymphocytes, etc.)
- Transfer learning with EfficientNet-B0
- GradCAM explainability for clinical interpretability
- Comprehensive evaluation with confusion matrices and per-class metrics

## Results

| Metric | Value |
|--------|-------|
| Test Accuracy | **99.77%** |
| Quadratic Weighted Kappa | **0.9985** |
| Tumor Detection AUC | **1.0000** |
| Tumor Precision | 99.49% |
| Tumor Recall (Sensitivity) | 99.86% |
| Tumor F1 Score | 0.9967 |

### Per-Class Performance

| Clinical Group | Class | Accuracy |
|----------------|-------|----------|
| Tumor-related | TUM (Tumor) | 99.9% |
| Tumor-related | STR (Stroma) | 99.2% |
| Immune | LYM (Lymphocytes) | 100.0% |
| Normal tissue | NORM (Normal mucosa) | 99.6% |
| Normal tissue | MUS (Smooth muscle) | 99.7% |
| Normal tissue | ADI (Adipose) | 99.9% |
| Other | MUC (Mucus) | 99.7% |
| Other | DEB (Debris) | 99.9% |
| Other | BACK (Background) | 100.0% |

## Dataset

**NCT-CRC-HE-100K**: 100,000 H&E stained image patches from colorectal cancer tissue

### Download

- **Kaggle**: [kaggle.com/datasets/imrankhan77/nct-crc-he-100k](https://www.kaggle.com/datasets/imrankhan77/nct-crc-he-100k)
- **Zenodo** (Original): [zenodo.org/records/1214456](https://zenodo.org/records/1214456)

### Tissue Classes

| Class | Description | Clinical Relevance |
|-------|-------------|-------------------|
| **TUM** | Colorectal adenocarcinoma epithelium | Primary tumor tissue |
| **STR** | Cancer-associated stroma | Tumor microenvironment |
| **LYM** | Lymphocytes | Immune infiltration |
| **MUC** | Mucus | Mucinous differentiation |
| **MUS** | Smooth muscle | Normal tissue boundary |
| **NORM** | Normal colon mucosa | Healthy tissue |
| **ADI** | Adipose tissue | Fat tissue |
| **DEB** | Debris | Processing artifacts |
| **BACK** | Background | Non-tissue regions |

## Quick Start

### Run on Kaggle

1. Go to the [NCT-CRC-HE-100K dataset](https://www.kaggle.com/datasets/imrankhan77/nct-crc-he-100k)
2. Click **"New Notebook"**
3. Upload the notebook or copy the code
4. Enable **GPU**: Settings → Accelerator → GPU P100
5. Run all cells

### Run Locally

```bash
# Clone repository
git clone https://github.com/Joana-Mansa/HnE_tissue_classification.git
cd HnE_tissue_classification

# Install dependencies
pip install torch torchvision numpy pandas matplotlib seaborn scikit-learn opencv-python tqdm pillow

# Download dataset and update DATA_DIR path in notebook
# Run notebook
jupyter notebook h-e-tissue-classification.ipynb
```

## Project Structure

```
├── h-e-tissue-classification.ipynb    # Main notebook
├── README.md                           # This file
├── requirements.txt                    # Dependencies
└── outputs/
    ├── he_tissue_classifier_final.pth  # Trained model
    ├── training_curves.png             # Loss/accuracy plots
    ├── confusion_matrix.png            # Evaluation results
    └── gradcam_visualizations.png      # Explainability outputs
```

## Model Architecture

- **Backbone**: EfficientNet-B0 (pretrained on ImageNet)
- **Classifier**: Custom head with dropout regularization
- **Input size**: 224 x 224 pixels
- **Training**: 15 epochs with AdamW optimizer and learning rate scheduling

## Explainability

GradCAM (Gradient-weighted Class Activation Mapping) visualizations show which regions of the tissue image the model focuses on for classification decisions. This is crucial for:

- **Clinical trust**: Pathologists can verify the model attends to relevant morphological features
- **Model validation**: Ensuring predictions are based on biologically meaningful patterns
- **Deployment readiness**: Meeting interpretability requirements for clinical AI systems

## Clinical Applicability

This pipeline is designed with clinical deployment in mind:

1. **Explainability**: GradCAM visualizations enable pathologist verification
2. **High sensitivity**: 99.86% tumor recall minimizes missed diagnoses
3. **Scalability**: Lightweight EfficientNet-B0 suitable for deployment
4. **Transferability**: Architecture applicable to pediatric cancer H&E analysis

## Requirements

```
torch>=2.0.0
torchvision>=0.15.0
numpy>=1.21.0
pandas>=1.3.0
matplotlib>=3.4.0
seaborn>=0.11.0
scikit-learn>=1.0.0
opencv-python>=4.5.0
tqdm>=4.62.0
Pillow>=8.0.0
```

## References

1. Kather, J.N., et al. (2019). Predicting survival from colorectal cancer histology slides using deep learning. *PLOS Medicine*.
2. Tan, M. & Le, Q. (2019). EfficientNet: Rethinking Model Scaling for CNNs. *ICML*.
3. Selvaraju, R.R., et al. (2017). Grad-CAM: Visual Explanations from Deep Networks via Gradient-based Localization. *ICCV*.

## Author

**Joana Owusu-Appiah**  
MSc Medical Imaging and Applications (Erasmus Mundus)  
Email: owusuappiahjoana59@gmail.com  
[LinkedIn](https://linkedin.com/in/joana-owusu-appiah) | [GitHub](https://github.com/Joana-Mansa)

---

*This project demonstrates expertise in computational pathology and explainable AI for cancer diagnosis applications.*# HnE_tissue_classification
