# 🌸 Iris Flower Species Classification

![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.x-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Notebook-Jupyter-F37626?logo=jupyter)
![License](https://img.shields.io/badge/License-MIT-green)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

> ** Supervised Machine Learning **  
> Multi-class flower species classification using KNN, Logistic Regression, and Naive Bayes.

<p align="center">
  <img src="assets/iris_species.png" width="700" alt="Iris flower species — Versicolor, Setosa, Virginica"/>
</p>

---

## 📌 The Problem

A botanical research centre manually identifies Iris flower species by measuring sepal and petal dimensions. This manual process is:

- **Time-consuming** — every sample requires a trained botanist to inspect
- **Error-prone** — human measurements and judgements introduce inconsistency
- **Not scalable** — cannot handle high-volume field studies or automated pipelines

The core challenge: *given only four physical measurements of a flower, can a machine reliably determine its species?*

---

## 💡 The Approach

Rather than jumping straight to the most complex model, this project follows a structured, comparative approach:

### Why compare three algorithms?

Each model brings a fundamentally different problem-solving strategy to the same task:

| Algorithm | How it solves the problem |
|---|---|
| **Logistic Regression** | Learns a linear decision boundary between classes — fast, interpretable, works well when classes are linearly separable |
| **K-Nearest Neighbours (KNN)** | Classifies by looking at the 5 most similar training samples — no learning phase, purely distance-based reasoning |
| **Naive Bayes** | Applies Bayes' theorem, assuming each feature contributes independently — probabilistic, excels on small datasets |

By running all three on the same data, we can understand *which reasoning style fits this problem best* — rather than blindly trusting a single model.

### Why train on only 50% of the data?

The Iris dataset is small (150 samples), balanced (50 per class), and clean — which makes any model look unrealistically good. To simulate a more real-world scenario where training data is limited:

- **Train set:** 50% of data (`test_size=0.5, random_state=42`)
- **Evaluation:** Predictions made on the **full 100%** of data

This deliberately stresses the models and gives a fairer picture of generalisation ability.

### Feature Engineering

The `Species` column (originally string labels) is encoded to integers `0, 1, 2` using `LabelEncoder` before training — a necessary preprocessing step since sklearn models require numeric targets.

---

## 📊 Dataset Description

The classic **Iris Dataset** — 150 samples, 3 perfectly balanced classes, 4 numeric features.

| Feature | Description |
|---|---|
| `SepalLengthCm` | Length of the sepal in centimetres |
| `SepalWidthCm` | Width of the sepal in centimetres |
| `PetalLengthCm` | Length of the petal in centimetres |
| `PetalWidthCm` | Width of the petal in centimetres |
| **`Species`** *(Target)* | `Iris-setosa`, `Iris-versicolor`, `Iris-virginica` |

> **Note:** Despite being a benchmark dataset, this project is designed to reflect realistic constraints — limited training data and evaluation against the full population — so results are deliberately imperfect.

---

## 🔬 Full Pipeline

```
Raw CSV
  └── Load with pandas
        └── Encode target labels (LabelEncoder)
              └── Train/Test Split (50% train, 50% test)
                    ├── Logistic Regression  (max_iter=1000)
                    ├── KNN                  (n_neighbors=5)
                    └── Naive Bayes          (GaussianNB)
                          └── Evaluate on full dataset (X, y)
                                ├── Accuracy Score
                                ├── Confusion Matrix
                                └── Classification Report
```

---

## ⚙️ Setup & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/iris-flower-classification.git
cd iris-flower-classification
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the Notebook
```bash
jupyter notebook iris_flower.ipynb
```

> Make sure `iris.csv` is in the same directory as the notebook.

---

## 📈 Results Summary

All three models were evaluated using Accuracy, Confusion Matrix, and a full Classification Report (Precision, Recall, F1-Score per class).

| Model | Strength in this context |
|---|---|
| Logistic Regression | Stable linear boundaries between well-separated species |
| KNN (k=5) | Strong on local structure — petal dimensions cluster tightly |
| Naive Bayes | Fast and competitive even with only 75 training samples |

> Check the notebook output for exact metric values. The intentional 50/50 split ensures scores reflect genuine generalisation, not overfitting to a tiny test set.

---

## 🧠 Key Takeaways

- A **comparative approach** reveals which algorithm's reasoning style fits the problem — not just which number is highest
- **Data quality and balance** matter more than model complexity; Iris is clean but real data rarely is
- **Evaluation strategy** (how you split, what you measure) shapes results as much as the model itself

---

## 🛠️ Tech Stack

- **Python 3.8+**
- **pandas** — data loading and inspection
- **scikit-learn** — preprocessing, models, evaluation metrics
- **Jupyter Notebook** — interactive development

---

## 👤 Author

**Afzal**  
BTech — Computer Science  
*Supervised ML project*

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).
