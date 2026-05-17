<div align="center">

# 🗣️ Dialogue Summarization with Fine-tuned T5

### Abstractive Text Summarization using Transformer Architecture

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-Transformers-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)](https://pytorch.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![Gradio](https://img.shields.io/badge/Gradio-FF7C00?style=for-the-badge&logo=gradio&logoColor=white)](https://gradio.app)

<br>

🚀 **[Live Demo on HuggingFace Spaces](https://huggingface.co/spaces/parmar-amit/text-summarizer)**

</div>

---

## 📌 Overview

This project fine-tunes **Google's T5-small** (Text-to-Text Transfer Transformer) on the **SAMSum dataset** — a large-scale corpus of messenger-style human conversations with abstractive summaries. The trained model accurately condenses multi-turn dialogues into concise, fluent summaries.

The system exposes a **FastAPI** REST endpoint and a **Gradio** web interface, making it accessible both programmatically and through a browser.

---

## 🎯 Problem Statement

Real-world conversational data — chat logs, meeting transcripts, customer support threads — is verbose and time-consuming to read. This project solves the challenge of **automatically extracting key information** from multi-turn dialogues using a fine-tuned sequence-to-sequence transformer.

---

## 🏗️ Architecture

```
Input Dialogue
      │
      ▼
┌─────────────────┐
│   T5Tokenizer   │  ← Tokenization + Padding (max 512 tokens)
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  T5-small Model │  ← Fine-tuned Encoder-Decoder Transformer
│  (Fine-tuned)   │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Beam Search    │  ← num_beams=4, max_length=150
│  Decoding       │
└────────┬────────┘
         │
         ▼
   Summary Output
```

---

## 📊 Dataset — SAMSum

| Split | Samples |
|:------|--------:|
| Train | 13,168 |
| Validation | 818 |
| Test | 819 |
| **Total** | **14,805** |

SAMSum contains linguistically diverse English conversations created by trained annotators, covering topics like daily life, work, relationships, and entertainment — closely mirroring real-world messaging patterns.

---

## ⚙️ Training Configuration

| Parameter | Value |
|:----------|:------|
| Base Model | `google/t5-small` |
| Task | Seq2Seq Summarization |
| Max Input Length | 512 tokens |
| Max Target Length | 150 tokens |
| Decoding Strategy | Beam Search |
| Number of Beams | 4 |
| Framework | HuggingFace Trainer API |
| Hardware | Google Colab (T4 GPU) |

---

## 🧪 Example

**Input Dialogue:**
```
Amanda: I baked cookies. Do you want some?
Jerry: Sure! I love cookies.
Amanda: Great! I'll bring you some tomorrow.
Jerry: Thanks Amanda, you're the best!
```

**Generated Summary:**
```
Amanda baked cookies and will bring Jerry some tomorrow.
```

---

## 🛠️ Tech Stack

<div align="center">

| Layer | Technology |
|:------|:-----------|
| 🤖 Model | T5-small (Fine-tuned) |
| 🔬 ML Framework | HuggingFace Transformers |
| 🔥 Deep Learning | PyTorch |
| ⚡ Backend API | FastAPI |
| 🎨 Frontend UI | Gradio |
| ☁️ Deployment | HuggingFace Spaces |
| 📊 Data | Pandas |
| 🐍 Language | Python 3.10+ |

</div>

---

## 📁 Project Structure

```
text-summarizer-t5-finetune/
│
├── app.py                      # FastAPI + Gradio application
├── requirements.txt            # Project dependencies
├── text_summarizer.ipynb       # Fine-tuning notebook (training pipeline)
└── README.md
```

> 📦 **Model weights** are hosted on HuggingFace Spaces (244MB):
> [`parmar-amit/text-summarizer`](https://huggingface.co/spaces/parmar-amit/text-summarizer)

---

## 🚀 Run Locally

**1. Clone the repository**
```bash
git clone https://github.com/paramramit305-a11y/text-summarizer-t5-finetune.git
cd text-summarizer-t5-finetune
```

**2. Install dependencies**
```bash
pip install -r requirements.txt
```

**3. Download model weights**

Download `saved_summary_model/` from [HuggingFace Spaces](https://huggingface.co/spaces/parmar-amit/text-summarizer/tree/main) and place it in the project root.

**4. Run the app**
```bash
python app.py
```

**5. API Usage**
```bash
curl -X POST "http://localhost:8000/summarize" \
     -H "Content-Type: application/json" \
     -d '{"dialogue": "Amanda: I baked cookies.\nJerry: Sure, I would love some!"}'
```

---

## 📡 API Reference

### `POST /summarize`

**Request Body:**
```json
{
  "dialogue": "string"
}
```

**Response:**
```json
{
  "summary": "string"
}
```

---

## 🔮 Future Improvements

- [ ] Fine-tune on larger T5 variant (T5-base / T5-large)
- [ ] Add ROUGE score evaluation
- [ ] Support multilingual summarization
- [ ] Integrate RAG for domain-specific summarization
- [ ] Deploy as REST API on AWS / GCP

---

## 📄 References

- [Attention Is All You Need — Vaswani et al. (2017)](https://arxiv.org/abs/1706.03762)
- [Exploring the Limits of Transfer Learning with T5 — Raffel et al. (2020)](https://arxiv.org/abs/1910.10683)
- [SAMSum Corpus — Gliwa et al. (2019)](https://arxiv.org/abs/1911.12237)

---

## 👤 Author

<div align="center">

**Parmar Amit**
*BSc IT (AIML) | Gokul Global University*

[![GitHub](https://img.shields.io/badge/GitHub-paramramit305--a11y-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/paramramit305-a11y)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Parmar%20Amit-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/parmar-amit-97941a377)
[![HuggingFace](https://img.shields.io/badge/HuggingFace-parmar--amit-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co/parmar-amit)

</div>

---

<div align="center">

⭐ If you find this project useful, please consider giving it a star!

</div>
