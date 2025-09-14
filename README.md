# 📌 Complete Spam Classifier Pipeline (MLOps Project)

This repository implements a **modular and production-ready ML pipeline** with proper logging, experiment tracking, and reproducibility using **DVC** (Data Version Control).  

The project is designed around the **Spam Detection Problem** (`spam.csv` dataset) but the pipeline is fully reusable for other ML tasks.  

---

## 🚀 Project Structure

```

COMPLETE-ML\_PIPELINE/
│
├── .dvc/                     # DVC metadata
├── data/                     # Raw and processed datasets (tracked by DVC)
├── dvclive/                  # DVC experiment tracking logs
├── env/                      # Virtual environment (not versioned)
│
├── experiments/              # Experiment-related files
│   ├── mynotebook.ipynb      # Jupyter notebook for exploration
│   └── spam.csv              # Dataset
│
├── logs/                     # Logs generated during pipeline execution
│   ├── data\_ingestion.log
│   ├── data\_preprocessing.log
│   ├── feature\_engineering.log
│   ├── model\_building.log
│   └── model\_evaluation.log
│
├── models/                   # Serialized trained models
│   └── model.pkl
│
├── reports/                  # Model reports & metrics
│   └── metrics.json
│
├── src/                      # Source code (modular pipeline scripts)
│   ├── data\_ingestion.py
│   ├── data\_preprocessing.py
│   ├── feature\_engineering.py
│   ├── model\_building.py
│   └── model\_evaluation.py
│
├── .dvcignore                # Files ignored by DVC
├── .gitignore                # Files ignored by Git
├── dvc.lock                  # DVC pipeline lock file
├── dvc.yaml                  # DVC pipeline definition
├── LICENSE                   # License file
├── params.yaml               # Parameters for pipeline execution
└── README.md                 # Project documentation

````

---

## ⚙️ Pipeline Stages

This project follows a modular **end-to-end ML pipeline**:

1. **Data Ingestion (`src/data_ingestion.py`)**  
   - Loads raw dataset (`spam.csv`)  
   - Stores dataset in `data/`  
   - Logs details in `logs/data_ingestion.log`

2. **Data Preprocessing (`src/data_preprocessing.py`)**  
   - Cleans text data  
   - Handles missing values, normalization, stopwords, etc.  
   - Logs steps in `logs/data_preprocessing.log`

3. **Feature Engineering (`src/feature_engineering.py`)**  
   - Converts text into numerical features (TF-IDF, Bag of Words, etc.)  
   - Creates training/test splits  
   - Logs details in `logs/feature_engineering.log`

4. **Model Building (`src/model_building.py`)**  
   - Trains ML model (e.g., Logistic Regression, Random Forest)  
   - Saves model in `models/model.pkl`  
   - Logs training details in `logs/model_building.log`

5. **Model Evaluation (`src/model_evaluation.py`)**  
   - Evaluates trained model on test data  
   - Generates metrics (accuracy, precision, recall, F1) in `reports/metrics.json`  
   - Logs results in `logs/model_evaluation.log`

---

## 📊 Experiment Tracking with DVC

- **DVC** is used to version datasets, models, and pipeline stages.  
- Run the pipeline with:

```bash
dvc repro
````

* Compare experiments:

```bash
dvc metrics show
dvc metrics diff
```

---

## ⚡ Getting Started

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/yourusername/complete-ml-pipeline.git
cd complete-ml-pipeline
```

### 2️⃣ Create Virtual Environment

```bash
python -m venv env
source env/Scripts/activate  # For Windows
# or
source env/bin/activate      # For Linux/Mac
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Initialize DVC

```bash
dvc init
dvc repro
```

---

## 📂 Parameters (`params.yaml`)

All configurable parameters (e.g., dataset paths, model hyperparameters, preprocessing configs) are defined in **params.yaml**.
This allows easy reproducibility and experiment tuning.

Example:

```yaml
data:
  raw_path: data/raw/spam.csv
  processed_path: data/processed/

model:
  type: logistic_regression
  max_iter: 1000
  test_size: 0.2
  random_state: 42
```

---

## 📑 Logs

Logs are generated for every stage and stored in `logs/`.
This ensures debugging and auditing capabilities.

Example:

```text
logs/data_ingestion.log
logs/data_preprocessing.log
logs/feature_engineering.log
logs/model_building.log
logs/model_evaluation.log
```

---

## 📈 Reports

* **metrics.json** stores evaluation results in structured format
* Can be compared across runs using `dvc metrics diff`

Example:

```json
{
  "accuracy": 0.95,
  "precision": 0.94,
  "recall": 0.93,
  "f1_score": 0.935
}
```

---

## 🛠️ Tech Stack

* **Python**
* **Scikit-learn**
* **Pandas / Numpy**
* **NLTK / Text Processing**
* **DVC (Data Version Control)**
* **Git for Version Control**
* **Logging for Monitoring**

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙌 Contributions

Contributions, issues, and feature requests are welcome!
Feel free to fork the repo and submit a PR.

```

---

Do you want me to also **generate a `requirements.txt` file** for this pipeline (with sklearn, pandas, numpy, nltk, dvc, etc.)?
```
