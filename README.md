# 🚀 Jio Hotstar Content Classification: A Deep Dive into Content Structure

## Project Goal
This project moved beyond traditional descriptive analysis to build a **perfectly accurate binary classification model**. The goal was to systematically analyze Hotstar's content metadata and definitively prove **which features** drive the distinction between a **Movie** and a **TV Show**.

This demonstrates a complete data science workflow, from data cleaning and exploratory analysis to advanced modeling, cross-validation, and crucial feature interpretability.

---

## 🛠️ Methodology & Workflow

Our process was designed to ensure rigor and reliability:

1.  **Data Preparation:** We addressed a classic real-world data challenge: **structural missingness** (TV shows miss runtime, movies miss episodes). We used logical imputation (0 or median) to ensure no information was lost.
2.  **Exploratory Data Analysis (EDA):** We dove deep into the data with a rich set of visualizations to understand distributions, identify relationships, and confirm our initial hypotheses visually.
3.  **Data Transformation:** We used **One-Hot Encoding** to prepare categorical features (`genre`, `age_rating`) into the numerical matrix required for modeling.
4.  **Modeling & Optimization:** We established a **Logistic Regression** baseline, optimized using the **Random Forest Classifier**, and ensured stability using **5-Fold Cross-Validation**.
5.  **Proof & Interpretability:** We used the **AUC Score** for robust performance measurement and **Feature Importance** to quantify *why* the model made its decisions.

---

## 📊 Exploratory Data Analysis (EDA) Visualizations

The visualizations confirm the inherent structural differences in the content library:

### Content Type and Distribution
The analysis began with a look at the content balance and production history.

| Content Type Distribution | Production Year Distribution |
| :--- | :--- |
| ![Count plot showing the distribution of Movies vs TV Shows](image_d7f702.jpg) | ![Histogram showing the distribution of content production years](image_d703e1.jpg) |

### Feature Relationships
The box plot clearly highlights the reason for the model's perfect score: the numerical features provide complete separation.

| Running Time Distribution by Type | Age Rating Distribution by Type |
| :--- | :--- |
| ![Box plot comparing running time across Movies and TV Shows](image_cb9af7.jpg) | ![Grouped bar chart showing content type separated by age rating](image_97f719.jpg) |

### Advanced Visualizations
The correlation heatmap and genre popularity charts provided deeper context on content strategy.

| Numerical Feature Correlation (Heatmap) | Top 10 Primary Genres |
| :--- | :--- |
| ![Heatmap showing correlation between numerical features](image_8cb35c.jpg) | ![Bar chart of the 10 most frequent primary genres](image_8890ca.jpg) |

---

## 💡 Model Performance & Strategic Insight

### A. Model Performance Summary

The model achieved **perfect classification** across all metrics, validating the power of the core features in the dataset.

| Metric | Logistic Regression | Random Forest Classifier | Interpretation |
| :--- | :--- | :--- | :--- |
| **Cross-Validation Accuracy** | **1.0000** | **1.0000** | Stability is perfect; the model is fully reliable. |
| **AUC Score (Test Set)** | - | **1.0000** | The model's ability to discriminate between the two content types is flawless. |
| **Precision & Recall** | **1.00** | **1.00** | There are zero False Positives or False Negatives. |

### B. Feature Interpretability: The Actionable Insight

The **Feature Importance** analysis (represented by the bar chart below) delivers the project's most critical business insight:

* The features **`running_time`** and the presence of **`seasons` / `episodes`** are the **sole dominant factors** driving content classification.
* **Conclusion:** For automatic tagging of new content, a system only needs to check these two numerical attributes for perfect classification, making all other metadata (genre, year, etc.) secondary to this specific task.

![Bar chart showing the importance of each feature in the Random Forest Model](image_88a443.jpg)

---

## 💻 Technology Stack

* **Language:** Python
* **Core Libraries:** `Pandas`, `NumPy`, `Seaborn`, `Matplotlib`
* **Machine Learning:** `Scikit-learn` (`LogisticRegression`, `RandomForestClassifier`, `cross_val_score`, `roc_auc_score`, `classification_report`)
