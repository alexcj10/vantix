# ML Project Setup Guide
A standard, reproducible setup process for Machine Learning and Data Science projects.

---

## 1. Create Project Folder

Creates a clean root folder for the project. Everything lives inside this folder.

```bash
mkdir project_name
cd project_name
```

---

## 2. Create Virtual Environment

Isolates project dependencies and prevents conflicts with system Python.

```bash
python -m venv venv
```

---

## 3. Activate Virtual Environment

Tells the system to install and use packages only for this project.

**Windows**
```bash
venv\Scripts\activate
```

**Linux / Mac**
```bash
source venv/bin/activate
```

---

## 4. Upgrade Core Python Tools

Ensures latest and stable package handling.

```bash
pip install --upgrade pip setuptools wheel
```

---

## 5. Create Project Folder Structure

Keeps data, code, configs, and experiments organized. Matches production and industry standards.

```bash
mkdir data notebooks src configs logs tests
mkdir data/raw data/processed
mkdir src/features src/models src/training src/inference
```

What each folder is for:

- `data/raw/` — original, untouched data
- `data/processed/` — cleaned and transformed data
- `notebooks/` — EDA, experiments, visualization
- `src/` — all production Python code
- `configs/` — configuration files (YAML/JSON)
- `logs/` — log files
- `tests/` — unit and integration tests

---

## 6. Create Required Files

These files are needed for dependency tracking, configs, and execution.

**Windows**
```bash
type nul > requirements.txt
type nul > .gitignore
type nul > README.md
type nul > .env
type nul > configs/config.yaml
type nul > src/training/train.py
```

**Linux / Mac**
```bash
touch requirements.txt .gitignore README.md .env
touch configs/config.yaml
touch src/training/train.py
```

---

## 7. Install Common ML / DS Dependencies

Installs libraries used for data analysis, ML, APIs, and experiments. Installed inside venv only.

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter
pip install mlflow fastapi uvicorn python-dotenv
```

---

## 8. Save Installed Dependencies

Freezes exact package versions so anyone can recreate the same environment.

```bash
pip freeze > requirements.txt
```

Note: `requirements.txt` always stays in the project root, never inside `venv`.

---

## 9. Setup .gitignore

Prevents unnecessary or sensitive files from being pushed to GitHub.

```bash
echo venv/ >> .gitignore
echo __pycache__/ >> .gitignore
echo .ipynb_checkpoints/ >> .gitignore
echo .env >> .gitignore
echo *.log >> .gitignore
```

---

## 10. Write Training Entry Script

Single entry point to train models. Notebooks are not used for final training.

Edit `src/training/train.py`:

```python
def train():
    print("Training started")

if __name__ == "__main__":
    train()
```

---

## 11. Run Training Script

Confirms the project structure and environment are working correctly.

```bash
python src/training/train.py
```

---

## 12. Initialize Git Repository

Enables version control. Required for collaboration and deployment.

```bash
git init
git add .
git commit -m "Initial ML project setup"
```

---

## 13. Recreate Environment (If venv Is Deleted)

The venv folder is disposable and can be rebuilt anytime from `requirements.txt`.

```bash
python -m venv venv
venv\Scripts\activate
pip install -r requirements.txt
```

---

## 14. Deactivate Virtual Environment

Exit the project environment safely.

```bash
deactivate
```

---

## Key Rules

- Never write code inside `venv`
- Never commit `venv` to GitHub
- Always activate venv before working
- All production code lives in `src/`
- Notebooks are for EDA only

---

> Virtual environment isolates dependencies, `requirements.txt` guarantees reproducibility, and a clean folder structure keeps ML projects production-ready.
