# Discovering Customer Lifecycle States and Behavioral Drift for Early Churn Detection Using Explainable AI and Generative AI

> Fall 2026  

---

### 👥 **Team Members**

| Name             | GitHub Handle | Contribution                                                             |
|------------------|---------------|--------------------------------------------------------------------------|
| Cristian Pena | @cpena-estrada | Data Engineering, Backend, Pandas |
| Addrita Biswas | @aaayushhhh | Web Design/Web Development, AI/ML |
| Ashley Cruz Lopez | @ashleyycruz | Python/Full Stack,  AI/ML integration |
| Medelen Nguyen | @medelennn24   | Python, Pandas, Sklearn |
| Harshal Patel | @Hersh3y  | Python, Applied AI, Backend Dev |
| Joshua Stewart-Roberts | @jroberts2605 | R, Java, Python |
| Dayana Pascual Sanchez | @dayanapascualsanchez | Python, Java, & AI/ML  |

---

## 🎯 **Project Highlights**

- Working on an early-warning system to identify customers at risk of churn using public e-commerce purchase data.
- Exploring changes in purchase frequency, spending, and days since the last purchase to detect declining customer engagement.
- Planning to compare churn prediction models and identify customer lifecycle states through clustering.
- Using a 90-day inactivity definition for churn and limiting features to past data to prevent future information from influencing predictions.

---

## 👩🏽‍💻 **Setup and Installation**

**1. Clone the repository**

```bash
git clone https://github.com/Break-Through-Tech/Amazon-1B-discovering-customer-lifecycle-states-and-behavioral-drift-for-early-churn-detection
cd Amazon-1B-discovering-customer-lifecycle-states-and-behavioral-drift-for-early-churn-detection
```

**2. Create and activate a virtual environment**

```bash
python3 -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
```

**3. Install dependencies**

```bash
pip install -r requirements.txt
```

**4. Access the dataset**

The raw dataset (both years combined, no cleaning applied yet) ships in the repo at [`data/online_retail_ii.parquet`](data/online_retail_ii.parquet) — pulling the repo is enough to get it:

```python
import pandas as pd
df = pd.read_parquet('data/online_retail_ii.parquet')
```

The raw source is the [Online Retail II dataset](https://archive.ics.uci.edu/dataset/502/online%2Bretail%2Bii) from the UCI Machine Learning Repository, if you need to rebuild the parquet from scratch.

**5. Run the notebooks**

WIP

---

## 🏗️ **Project Overview**

- This project is part of the Fall 2026 Break Through Tech AI Studio, where the team is applying machine learning skills to a real-world customer retention problem.
- Guided by an Amazon software development engineer volunteering as our challenge advisor, we are using public e-commerce data to predict churn, detect behavioral changes, and explain customer risk.
- Our work could help businesses identify declining customer engagement earlier, make more informed retention decisions, and reduce revenue loss.

---

## 📊 **Data Exploration - TBD **


* The dataset(s) used: origin, format, size, type of data
* Data exploration and preprocessing approaches
* Insights from your Exploratory Data Analysis (EDA)
* Challenges and assumptions when working with the dataset(s)

**Potential visualizations to include:**

* Plots, charts, heatmaps, feature visualizations, sample dataset images

---

## 🧠 **Model Development - TBD **


* Model(s) used (e.g., CNN with transfer learning, regression models)
* Feature selection and Hyperparameter tuning strategies
* Training setup (e.g., % of data for training/validation, evaluation metric, baseline performance)


---

## 📈 **Results & Key Findings - TBD **

* Performance metrics (e.g., Accuracy, F1 score, RMSE)
* How your model performed
* Insights from evaluating model fairness

**Potential visualizations to include:**

* Confusion matrix, precision-recall curve, feature importance plot, prediction distribution, outputs from fairness or explainability tools

---

## 🚀 **Next Steps - TBD **

* What are some of the limitations of your model?
* What would you do differently with more time/resources?
* What additional datasets or techniques would you explore?

---

## 📝 **License**

Specify how your project can be used by others. Choose an appropriate license and link it here (e.g., MIT, Apache 2.0). Make sure your Challenge Advisor approves of the selected license type. 

**Example:**
This project is licensed under the MIT License.

---

## 📄 **References** (Optional but encouraged)

Cite relevant papers, articles, or resources that supported your project.

---

## 🙏 **Acknowledgements** (Optional but encouraged)

Thank your Challenge Advisor, host company representatives, TA, and others who supported your project.
