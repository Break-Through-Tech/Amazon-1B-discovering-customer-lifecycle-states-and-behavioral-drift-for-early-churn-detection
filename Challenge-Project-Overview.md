

# Discovering Customer Lifecycle States and Behavioral Drift for Early Churn Detection Using Explainable AI and Generative AI

**Company / Org:** Amazon.com  
**Challenge Advisor:** Aryyama Kumar Jana, janaaryyama@gmail.com   
**AI Studio Coach:** Ayush Amberkar, ayush.amberkar@breakthroughtech.org  
**Program:** Break Through Tech AI Studio - Fall 2026  

---

## About the Challenge Advisor and Project Context
Aryyama Kumar Jana is a Software Development Engineer at Amazon.com. This Challenge Project is designed by the Challenge Advisor in a personal volunteer capacity and is not submitted on behalf of Amazon or any employer. The project is inspired by broad, industry-wide problems in customer analytics and retention, but it will use only publicly available datasets and open-source methods. No Amazon confidential data, internal systems, proprietary workflows, customer information, or non-public business context will be used.

---

## 🎯 The Challenge
### Project Summary
In this project, you will use public e-commerce customer transaction and event-behavior data and machine learning techniques including time-series feature engineering, clustering, classification, behavioral drift detection, and explainable AI to build an early-warning system that detects meaningful customer behavior changes before churn occurs. The system will also generate grounded, plain-English risk summaries using deterministic template-based generation from model outputs and feature explanations. This will help organizations address the business problem of identifying at-risk customers earlier, improving retention strategies, and reducing revenue loss from preventable customer churn.

### Churn Definition and Modeling Boundary
For the primary Online Retail II dataset, churn will be defined using a forward-looking inactivity window. A customer-month will be labeled as churn-risk positive if the customer makes no purchase in the next 90 days after that month. Features for each customer-month must only use information available up to that point in time, so the model does not use future information when making predictions. Customer-months too close to the end of the dataset, where a full 90-day future observation window is not available, should be excluded from supervised model training.

### Success Criteria
Success will be measured using both predictive performance and early-warning usefulness. The team will evaluate churn prediction using precision, recall, F1 score, ROC-AUC, and PR-AUC. Since this project focuses on early detection, the team will also measure early-warning horizon, defined as how many days or weeks before churn the system can identify meaningful behavioral drift or a transition into an at-risk lifecycle state. The lifecycle-state approach will be evaluated by whether the discovered customer states are interpretable and whether transitions into at-risk states improve early churn detection compared with standard churn models. The explanation component will be evaluated based on whether generated risk summaries are accurate, clear, and grounded in actual model features, SHAP values, or drift metrics. A successful December outcome would be a reproducible Python/Google Colab pipeline that ingests public e-commerce data, creates customer-time features, applies a standardized churn definition, trains baseline models, discovers customer lifecycle states, measures early-warning performance, and produces explainable customer-risk summaries.

### Stretch Goals
If the team progresses quickly, stretch goals could include building customer behavior embeddings using autoencoders or sequence models, comparing lifecycle-state discovery across Online Retail II and RetailRocket, adding a lightweight dashboard using Streamlit or Gradio, testing a small local open-source language model for narrative summaries, or developing simple retention recommendation logic based on the type of behavioral drift detected. GenAI should be treated as optional or stretch; the required project should work with deterministic, template-based summaries without paid APIs.

### Project Milestones
Use these milestones to guide your work. Your team will create a GitHub Projects board to track tasks within each milestone.
| Month | Milestone | Key Activities |
|-------|-----------|----------------|
| **September** | Data Pipeline and Churn Definition | The team will focus on understanding the business problem, exploring the public datasets, and building the foundational data pipeline. Fellows will use Online Retail II as the primary dataset, combine both Excel sheets, clean transactions, handle missing customer IDs, remove or separately handle canceled invoices, convert timestamps, and create a customer-month feature table. The team will standardize the churn definition using a 90-day forward-looking inactivity window and ensure features only use information available before the prediction point. By the end of September, the team should have a reproducible Google Colab notebook that converts raw public data into modeling-ready customer-time features. |
| **October** | Baseline Modeling and Behavioral Drift | The team will train baseline churn prediction models such as Logistic Regression, Random Forest, and XGBoost, then evaluate them using precision, recall, F1 score, ROC-AUC, and PR-AUC. The team will also create behavioral drift features that compare a customer’s current behavior with previous behavior, such as changes in purchase frequency, revenue, unique items, average order value, and days since last purchase. By the end of October, the team should have working baseline churn models and an initial behavioral drift scoring approach. |
| **November** | Lifecycle States, Explainability, and Final Demo | TThe team will apply clustering methods such as K-Means, Gaussian Mixture Models, or HDBSCAN to discover latent customer lifecycle states, such as active buyer, occasional buyer, declining customer, and at-risk customer. The team will compare the lifecycle-state and behavioral-drift approach against baseline churn models, measure early-warning horizon, add explainability using SHAP or feature attribution, and generate deterministic template-based customer-risk summaries. By the end of November, the team should have a final end-to-end demo, evaluation results, and clear explanations of which behavioral changes indicate future churn risk. |

