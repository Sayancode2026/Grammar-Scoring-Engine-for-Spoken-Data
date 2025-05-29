
# 🎓 Grammar Scoring Engine for Spoken English

## 📝 Overview

This project aims to develop a **Grammar Scoring Engine** that automatically evaluates spoken English audio samples and outputs a **continuous grammar score** between **0 and 5**. The model should be able to interpret the speaker's grammatical competence based on the structure and syntax of their speech.

---

## 📅 Competition Timeline

| Phase        | Date           |
|--------------|----------------|
| Start Date   | April 4, 2025  |
| End Date     | May 4, 2025    |

---

## 🧾 Competition Link

🔗 [SHL Intern Hiring Assessment – Grammar Scoring Engine](https://www.kaggle.com/competitions/shl-intern-hiring-assessment/overview)

---

## 📁 Dataset Description

### 🔊 Audio Files
- Format: `.wav`
- Length: Each file is **45–60 seconds**

### 📊 CSV Files
| File | Description |
|------|-------------|
| `train.csv` | Contains audio filenames and grammar scores |
| `test.csv` | Contains audio filenames (labels are randomized) |
| `sample_submission.csv` | Template for valid submission format |

---

## 🎯 Grammar Score Rubric (Likert Scale 1–5)

| Score | Description |
|-------|-------------|
| 1 | Limited control over sentence structure; struggles with grammar; uses memorized patterns |
| 2 | Uses simple structures with **frequent errors**; often **incomplete** sentences |
| 3 | Moderate grasp of sentence structure but **some grammatical or syntactical issues** |
| 4 | Good grammar control; **occasional minor errors** that do not affect comprehension |
| 5 | High grammatical accuracy; handles **complex grammar** with **self-correction** |

---

## 🔧 Project Pipeline

### 1. **Preprocessing**
- **Audio Loading**: Resampled at 16 kHz using `librosa`
- **Feature Extraction**:
  - MFCCs (20 coefficients)
  - Delta & Delta-Delta MFCCs
  - Spectral features: Centroid, Bandwidth, Roll-off
  - Zero Crossing Rate

### 2. **Feature Aggregation**
- Aggregated statistics: **mean, std, min, max**
- Produced a fixed-size vector per audio clip

### 3. **Modeling**
- Tried multiple models:
  - Support Vector Regressor (SVR)
  - Random Forest Regressor
  - XGBoost Regressor
- **Best Model**: **SVR**, chosen for its generalization and performance

### 4. **Evaluation**
- Primary Metric: **Pearson Correlation**
- Additional Metrics: **RMSE** (required), MAE
- **Visualizations**: Plots showing predicted vs actual scores, feature importance, and error distribution

---

## 📈 Final Model Performance (on Training Data)

| Metric | Score |
|--------|-------|
| ✅ RMSE (Required) | `0.9079` |
| ✅ MAE | `0.7082` |
| ✅ Pearson Correlation | `0.6406` |

> ✔️ RMSE is included in the final notebook as **compulsory evaluation**.

---

## 📑 Submission Requirements

- ✅ A **Jupyter Notebook** with:
  - Clean, **well-commented code**
  - All **preprocessing steps** clearly explained
  - Model architecture and evaluation process
  - **RMSE score on training data**
  - Visualizations to support interpretability

---

## 🧠 Evaluation Criteria

| Category        | Description |
|----------------|-------------|
| ✔️ Correctness   | Does the model behave as expected and follow the rubric? |
| ✔️ Code Quality | Clean, modular, and well-documented code |
| ✔️ Performance  | Model accuracy and correlation with human ratings |
| ✔️ Interpretability | Are the results explained with **plots and analysis**? |

---



---

## 🧪 Potential Improvements

- Add ASR (Speech-to-Text) for transcript-based linguistic analysis
- Combine acoustic + textual features for multimodal modeling
- Use deep learning (e.g., CNNs on spectrograms or pretrained Wav2Vec)

---

## 🛠️ Requirements

```bash
pip install librosa scikit-learn pandas matplotlib xgboost
```

---

## 👤 Author

**Sayan Bardhan**  
Email: [sayanbardhan2023@gmail.com](mailto:sayanbardhan2023@gmail.com)

---

## 📜 License

This project is released under the [MIT License](LICENSE).
