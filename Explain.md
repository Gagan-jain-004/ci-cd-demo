 mkdir -p .github/workflows

 vi .github/workflows/main.yml

-> go to repo -> actions  -> click ... at right  -> view workflow  -> click on build at left sidebar -> Run Script 

---

## 🧾 Workflow Name
```yaml
name: Python CI
```
- This sets the name of the workflow as **"Python CI"** — it’ll show up like this in the GitHub Actions tab.

---

## 🚀 Trigger Conditions
```yaml
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
```
- The workflow runs automatically when:
  - You **push** code to the `main` branch.
  - You **open or update a pull request** targeting the `main` branch.

---

## 🧱 Job Definition
```yaml
jobs:
  run-script:
    runs-on: ubuntu-latest
```
- Defines a job named `run-script`.
- It runs on the **latest Ubuntu runner** provided by GitHub.

---

## 🔨 Steps Inside the Job

### 1. ✅ Checkout Code
```yaml
- name: ⬇️ Checkout code
  uses: actions/checkout@v4
```
- This step **clones your repository** into the runner so the workflow can access your files (like `hello.py`).

---

### 2. 🐍 Set Up Python
```yaml
- name: Set up Python
  uses: actions/setup-python@v4
  with:
    python-version: '3.11'
```
- Installs **Python 3.11** on the runner.
- Ensures your script runs in the correct Python environment.

---

### 3. 📦 Install Dependencies
```yaml
- name: Install dependencies (if any)
  run: |
    python -m pip install --upgrade pip
    # pip install -r requirements.txt  # Uncomment if you add dependencies
```
- Upgrades `pip` to the latest version.
- If you add a `requirements.txt` later, you can uncomment the second line to install packages.

---

### 4. 🚀 Run Your Script
```yaml
- name: Run hello.py
  run: python hello.py
```
- Executes your Python script.
- In your case, it prints:
  ```
  CI/CD with Github Actions
  done
  ```

---

### 🧠 Summary
This workflow is perfect for a **CI/CD demo**. It’s clean, modular, and ready to extend. You can later add:
- `pytest` for testing
- `flake8` for linting
- Deployment steps (e.g., Docker, SSH, or cloud CLI)

Want me to scaffold those next steps for you?
