---

# Hindi Formality Style Transfer

**Bidirectional Text Style Transfer using mT5 and IndicBART**

## 🧠 Overview

This project addresses the unique linguistic challenge of **formality style transfer in Hindi**—a task that involves converting informal sentences to formal ones and vice versa, without losing the original meaning. We propose a **bidirectional text style transfer model** trained on a custom parallel dataset using **mT5** and **IndicBART**.

> 🔄 Both directions — *Formal ➡️ Informal* and *Informal ➡️ Formal* — are supported.

The model has demonstrated **better performance** than existing baselines like GPT-2, mBART, and IndicGPT in terms of **BLEU score**, **BERTScore**, and **Perplexity**.

---

## 🧾 Key Features

* ✨ **Bidirectional transfer**: Formal to informal & informal to formal
* 🤖 Fine-tuned **mT5-small** and **AI4Bharat IndicBART** models
* 📊 Evaluated with **BLEU**, **BERTScore**, and **Perplexity**
* 🔄 Ensemble inference combining both models for improved results
* 🗣️ Focused on Hindi — a complex, culturally rich, and low-resource language

---
 
## 🏗️ Models Used
🔹 **mT5 (Multilingual T5)**
* Pretrained on mC4 corpus

* Encoder-decoder Transformer

* Effective for generalization and semantic preservation

🔹 **IndicBART**
* Pretrained on Indic corpora by AI4Bharat

* Strong with morphological and stylistic nuance

* Superior fluency and contextual accuracy

## 📁 Dataset

* **Size**: 50,000 sentence pairs
* **Format**: Parallel corpus of formal and informal Hindi sentences
* **Source**: Created manually and scraped from publicly available Hindi content
* **Usage**: Used for bidirectional training of both models

## 🧠 Methodology

### Model Architecture

* **Seq2Seq Transformers**: Both mT5 and IndicBART are encoder-decoder models.
* **Input Format**: `"formal: <sentence>"` or `"informal: <sentence>"`
* **Output Format**: Translated sentence in the desired style

### Training Details

* **Framework**: Hugging Face Transformers
* **Tokenizer**: SentencePiece-based tokenizers for both models
* **Training Epochs**: 5
* **Batch Size**: 16
* **Optimizer**: AdamW
* **Learning Rate Scheduler**: Linear warmup with decay

### Inference Strategy

* **Beam Search**: Used during inference to enhance fluency
* **Ensemble Inference**: Combines predictions from mT5 and IndicBART to improve output quality

### Evaluation Metrics

* **BLEU Score**: 23.0
* **BERTScore**: Precision 0.86, Recall 0.85, F1 0.85
* **Perplexity**: 8.25

## 📊 Results

| Model         | BLEU  | BERTScore F1 | Perplexity |
| ------------- | ----- | ------------ | ---------- |
| **mT5**       | 23.31 | 0.85         | 8.25       |
| **IndicBART** | 17.84 | 0.81         | 5.36       |
| **Ensemble**  | 21.65 | 0.84         | 6.20       |
| GPT-2         | 0.26  | 0.60         | 3.13       |
| IndicGPT      | 20.01 | 0.63         | 41.77      |
| mBART         | 8.91  | 0.77         | 15.07      |


## 🔧 Installation

```bash
git clone https://github.com/Varalakshmikannuru/hindi-formality-transfer.git
cd hindi-formality-transfer
pip install -r requirements.txt
```

## 🏃‍♀️ Running the Project

### Training

```bash
python train.py --model mt5 --epochs 5 --batch_size 16
python train.py --model indicbart --epochs 5 --batch_size 16
```

### Inference

```bash
python inference.py --input "formal: क्या आप ठीक हैं?" --model ensemble
```

## 🧪 Folder Structure

```
hindi-formality-transfer/
│
├── data/                     # Training and evaluation datasets
├── models/                   # Saved model checkpoints
├── src/
│   ├── train.py              # Training script
│   ├── inference.py          # Inference script
│   ├── utils.py              # Utility functions
│
├── evaluation/
│   ├── metrics.py            # Evaluation metrics
│   └── results/              # Result outputs
│
├── README.md
└── requirements.txt
```

## ✍️ Author

**Varalakshmi Kannuru**
Final Year B.Tech Student | AI/ML Enthusiast
📫 [Varalakshmikannuru](https://github.com/Varalakshmikannuru)
