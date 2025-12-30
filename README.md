# **Breast Cancer Classification using Machine Learning**

## **Project Overview**

This project aims to develop a reliable machine learning model to classify breast tumors as **malignant** or **benign** using numerical features extracted from fine-needle aspirate (FNA) images of cell nuclei.
The emphasis is placed on **robust baseline modeling**, **interpretability**, and **disciplined evaluation**, rather than aggressive metric optimization.

## **Dataset Description**

- Source: Breast Cancer Wisconsin (Diagnostic) Dataset
- Samples: 569
- Target Variable:
  - M → Malignant
  - B → Benign
- Features: 30 continuous numerical features derived from cell nucleus characteristics:
  - Mean measurements (*_mean)
  - Standard error measurements (*_se)
  - Worst-case measurements (*_worst)
- Data Quality:
  - No missing values in predictive features
  - No duplicate records
  - One non-informative identifier column removed (id)
 
## **Modeling Approach**

The problem is formulated as a binary classification task.
The modeling strategy follows a structured pipeline:
1. Exploratory Data Analysis (EDA) to understand feature behavior and class separability
2. Feature scaling (where required)
3. Stratified train–test split to preserve class proportions
4. Evaluation of multiple baseline models using consistent preprocessing and metrics
Outlier removal was deliberately avoided, as extreme values reflect real biological variation.

## **Initial Model Performance**

Four baseline models were evaluated without hyperparameter tuning:

| Model               | ROC–AUC | Accuracy | Malignant Recall |
| ------------------- | ------: | -------: | ---------------: |
| Logistic Regression |  ~0.995 |    ~0.97 |             0.95 |
| SVM (RBF)           |  ~0.995 |    ~0.98 |             0.98 |
| Random Forest       |  ~0.995 |    ~0.98 |             0.98 |
| KNN                 |   ~0.98 |    ~0.96 |             0.90 |

All top-performing models achieved near-saturated ROC–AUC, indicating strong inherent class separability in the dataset.

## **Overfitting Control & Hyperparameter Tuning**

Hyperparameter tuning was intentionally not performed.
This decision was driven by:
- The small dataset size, where extensive tuning increases overfitting risk
- The already excellent baseline performance, leaving little room for meaningful improvement
- The medical context, where model stability and generalization are prioritized over marginal metric gains
Rather than chasing negligible score improvements, this project favors **robust and reproducible baseline models**.

## **Performance Comparison**

- Logistic Regression provides strong performance with high interpretability, making it suitable for transparent decision-making.
- SVM (RBF) and Random Forest marginally outperform Logistic Regression, offering better malignant recall and flexibility.
- KNN shows comparatively weaker recall for malignant cases and is not considered a final candidate.
Performance differences between the top models are small and not clinically significant, reinforcing that model choice should be driven by deployment needs rather than raw metrics alone.

## **Business Interpretation**

From a real-world and clinical perspective:
- False negatives (missed malignant cases) are more costly than false positives.
- Models with high recall for malignant tumors are therefore preferred.
- Stability, interpretability, and reproducibility are more valuable than marginal accuracy gains.

This makes Logistic Regression (interpretability) and SVM / Random Forest (robust performance) all viable depending on operational constraints.

## **Project Conclusion**

This project demonstrates that, on a clean and information-rich medical dataset, careful EDA, principled baseline modeling, and restrained optimization are sufficient to achieve excellent performance.

Avoiding hyperparameter tuning in this context is a deliberate modeling choice, not a limitation.
The results highlight the importance of model reliability and interpretability over metric chasing in healthcare applications.

## **Tools & Libraries (Dependencies)**

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- scikit-learn

## **How to Run**

1. Clone the repository:
```bash
git clone https://github.com/PranayDomal/Brest-Cancer-Prediction.git
```

2. Navigate to the folder:
```bash
cd Brest-Cancer-Prediction
```

3. Run the notebook:
```bash
jupyter notebook Brest_Cancer_Prediction.ipynb
```

## **Project Structure**
```
├── Brest_Cancer_Prediction.ipynb
├── Brest_Cancer_Prediction.pdf
├── Brest_Cancer_Dataset.csv
├── README.md
```

## **Author**

https://www.linkedin.com/in/pranay-domal-a641bb368/
