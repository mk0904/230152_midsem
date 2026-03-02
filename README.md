# Sentiment Analysis of Twitter Data
### Advanced Machine Learning — Mid-Semester Examination (Part A)

> **Paper:** Sentiment Analysis of Twitter Data  
> **Authors:** Apoorv Agarwal, Boyi Xie, Ilia Vovsha, Owen Rambow, Rebecca Passonneau  
> **Venue:** Workshop on Language in Social Media (LSM 2011) — Association for Computational Linguistics  
> **Year:** 2011  
> **Link:** https://aclanthology.org/W11-0705.pdf

---

## 📌 What is this paper about?

This paper tackles the problem of **sentiment classification of tweets** — automatically determining whether a tweet is **positive**, **negative**, or **neutral**.

The authors experiment with three types of models:
- **Unigram model** — baseline using raw word frequencies (~10,000 features)
- **Feature-based SVM** — uses only 100 hand-crafted linguistic features
- **Tree Kernel SVM** — uses a custom tree representation of tweets, no manual feature engineering needed

The key insight is that combining the **prior polarity of a word** (is it generally positive/negative?) with its **Part-of-Speech (POS) tag** (how is it being used?) produces the most powerful features — outperforming even the unigram baseline that uses 100x more features.

---

## 🧠 Primary Method

**Support Vector Machine (SVM)**  
- Binary classification: Positive vs Negative  
- 3-class classification: Positive vs Negative vs Neutral  
- Feature-based SVM with POS-specific prior polarity features  
- Tree Kernel SVM using syntactic tweet representation  

---

## 📂 Repository Structure

```
<rollnumber>-midsem/
│
├── README.md                  # This file
├── llm_usage_partA.json       # Complete LLM usage disclosure (mandatory)
```

---

## 📊 Dataset

The paper uses **11,875 manually annotated tweets** collected from a real-time Twitter stream.

- Tweets labeled as: Positive / Negative / Neutral / Junk
- After removing junk: **8,753 tweets**
- Balanced subset used for experiments: **5,127 tweets** (1,709 per class)
- Data collected via real-time streaming — no query bias
- **Publicly available** (contact first author as per paper's Acknowledgments)

A suitable substitute for reproduction: the [Sentiment140 dataset](http://www.sentiment140.com/) or the [NLTK Twitter corpus](https://www.nltk.org/) — both freely downloadable.

---

## ⚙️ Reproducibility

| Factor | Status |
|---|---|
| Dataset availability | ✅ Publicly available / substitute exists |
| Compute requirement | ✅ CPU-only, runs on a standard laptop |
| Libraries needed | ✅ scikit-learn, NLTK, numpy |
| Implementation complexity | ✅ Student-level reproducible |
| Special access required | ❌ None |

### Minimal reproduction steps:
```python
# Install dependencies
pip install scikit-learn nltk numpy

# Core pipeline
from sklearn.svm import SVC
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.pipeline import Pipeline

# Load dataset (e.g. Sentiment140 as substitute)
# Preprocess: remove URLs, expand acronyms, replace emoticons
# Extract features: unigrams + POS prior polarity
# Train SVM and evaluate on 5-fold cross validation
```

---

## 🔑 Key Contributions

1. **POS-specific prior polarity features** — combining sentiment polarity of a word with how it's grammatically used. e.g., "great" as an adjective vs "great" in sarcasm.
2. **Tree kernel model** — represents a tweet as a syntactic tree and uses a kernel function to measure similarity — no manual feature engineering needed.
3. **New resources** — emoticon dictionary (170 emoticons with polarity labels) and acronym dictionary (5,184 entries).
4. **Unbiased dataset** — tweets collected from real-time stream, not query-based, so no topic bias.

---

## 📉 Limitations & Failure Cases

- **Sarcasm and irony** — POS-polarity features fail when sentiment is expressed indirectly
- **Informal language** — acronyms, misspellings, and slang not in the dictionary are missed
- **Class imbalance** — original dataset is heavily unbalanced; stratified sampling was needed
- **Domain specificity** — model trained on general tweets may not generalize to domain-specific tweets (e.g. finance, healthcare)
- **Short text** — 140-character limit means very little context for the classifier

---

## 📝 Why This Paper Was Selected

This paper was selected because it applies a well-understood classical ML method (SVM) to a real-world, relatable problem — detecting sentiment in tweets. The paper is short (8 pages), clearly written, and uses a publicly available dataset. The experiments are feasible on a standard laptop without any GPU or special hardware. The feature engineering approach (POS + prior polarity) is intuitive enough to understand and explain as a 3rd year undergrad, while still being academically rigorous.

---

## 🛠️ LLM Usage Disclosure

Full disclosure of all LLM tools used during Part A is available in [`llm_usage_partA.json`](./llm_usage_partA.json).

Tools used: **Perplexity AI** (paper search & selection) and **Claude by Anthropic** (form filling & JSON generation).

---

## 👤 Student Details

| Field | Value |
|---|---|
| Name | YOUR_FULL_NAME |
| Roll Number | YOUR_ROLL_NUMBER |
| Course | Advanced Machine Learning |
| Exam | Mid-Semester Examination — Part A |
| Submission Date | 2026-03-02 |

---

*This repository is part of the Advanced Machine Learning Mid-Semester Examination submission at Rishihood University.*
