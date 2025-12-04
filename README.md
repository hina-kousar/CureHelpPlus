# CureHelp+   |    AI-Powered Health Risk Analyzer

<div align="center">

![CureHelp+](https://img.shields.io/badge/CureHelp+-Healthcare_AI-blue?style=for-the-badge&logo=medical)
![Flask](https://img.shields.io/badge/Built%20with-Flask-000000?style=for-the-badge&logo=flask)
![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn)

**Your Personal Health Companion for Predictive Diagnostics and Medical Assistance**

[![Demo](https://img.shields.io/badge/🚀-Live_Demo-2EA043?style=for-the-badge)](#quick-start)
[![Documentation](https://img.shields.io/badge/📚-Documentation-8A2BE2?style=for-the-badge)](#documentation)
[![Issues](https://img.shields.io/badge/🐛-Report_Issues-FF6B6B?style=for-the-badge)](https://github.com/your-repo/issues)

</div>

## 🌟 Overview

CureHelp+ is an advanced healthcare analytics platform that leverages machine learning to provide comprehensive health risk assessments, predictive diagnostics, and personalized medical guidance. The latest release ships with a Flask-powered dashboard, offline-first patient profile storage, a revamped chatbot experience, and production-ready PDF reporting. An embedded medical assistant is integrated with curated clinical datasets for faster, higher-quality responses.

---

## Deployment 
**Live** - https://www.curehelplus.me
**Azure Live** - https://curehelplus.blackpebble-3708035a.centralindia.azurecontainerapps.io
**Docker Image** - https://hub.docker.com/r/asimhusain/curehelplus

---

---

## Author
Made with ❤️ By: **Asim Husain** https://www.asimhusain.dev

---

### Key Features

- 🩺 **Multi-Disease Risk Prediction** - Diabetes, Heart Disease(Blockage), Fever, and Anemia with calibrated probabilities
- 🤖 **AI Medical Assistant** - Rule-based chatbot with live typing indicator and curated medical knowledge base
- 📊 **Interactive Visualizations** - Risk gauges, comparison grids, and real-time result cards
- 👨‍⚕️ **Healthcare Provider Directory** - Nearby hospitals and specialists with direct map links
- 🗂️ **Patient Profile Management** - Secure JSON-backed storage with session syncing
- 📄 **PDF Report Generation** - Publication-ready clinical reports generated via Matplotlib
- 💊 **Clinical Guidance** - Evidence-aligned prevention protocols and medication suggestions
- ⚙️ **One-Click Test Inputs** - Authentic normal and abnormal presets for every disease form


---

## Machine Learning Models
## Model Architecture

| Disease | Algorithm | Accuracy | Features | Special Notes |
|---------|-----------|----------|----------|---------------|
| **Diabetes** | XGBoost | 95% | 8 features | Handles gender-specific parameters |
| **Heart Disease** | Random Forest | 96% | 13 features | Comprehensive cardiac assessment |
| **Fever** | Dual Random Forest | 96% | 18 features | Severity + Risk classification |
| **Anemia** | Multi-output RF | 94% | 14 features | Risk + Type prediction |

---

## Usage

1.  **Landing Page:** Upon launching the application, you will be greeted by the landing page. Click on "Get Started" to proceed.
2.  **Patient Details:** Fill in your personal details to create a profile. This information will be used to personalize the predictions and reports.
3.  **Input Health Metrics:** Navigate through the different tabs for each disease (Diabetes, Heart Disease, Fever, Anemia) and enter your health metrics.
4.  **Predict Risk:** Click on the "Predict" button to get your risk assessment.
5.  **View Results:** Review interactive gauges, comparator cards, and AI-powered recommendations.
6.  **Generate Report:** Download a consolidated PDF report with risk protocols and clinical interventions.
7.  **Explore Directory:** Browse nearby hospitals and doctors, or use search to filter specialists.


## Performance Metrics

### Model Performance
- **Overall Accuracy**: 84.75% average across all models
- **Precision**: 90-94% range depending on disease
- **Recall**: 89-94% for critical condition detection  
- **F1-Score**: 91% balanced performance metric

### System Performance
- **Response Time**: ~1.8 seconds for predictions on a typical laptop
- **Concurrent Users**: Session-isolated Flask backend supporting multiple users
- **Memory Usage**: Lazy model loading and cached chatbot datasets
- **Scalability**: Modular services for predictions, chat, parsing, and reporting

### Privacy & Security

### Data Protection
- **Local Storage**: All user data stored locally in `user_profiles.json`
- **No Cloud Transmission**: Privacy-first approach with offline datasets in `bot_data/`
- **Anonymous Analytics**: Optional usage statistics (disabled by default)
- **Data Integrity**: Thread-safe writes and session-bound predictions

---

### Medical Disclaimer
> ⚠️ **Important**: CureHelp+ is designed for informational purposes only and does not provide medical diagnosis. Always consult qualified healthcare professionals for medical advice and treatment. The predictions are based on machine learning models and should be used as supplementary information only.

---

## 🌟 Contributing

I welcome contributions from the community!

---

##  Quick Start

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Git

### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/asimhusain-ai/CureHelpPlus.git
   cd curehelp-plus
   ```

2. **Create and Activate a Virtual Environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate      # Windows
   source .venv/bin/activate     # macOS / Linux
   ```

3. **Install Dependencies**
   ```bash
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

4. **Prepare Datasets and Models**
   - Place chatbot CSVs inside `bot_data/`
   - Ensure trained model artifacts exist in `models/`
   - Optional: keep sample medical reports in `Sample_inputs/`

5. **Set Environment Variables (optional but recommended)**
   ```bash
   set CUREHELP_SECRET_KEY=change-me      # Windows PowerShell
   export CUREHELP_SECRET_KEY=change-me   # macOS / Linux
   ```

6. **Run the Flask Server**
   ```bash
   flask --app app run
   ```

7. **Access the Dashboard**
   - http://127.0.0.1:5000

### Container Deployment (Azure Container Apps)

1. **Build the Docker Image**
   ```bash
   docker build -t curehelplus:latest .
   ```

2. **Tag and Push to Azure Container Registry**
   ```bash
   az acr login --name cureacr
   docker tag curehelplus:latest cureacr.azurecr.io/curehelplus:latest
   docker push cureacr.azurecr.io/curehelplus:latest
   ```

3. **Deploy to Azure Container Apps**
   ```bash
   az containerapp up --name curehelplus --resource-group curehelplus --location central-india --image cureacr.azurecr.io/curehelplus:latest --target-port 5000 --ingress external --environment managedEnvironment-curehelplus-ade7
   ```

4. **Configure Secrets and Storage**
   - Set `CUREHELP_SECRET_KEY` and other env vars with `az containerapp secret set`
   - Mount persistent storage if the container needs to retain `user_profiles.json`

5. **Verify Deployment**
   - Use `az containerapp show --name curehelp-plus --resource-group curehelplus` to fetch the HTTPS endpoint
   - Confirm health with the `/` route and exercise prediction + chatbot flows
