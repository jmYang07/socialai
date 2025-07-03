# Setup and Installation Guide

## 1. Development Environment Setup

### Step 1: Unzip the Project
```bash
unzip flask_app.zip -d flask_app
cd flask_app
```

### Step 2: (Optional) Create Virtual Environment
```bash
conda create -n flask_ib_demo python=3.11 -y
conda activate flask_ib_demo
```

---

## 2. Install Dependencies

### Step 3: Install Python Packages
```bash
pip install -r requirements.txt
```
If `requirements.txt` is not present, manually install:
```bash
pip install flask flask_sqlalchemy flask_login yfinance pandas plotly ib_insync
```

---

## 3. IB TWS API Setup

### Step 4: Install and Run IB TWS
- Download: https://www.interactivebrokers.com/en/index.php?f=16040
- Log in using a **demo account**

### Step 5: Enable API Access in TWS
- Navigate to: `Edit > Global Configuration > API > Settings`
- Enable:
  - ✅ "Enable ActiveX and Socket Clients"
  - ✅ "Allow connections from localhost"
- Confirm default port is set to `7497`

---

## 4. Run the Application Locally

### Step 6: Initialize the Database and Benchmark
```bash
python JamieYang0702_ib_flask_setup.py --db_path ./JamieYang0702_ib.db --log_path ./JamieYang0702_ib.log --benchmark ^GSPC
```

### Step 7: Start the Flask Web App
```bash
python JamieYang0702_flask_backend.py --db_path ./JamieYang0702_ib.db
```

### Step 8: Visit the App in Browser
Open: [http://127.0.0.1:5000](http://127.0.0.1:5000)
