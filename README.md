#Fake News Detection with IBM Granite (Capstone Project)

## Project Overview
Disinformation and fake news spread rapidly on social media and news platforms.  
This project aims to build an AI-powered pipeline that classifies news articles as REAL or FAKE, and provides human-readable explanations.  
We utilized the Fake and Real News Dataset from Kaggle, processed the data in Google Colab, and integrated IBM Granite (via Replicate API) to support classification and explanation.

---

## Raw Dataset
- Source: [Fake and Real News Dataset – Kaggle](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset)  
- Files used:  
  - `Fake.csv`  Fake news articles  
  - `True.csv`  Real news articles  

---

## Analysis Process
1. Data Loading > Import dataset (Fake.csv, True.csv) using `pandas`.  
2. Preprocessing > Handle corrupted rows, sample articles.  
3. Model Integration > Send news samples to IBM Granite 8B Instruct via `langchain_community.llms.Replicate`.  
4. Structured Output > Force Granite to reply in JSON format:  
   ```json
   {"label": "FAKE", "reason": "Explanation..."}
5. Parsing andf Evaluation > Compare Granite’s prediction vs dataset label, calculate simple accuracy.
6. Visualization > Bar chart of predictions vs ground truth.

## Insights and Findings
- Granite is able to return structured outputs (label, reason) consistently.
- However, accuracy vs Kaggle labels is low, because Granite is not specifically trained on fake news detection.
- Strength: Granite explains predictions in natural language (very useful for transparency).
- Weakness: Without fine-tuning or external verification, Granite tends to label many articles as REAL even if they are in Fake.csv.

## AI Support Explanation
- IBM Granite 3.3-8B Instruct (via Replicate API) was used as LLM.
- Role of AI in this project:
      - Classification: Assign label REAL or FAKE.
      - Explainability: Provide a short reason behind the classification.
- This shows how general-purpose LLMs can be integrated into a workflow with domain datasets.
