# ❤️ Heart Disease Prediction Web App

A machine learning web application built with **Streamlit** and **Scikit-learn** that predicts the risk of heart disease based on clinical patient parameters using a pre-trained **Logistic Regression** model.

---

## 📌 Project Overview

Heart disease is one of the leading causes of mortality worldwide. Early detection and risk assessment can significantly improve clinical outcomes. This application provides a user-friendly, interactive interface for healthcare professionals and individuals to input clinical metrics and receive instant risk predictions.

---

## 🚀 Live Demo

👉 [Try the Heart Disease Prediction App](https://heart-disease-prediction-app-lmwzfrvwrhsf85aw8tdptd.streamlit.app/)

---



## ✨ Features

- **Interactive User Interface**: Built with Streamlit, providing intuitive sliders, numeric inputs, and dropdown selectors.
- **Instant Risk Assessment**: Immediate feedback indicating either **Low Risk** or **High Risk** of heart disease.
- **Robust Feature Alignment**: Ensures user inputs match the exact feature columns and encodings used during model training.
- **Lightweight & Fast**: Uses serialized models and preprocessors with `joblib` for rapid inference with minimal overhead.
- **Deployment Ready**: Optimized directory structure and relative path resolution for seamless deployment to Streamlit Community Cloud.

---

## 🛠️ Technologies Used

- **Python**: Core programming language.
- **Streamlit**: Web application framework for machine learning and data science.
- **Scikit-learn (1.6.1)**: Machine learning library used for training the Logistic Regression model and StandardScaler.
- **Pandas**: Data manipulation and feature vector alignment.
- **NumPy**: Numerical operations.
- **Joblib**: Efficient serialization and loading of Python objects/models.

---

## 🧠 How the Machine Learning Model Works

1. **Input Collection**:
   The user enters 11 clinical features via the Streamlit interface:
   - **Age**: Patient's age in years.
   - **Sex**: Biological sex (`M`, `F`).
   - **Chest Pain Type**: `ATA` (Atypical Angina), `NAP` (Non-Anginal Pain), `TA` (Typical Angina), `ASY` (Asymptomatic).
   - **Resting Blood Pressure**: Resting BP in mm Hg.
   - **Cholesterol**: Serum cholesterol in mg/dL.
   - **Fasting Blood Sugar**: Fasting blood sugar > 120 mg/dL (`1` for True, `0` for False).
   - **Resting ECG**: Resting electrocardiogram results (`Normal`, `ST`, `LVH`).
   - **Max Heart Rate**: Maximum heart rate achieved (60–220 bpm).
   - **Exercise-Induced Angina**: Presence of angina during exercise (`Y`, `N`).
   - **Oldpeak**: ST depression induced by exercise relative to rest.
   - **ST Slope**: Slope of the peak exercise ST segment (`Up`, `Flat`, `Down`).

2. **Feature Encoding & Alignment**:
   - Categorical inputs are one-hot encoded to match the dummy variable columns created during model training (e.g., `Sex_M`, `ChestPainType_ATA`, `ST_Slope_Flat`).
   - The input vector is compared against `column.pkl` (`expected_columns`) to guarantee that all expected features are present in the exact order required by the model.

3. **Classification**:
   - The processed feature vector is passed to the trained **Logistic Regression** classifier (`logistic_regression.pkl`).
   - The model predicts:
     - **0**: Low Risk of Heart Disease (`✅ Low Risk of Heart Disease`)
     - **1**: High Risk of Heart Disease (`⚠️ High Risk of Heart Disease`)

---

## 📁 Project Structure

```text
heart-disease-prediction-streamlit/
│
├── app.py                   # Streamlit web application & prediction logic
├── logistic_regression.pkl  # Trained Logistic Regression model
├── scaler.pkl               # Fitted StandardScaler preprocessor
├── column.pkl               # Serialized training feature column schema
├── requirements.txt         # Project dependencies (scikit-learn==1.6.1, etc.)
├── .gitignore               # Git ignore configuration
└── README.md                # Project documentation
```

---

## 🚀 How to Run the Project Locally

### 1. Clone or Navigate to the Project Directory

```bash
git clone https://github.com/<your-username>/Heart_disease.git
cd Heart_disease
```

### 2. Create and Activate a Virtual Environment (Recommended)

- **On Windows (PowerShell):**
  ```powershell
  python -m venv venv
  .\venv\Scripts\Activate.ps1
  ```
- **On macOS / Linux:**
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```

### 3. Install Dependencies

Install all required packages specified in `requirements.txt`:

```bash
pip install -r requirements.txt
```

> **Note:** Ensure `scikit-learn==1.6.1` is installed to match the version used when training the model.

### 4. Run the Streamlit Application

Launch the app using:

```bash
python -m streamlit run app.py
```
or:
```bash
streamlit run app.py
```

### 5. Access the Web App

Open your browser and navigate to:
```
http://localhost:8501
```

---

## ☁️ Deployment Instructions (Streamlit Community Cloud)

To deploy your application publicly using Streamlit Community Cloud:

1. **Push your repository to GitHub**:
   Ensure all files (`app.py`, `requirements.txt`, `.pkl` files, and `README.md`) are committed and pushed to a public or private GitHub repository (see Git instructions below).

2. **Sign In to Streamlit Cloud**:
   Visit [share.streamlit.io](https://share.streamlit.io/) and log in using your GitHub account.

3. **Create a New App**:
   - Click on the **"New app"** button.
   - Select your repository (`<your-username>/Heart_disease`).
   - Set the Branch to `main` (or `master`).
   - Set the Main file path to `app.py`.

4. **Deploy**:
   - Click **"Deploy!"**.
   - Streamlit Cloud will automatically detect `requirements.txt`, install dependencies (including `scikit-learn 1.6.1`), and launch the application.
