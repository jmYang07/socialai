# Setup and Installation Guide

This guide walks you through setting up the development environment, installing dependencies, configuring the IB TWS API, and running the Flask web application locally.

---

## 1. Development Environment Setup

### Step 1: Extract the Project Files
Download and unzip the project:
```bash
unzip flask_app.zip -d flask_app
cd flask_app
```

### Step 2: (Optional but Recommended) Create a Virtual Environment
Using Conda:
```bash
conda create -n flask_ib_demo python=3.11 -y
conda activate flask_ib_demo
```

Or using `venv`:
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

---

## 2. Install Python Dependencies

### Step 3: Install All Required Packages
If `requirements.txt` is provided:
```bash
pip install -r requirements.txt
```

Otherwise, manually install required packages:
```bash
pip install flask flask_sqlalchemy flask_login yfinance pandas plotly ib_insync
```

---

## 3. Configure IB Trader Workstation (TWS)

### Step 4: Download & Launch TWS
Download TWS: https://www.interactivebrokers.com/en/index.php?f=16040  
Login using a **demo account** (real accounts are not permitted).

### Step 5: Enable API Access in TWS
Go to:
```
Edit > Global Configuration > API > Settings
```
Make sure to check:
- “Enable ActiveX and Socket Clients”
- “Allow connections from localhost only”
- Port: **7497** (default and required)

Keep TWS running while using the app.

---

## 4. Initialize Database and Fetch Benchmark Data

### Step 6: Run Initialization Script
This script:
- Creates SQLite database
- Fetches initial account and benchmark data (e.g., S&P500 via Yahoo Finance)

Run:
```bash
python JamieYang0702_ib_flask_setup.py \
  --db_path ./JamieYang0702_ib.db \
  --log_path ./JamieYang0702_ib.log \
  --benchmark ^GSPC
```

Arguments:
- `--db_path`: Path to the SQLite database file
- `--log_path`: Path to save log output
- `--benchmark`: Ticker symbol (e.g., ^GSPC for S&P 500)

---

## 5. Run Flask Web Application Locally

### Step 7: Launch the Web Server
```bash
python JamieYang0702_flask_backend.py --db_path ./JamieYang0702_ib.db
```

If successful, you'll see:
```
* Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

---

## Step 8: Open in Browser

Open your browser and go to:
```
http://127.0.0.1:5000
```

---

## Setup Complete!

You can now register a new account, log in, and view live IB account data and benchmark comparisons from your local web dashboard.
