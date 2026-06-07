# DSO101 – Assignment 4: CI/CD Pipeline with GitHub Actions and Render

# Student information
**Name:** Sangay Wangchuk  
**Student ID:** 02250367  
**Module:** DSO101  
**GitHub Repository:** https://github.com/SWangchuk676/SangayWangchuk_02250367_DSO101_A4  
**Live URL:** https://my-flask-app.onrender.com  

## 1. Introduction

This assignment involves building a simple Python Flask web application, pushing it to a GitHub repository, setting up a CI/CD pipeline using GitHub Actions, and deploying it live using Render. The goal is to demonstrate an understanding of continuous integration and continuous deployment concepts in a real-world workflow.

## 2. Application Overview

A simple Flask web application was created that returns a plain text response when accessed via a browser.

### Project Structure

```
SangayWangchuk_02250367_DSO101_A4/
└── my-web-app/
    ├── app.py
    ├── requirements.txt
    ├── README.md
    └── .github/
        └── workflows/
            └── deploy.yml
```

### app.py

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Hello DevOps!"

if __name__ == '__main__':
    app.run()
```

### requirements.txt

```
flask
gunicorn
```

### .github/workflows/deploy.yml

```yaml
name: Deploy to Render

on:
  push:
    branches: [ "main" ]

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Dummy step
      run: echo "Code pushed successfully!"
```

---

## 3. Steps to Run Locally

1. Clone the repository:
   ```bash
   git clone https://github.com/SWangchuk676/SangayWangchuk_02250367_DSO101_A4.git
   ```

2. Navigate into the project folder:
   ```bash
   cd SangayWangchuk_02250367_DSO101_A4/my-web-app
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

4. Run the app:
   ```bash
   python app.py
   ```

5. Open your browser and go to: `http://localhost:5000`

---

## 4. GitHub Setup

The project was pushed to a public GitHub repository. The repository was connected to Render for automatic deployment on every push to the `main` branch.

**Screenshot – Connecting GitHub repository to Render:**

![GitHub Repo Connected to Render](screenshots/image.png)

---

## 5. GitHub Actions CI/CD Workflow

A GitHub Actions workflow was configured to trigger automatically on every push to the `main` branch. The workflow checks out the code and runs a confirmation step.

**Workflow trigger:** Push to `main` branch  
**Runner:** `ubuntu-latest`

---

## 6. Deployment on Render

The Flask application was deployed on Render as a Web Service using the following configuration:

| Setting | Value |
|---|---|
| Environment | Python |
| Root Directory | `my-web-app` |
| Build Command | `pip install -r requirements.txt` |
| Start Command | `gunicorn app:app` |
| Instance Type | Free |

**Screenshot – Successful Build on Render:**

![Build Successful](screenshots/image2.png)

**Screenshot – Deployment History showing Live Deploy:**

![Deploy Live](screenshots/image3.png)

---

## 7. Live Application

The application was successfully deployed and is accessible at the live Render URL.

**Screenshot – Live Application in Browser:**

![Hello DevOps](screenshots/image4.png)

The app displays **"Hello DevOps!"** confirming the deployment was successful.

## 8. Conclusion

This assignment demonstrated a complete CI/CD pipeline:

- A Flask web app was built and version-controlled using Git and GitHub.
- A GitHub Actions workflow was set up to trigger on every push to `main`.
- The application was deployed live on Render with automatic re-deployment on new commits.
- The live application is accessible publicly via the Render URL.

This workflow reflects real-world DevOps practices where code changes are automatically tested and deployed without manual intervention.