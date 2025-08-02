# 🔐 Deep Learning-Based XSS Detection

This project develops a **deep learning-based system for detecting Cross-Site Scripting (XSS) attacks**, utilizing **web scraping**, **ASCII/token-based preprocessing**, and models such as **CNN** and **CNN+LSTM**.

> Developed as part of the B.Tech Major Project at Tezpur University by [Anubhav Binit](https://github.com/your-username) and Hirok Jyoti Nath, under the guidance of Dr. Dhruba K Bhattacharyya.

---

## 🧠 Project Objective

To create a robust system that:
- Builds a comprehensive dataset of benign and malicious JavaScript snippets.
- Employs deep learning to detect XSS vulnerabilities.
- Compares preprocessing strategies (ASCII, tokenization) and model architectures.

---

## 📦 Dataset

- **Malicious Scripts Source:** [XSSed.com](http://xssed.com)
- **Benign Scripts Source:** [web.archive.org](https://web.archive.org)
- **Total Samples:** 17,515  
  - Malicious: 9,780  
  - Benign: 8,880

Each sample includes:
- `script`: Extracted JavaScript code
- `label`: 1 (malicious) or 0 (benign)

---

## ⚙️ Preprocessing Techniques

### 1. ASCII Conversion
- Converts characters into 100x100 normalized arrays.
- Applies noise filtering and custom handling for edge characters.

### 2. Tokenization
- Parses JavaScript using `esprima`.
- Performs minification and cleaning (removes whitespace, comments, redundant semicolons).

### 3. Word2Vec
- Generates word embeddings from tokenized scripts to capture semantic context.

---

## 🏗️ Model Architectures

### 🔹 CNN (Character & Token-based)
- Uses multiple Conv2D/1D layers with max pooling.
- Includes dense layers with a sigmoid output for binary classification.

### 🔹 CNN + LSTM (Hybrid)
- Employs Conv1D layers for feature extraction.
- Uses LSTM layers to capture temporal dependencies.
- Concludes with a sigmoid layer for binary classification.

---

## 📊 Evaluation Metrics

- **Accuracy**
- **Precision**
- **Recall**
- **F1-Score**
- **Confusion Matrix**
- **ROC Curves**

### 📈 Results Summary

| Model            | Accuracy | Precision | Recall |
|------------------|----------|-----------|--------|
| CNN (ASCII)      | 0.75     | 0.76      | 0.83   |
| CNN+LSTM (ASCII) | 0.76     | 0.84      | 0.65   |
| CNN (Tokens)     | 0.72     | 0.77      | 0.74   |
| CNN+LSTM (Tokens)| 0.78     | 0.73      | 0.76   |


<img width="936" height="649" alt="chart" src="https://github.com/user-attachments/assets/0190fbd5-8b80-43bc-ada9-57079ca24856" />


---

## 🔍 Folder Structure

```
├── data/
│   ├── XSS.csv
│   ├── benign.csv
│   └── features.ipynb
├── model/
│   ├── cnn_model.ipynb
│   ├── cnn_lstm_model.ipynb
│   └── model_utils.py
├── Output.csv
├── README.md
├── .gitignore
└── venv/ (ignored)
```

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/xss-detector.git
   cd xss-detector
   ```

2. Install dependencies:
   ```bash
   python -m venv venv
   source venv/bin/activate  # or venv\Scripts\activate on Windows
   pip install -r requirements.txt
   ```

3. Train the model:
   ```bash
   python train_model.py
   ```

4. Evaluate on test data:
   ```bash
   python evaluate_model.py
   ```