> **Note for the team:** Please create a GitHub Projects board in this repository to break these milestones into weekly tasks. Go to the **Projects** tab → **New project** → Choose **Board** → Add columns for each month.

---

## 📊 Dataset
**Name and Source:**
- Primary dataset: Online Retail II from the UCI Machine Learning Repository
- Optional secondary dataset: RetailRocket E-commerce Dataset from Kaggle

**Location:**
- https://archive.ics.uci.edu/dataset/502/online%2Bretail%2Bii
- https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset

### Key Details
- Online Retail II will be the primary dataset for feature engineering, churn-label construction, modeling, lifecycle-state discovery, and evaluation.
- RetailRocket may be used as an optional secondary validation dataset if time allows. Because RetailRocket is event-based while Online Retail II is transaction-based, students will map both datasets into a common customer-time behavioral representation rather than expecting the raw schemas to match.
- Preprocessing must account for temporal sequencing, handle high-cardinality categorical variables, and normalize transactional volume across different customer segments.
- The team will define churn using a standardized forward-looking inactivity window. For the primary Online Retail II dataset, a customer-month will be labeled as churn-risk positive if the customer makes no purchase in the next 90 days after that month.
- The project will use only publicly available datasets. No Amazon data, employer data, confidential data, proprietary workflows, or non-public business context will be used.
- Required preprocessing includes timestamp conversion, cancellation handling, missing customer filtering, customer-time window creation, churn-label construction, behavioral drift feature engineering, and leakage prevention.

---

## 🛠️ Suggested Approach

**ML Problem Type:** Classification, Clustering, and NLP (Generative AI)  

**Recommended Libraries:**
- pandas and NumPy for data cleaning and feature engineering
- scikit-learn for preprocessing, baseline models, clustering, and evaluation
- XGBoost or LightGBM for stronger churn classification baselines
- SHAP for explainability
- matplotlib or plotly for visualization
- optional: hdbscan for lifecycle-state discovery
- optional: Streamlit or Gradio for a lightweight demo
- optional: Hugging Face Transformers only if the team has time and can run a small local model in Colab

**Evaluation Metrics:**
- Classification: precision, recall, F1 score, ROC-AUC, PR-AUC
- Early detection: average early-warning horizon in days or weeks before churn
- Clustering: silhouette score plus qualitative interpretability of lifecycle states
- Explainability: whether generated risk summaries are grounded in actual model features, SHAP values, or behavioral drift metrics

---

## 📚 Resources to Get Started

The following resources will help your team understand the problem space and potential technical approaches for this project:

**Background Reading:**
- Online Retail II dataset: https://archive.ics.uci.edu/dataset/502/online%2Bretail%2Bii
- RetailRocket dataset: https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset
- Customer churn overview: https://en.wikipedia.org/wiki/Customer_attrition

**Technical Tutorials:**
- pandas groupby: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html
- scikit-learn model evaluation: https://scikit-learn.org/stable/modules/model_evaluation.html
- scikit-learn clustering: https://scikit-learn.org/stable/modules/clustering.html
- SHAP documentation: https://shap.readthedocs.io/

**Code Examples:**
- Starter notebook should include reading Online Retail II Excel sheets, cleaning transactions, creating customer-month features, defining the 90-day churn label, training a baseline model, and evaluating results.
- Students are encouraged to keep the first version simple and reproducible before adding lifecycle-state discovery or narrative summaries.

*Feel free to explore beyond these, and share anything interesting you find with me!*

---

## 🤝 How We'll Work Together

**Official check-ins:** During our biweekly 45-minute AI Studio Lab Section meeting block (2nd and 4th week of every month)

 **Other ways to reach out to me with questions:** 
* Use the team’s Break Through Tech communication channel for project questions.
* For longer technical questions, students may email me and copy the full team and AI Studio Coach.
* I will aim to respond within a week.
* For urgent program logistics, please contact the AI Studio Coach.

**Recommended free coding / collaboration tools**
* Google Colab
* GitHub
* GitHub Projects
* pandas, scikit-learn, XGBoost/LightGBM, SHAP
* optional: Streamlit or Gradio for demo UI

---

## 🚀 Getting Started

1. **Review this overview document** and note any questions for our first meeting
2. **Begin reviewing the dataset** using the link above
3. **Read the GitHub Projects documentation** [here](https://docs.github.com/en/issues/planning-and-tracking-with-projects/learning-about-projects/about-projects)

I’m excited to work with you!

---

## ❓ Questions?

Please bring any questions to our first meeting during the week of August 24th (Break Through Tech’s Bridge to Studio - Session C). 
