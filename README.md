# Amazon Product Review Analytics  
### Synthetic Data Generation | Sentiment Analysis | Recommendation Systems  
**Master of Data Analytics – Predictive Analytics Project (DAMO-510-6)**  
Team Members: Sridevi Pemmasani · Catherine Calantoc · Jayasri Katragadda ·   Mounika Ravella

---

## 📌 Project Overview  
This project analyzes Amazon product reviews using advanced data analytics and machine learning techniques.  
We address three core modules from our course:

1. **Synthetic Data Generation** (500,000+ records)  
2. **Sentiment Analysis** (Traditional NLP + Transformer Models)  
3. **Recommendation Systems** (Collaborative Filtering + Content-Based)  

Since Databricks Community Edition has limited compute, we use a hybrid architecture:  
- **Databricks** for Spark processing, ALS recommender, and synthetic data generation  
- **Google Colab (GPU)** for BERT/DistilBERT sentiment model training

---

## 🗂 Repository Structure  


---

## 📊 Dataset Summary  
We start with a real Amazon Review dataset containing:

- **1,400 customer reviews**
- Product attributes  
- Ratings  
- Review titles & text  
- Verified purchase flag  
- Helpful votes  

This dataset forms the basis for generating **500,000 synthetic reviews** using SDV + CTGAN + LLM-assisted text generation.

---

## 🧪 Methodology  

### 1️⃣ **Synthetic Data Generation**
Techniques used:
- **SDV – CTGAN** (learn data distribution)
- **Faker** (names, timestamps, locations)
- **GPT-generated synthetic review text** for realism
- Statistical fidelity metrics

Output:
- **500,000 highly realistic user–product interactions**

---

### 2️⃣ **Sentiment Analysis**
We implemented both classical and deep learning approaches:

#### ✔ Baseline Models  
- VADER  
- TextBlob  
- TF-IDF + Logistic Regression  
- TF-IDF + Linear SVM  

#### ✔ Transformer Model (Google Colab GPU)  
- DistilBERT fine-tuned on synthetic + real review text  
- Achieved high accuracy and strong generalization  
- Exported model → used in Databricks for inference

---

### 3️⃣ **Recommendation Systems**
Two recommendation pipelines were built:

#### ✔ Spark ALS (Collaborative Filtering)
- Trained in Databricks using synthetic user–product interactions  
- Generates personalized top-N product recommendations  

#### ✔ Content-Based Filtering
- SentenceTransformer embeddings for product descriptions  
- Cosine similarity matrix  
- Hybrid recommendations combining text + ratings

---

## 🏗 System Architecture  

### **Hybrid Cloud Workflow (Databricks + Google Colab)**

Real Dataset → Databricks → Synthetic Data (500k) → Databricks
↓
(Export small subset)
↓
Google Colab (GPU)
→ DistilBERT Training → Model Export
↓
Databricks (Inference + Pipeline)


---

## 🚀 How to Run This Project

### **1. Clone Repository**
```bash
git clone https://github.com/<your-team>/amazon-review-analytics.git
cd amazon-review-analytics
