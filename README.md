# AlphabetSoupCharity Deep Learning Model Report

## **Overview**
This project aims to build and optimize a deep learning model to predict whether applicants for funding from AlphabetSoupCharity will be successful. The goal was to achieve an accuracy of **at least 75%** using a **neural network model (deep learning)**.

---

## **Results**

### **Data Preprocessing**
#### **Target Variable**
- The target variable for this model is:
  - `IS_SUCCESSFUL` (Binary: 1 for successful funding, 0 for unsuccessful).

#### **Feature Variables**
- Features used in the model include:
  - `APPLICATION_TYPE`
  - `CLASSIFICATION`
  - `USE_CASE`
  - `ORGANIZATION`
  - `ASK_AMT`

#### **Removed Variables**
![image](https://github.com/user-attachments/assets/cb85d84c-a119-4f83-a553-f1490d4e73e3)

- The following columns were removed as they are **not useful for predictions**:
  - `EIN` (Employer Identification Number)
  - `NAME` (Applicant’s Name)

---

### **Model Architecture**
| Layer | Neurons | Activation Function |
|--------|---------|---------------------|
| **Input Layer** | 100 | ReLU |
| **Hidden Layer 1** | 50 | ReLU |
| **Hidden Layer 2** | 30 | Tanh |
| **Output Layer** | 1 | Sigmoid |

- **Why these selections?**
  - **ReLU** for efficient learning.
  - **Tanh** for diverse feature extraction.
  - **Sigmoid** for binary classification.

#### **Model Performance**
- **Final Accuracy on Test Data:** ~**72-74%**
- **Target Accuracy (≥75%)**: ❌ Not achieved.

---

### **Steps Taken to Improve Performance**
- **Data Adjustments:**
  - Grouped rare categories in **APPLICATION_TYPE** and **CLASSIFICATION** as `"Other"`.
  - Applied **one-hot encoding** to categorical variables.
  - Standardized numerical features using **StandardScaler**.

- **Model Adjustments:**
  - Increased neurons and added a third hidden layer.
  - Tried different activation functions (`ReLU`, `Tanh`, `Sigmoid`).
  - Increased training epochs **(from 50 to 100)**.
  - Used a **checkpoint callback** to save the best model.
  - Attempted **Dropout layers** to reduce overfitting (minimal impact).

---

### **Training Performance**
**Training Accuracy & Loss Graphs**
![Training Accuracy](images/training_accuracy.png)
![Training Loss](images/training_loss.png)

---

## **Alternative Model Recommendation**
While deep learning models work well for **complex, unstructured data**, structured tabular data often performs better with **tree-based models** like **Random Forest or XGBoost**.

| Model | Accuracy | Pros | Cons |
|--------|---------|------|------|
| **Neural Network** | 72-74% | Handles complex patterns | Hard to tune, slow |
| **XGBoost** | TBD | Handles categorical data well | May need feature selection |
| **Random Forest** | TBD | Robust, interpretable | Slower on large datasets |

✅ **Recommendation**: Try **XGBoost or Random Forest**, refine feature selection, and re-test.

---


## **Final Thoughts**
- **Deep learning was not the best approach for this problem.**
- **A different machine learning model** (e.g., XGBoost) might achieve **higher accuracy** and better interpretability.

