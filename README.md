# A Large-Scale Multiclass Dataset and Comparative Analysis for Bangla Cyberbullying Detection

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3+-blue.svg)](https://www.python.org/downloads/)

This is the official repository for the paper **"A Large-Scale Multiclass Dataset and Comparative Analysis for Bangla Cyberbullying Detection"**. 

This repository contains the data preprocessing scripts, model training codes, and evaluation pipelines for detecting multiclass cyberbullying in Bengali social media posts and comments.

## 📌 Overview

Detecting cyberbullying in low-resource languages like Bangla is challenging due to limited training data, inconsistent spelling, and non-standard linguistic structures. This project introduces a new, large-scale multi-class dataset containing **104,218** social media texts manually categorized into five classes. 

We benchmarked three families of models on this dataset:
1. **Classical Machine Learning:** SVM, Naive Bayes (with TF-IDF)
2. **Deep Learning:** CNN, LSTM, GRU (with Word2Vec and FastText embeddings)
3. **Pre-trained Transformers:** BanglaBERT, MuRIL, XLM-RoBERTa

**Key Findings:** 
* Contextual language models (Transformers) significantly outperform non-contextual models.
* **BanglaBERT** achieves the state-of-the-art accuracy of **87.76%**.
* For deep learning architectures, **FastText** embeddings consistently outperform Word2Vec, demonstrating superior capability in handling the morphological richness and noisy spellings of informal Bangla.

## 📊 Dataset

The dataset was constructed by cleaning, consolidating, and re-annotating two publicly available datasets (a Kaggle dataset and Jahin et al., 2025). 

*(Note: The full consolidated dataset is available upon request to the primary author. A sample is provided in the `data/` folder).*

### Class Distribution
| Class | Sample Count | Percentage (%) |
| :--- | :---: | :---: |
| Not Bully | 36,762 | 35.27% |
| Religious | 20,381 | 19.56% |
| Troll | 19,574 | 18.81% |
| Sexual | 16,401 | 15.72% |
| Threat | 11,100 | 10.64% |
| **Total** | **104,218** | **100%** |

## 🚀 Methodology

The unified framework for this study processes the raw Bengali text through a custom regular expression-based cleaning pipeline (removing Latin characters, digits, and emojis, keeping only valid Bengali Unicode). 

Features are extracted using:
* **TF-IDF** (for ML models)
* **Word2Vec / FastText** (for DL models)
* **Subword Tokenizers** (for Transformer models)

## 🏆 Results

All models were evaluated on an identical held-out test set using Accuracy, Macro-F1, and Micro-AUC.

### 1. Transformer Models (Best Performers)
| Model | Accuracy (%) | Macro-F1 | Micro-AUC |
| :--- | :---: | :---: | :---: |
| **BanglaBERT** | **87.76** | **0.8692** | **0.96** |
| MuRIL | 85.13 | 0.8453 | 0.95 |
| XLM-RoBERTa | 83.77 | 0.8294 | 0.95 |

### 2. Deep Learning Models
| Model | Embedding | Accuracy (%) | Macro-F1 | Micro-AUC |
| :--- | :--- | :---: | :---: | :---: |
| **LSTM** | **FastText** | **83.84** | **0.8461** | **0.97** |
| GRU | FastText | 83.59 | 0.8400 | 0.97 |
| CNN | FastText | 83.32 | 0.8354 | 0.97 |
| GRU | Word2Vec | 78.78 | 0.8069 | 0.96 |

### 3. Classical Machine Learning
| Model | Accuracy (%) | Macro-F1 | Micro-AUC |
| :--- | :---: | :---: | :---: |
| **SVM (TF-IDF)** | **83.49** | **0.8348** | **0.958** |
| Naive Bayes (TF-IDF)| 77.27 | 0.7275 | 0.944 |

## ⚙️ Setup & Installation

Clone the repository and install the dependencies:

```bash
git clone https://github.com/yourusername/bangla-cyberbullying-detection.git
cd bangla-cyberbullying-detection
pip install -r requirements.txt
```

## 📖 Citation

If you use our dataset or methodology in your research, please cite our paper:

```bibtex
@inproceedings{bangla_cyberbullying_2026,
  title={A Large-Scale Multiclass Dataset and Comparative Analysis for Bangla Cyberbullying Detection},
  author={[Author Names]},
  booktitle={IEEE [Conference Name]},
  year={2026}
}
```

## 📜 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
