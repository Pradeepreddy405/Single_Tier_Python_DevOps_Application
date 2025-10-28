# Single_Tier_Python_DevOps_Application
This project demonstrates a **single-tier (monolithic)** Python web application deployed on a **Linux server** with **Git-based version control** and simple **DevOps automation**.

# 🐍 Single_Tier_Python_DevOps_Application

## 📘 Project Overview
This project demonstrates a **single-tier (monolithic)** Python application deployed on a **CentOS Linux server** with **Git-based version control** and simple **DevOps automation** using **Jenkins**.  
The goal is to showcase how DevOps practices (version control, CI/CD, and automation) can be applied even to a standalone desktop Python app.



## 🧩 Architecture
┌───────────────────────────────────────────────┐
│ Single Tier │
│ ┌────────────┐ ┌────────────┐ ┌─────────┐ │
│ │ UI Layer │ → │ Logic Layer│ → │ Data DB │ │
│ │ (Tkinter) │ │ (Python) │ │(SQLite) │ │
└───────────────────────────────────────────────┘
▲
│
CI/CD Pipeline (Jenkins)
│
▼
GitHub Repository (Code)

## ⚙️ Tools and Technologies
| Component | Tool / Technology |
|------------|-------------------|
| **Operating System** | CentOS Linux |
| **Programming Language** | Python 3 |
| **Database** | SQLite |
| **Version Control** | Git & GitHub |
| **CI/CD Tool** | Jenkins |
| **Automation** | Bash |
| **Packaging** | PyInstaller |
| **Testing** | Pytest |

## 📁 Project Structure
Single_Tier_Python_DevOps_Application/
├── app/
│ ├── main.py # Entry point (Tkinter UI)
│ ├── models.py # Database logic
│ └── ui.py # GUI components
├── tests/
│ └── test_models.py # Unit tests
├── scripts/
│ └── package.sh # Packaging script using PyInstaller
├── requirements.txt # Dependencies
├── Jenkinsfile # CI/CD pipeline configuration
└── README.md # Project documentation





---------------------------------------------------------------🧰 Setup Instructions------------------------------------------------------




### 1️⃣ Install Prerequisites on CentOS
commands : 
sudo yum update -y
sudo yum install -y git python3 python3-pip

##Optional (for CI/CD):
## Install Jenkins
sudo wget -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io.key
sudo yum install -y jenkins java-11-openjdk
sudo systemctl enable --now jenkins

2️⃣ Clone the Repository
git clone https://github.com/<your-username>/Single_Tier_Python_DevOps_Application.git
cd Single_Tier_Python_DevOps_Application

3️⃣ Install Dependencies
pip3 install -r requirements.txt

4️⃣ Run the Application Locally
python3 app/main.py

5️⃣ Run Unit Tests
pytest tests/ --maxfail=1 --disable-warnings -q

6️⃣ Package the Application
chmod +x scripts/package.sh
./scripts/package.sh


This generates an executable inside the dist/ folder:

dist/expense_app

🔄 Jenkins CI/CD Pipeline

Pipeline Stages:

Checkout – Pull code from GitHub

Install Dependencies – Set up Python environment

Test – Run Pytest for validation

Package – Build executable using PyInstaller

(Optional) Deploy or publish artifact

Jenkinsfile Overview
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Install Dependencies') {
            steps { sh 'pip3 install -r requirements.txt' }
        }
        stage('Run Tests') {
            steps { sh 'pytest tests/ --maxfail=1 --disable-warnings -q' }
        }
        stage('Package App') {
            steps { sh './scripts/package.sh' }
        }
    }
    post {
        success { echo '✅ Build successful!' }
        failure { echo '❌ Build failed.' }
    }
}


🔗 Git & GitHub Workflow
-- Action	Command
-- Clone repo	git clone <repo-url>
-- Create new branch	git checkout -b feature-branch
-- Commit changes	git commit -m "Added feature"
-- Push branch	git push origin feature-branch
-- Merge changes	Create a Pull Request on GitHub

🧩 DevOps Concepts Demonstrated
-- DevOps Practice	Implementation
-- Version Control	Git & GitHub
-- Continuous Integration	Jenkins (Build + Test)
-- Continuous Delivery	Automated packaging
-- Automation	Bash scripts
-- Monitoring & Reporting	Jenkins console logs
