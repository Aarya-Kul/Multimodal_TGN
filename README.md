# Multimodal_TGN

This repository contains the codebase for training and experimenting Multimodal Temporal Graph Networks for Sequential Recommendations (MM-TGN). It includes data processing scripts and environment setup details

---

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/Multimodal_TGN.git
cd Multimodal_TGN
```

### 2. Create and Activate Virtual Environment

It is recommended to use a virtual environment:
```bash
python3 -m venv env
source env/bin/activate  # On Mac/Linux
env\Scripts\activate     # On Windows
```

Install required dependencies:
```bash
pip install -r requirements.txt
```

Make sure your API keys and sensitive files are stored in a `.env` file which is already gitignored.

---

## 📂 Data Setup

This repository requires additional dataset files that are not tracked in Git due to their size. These files are stored on Google Drive.

To download the required dataset(s), run the following script:
```bash
bash scripts/download_data.sh
```

Make sure `wget` is installed on your system. You may need to edit the script to include your own Google Drive file IDs if you're working with new or different data.

### 🧠 Tip: Finding Google Drive File IDs

To download a file using its Drive ID:

1. Right-click the file in Google Drive → "Get link."
2. You will get a link like:
```
   https://drive.google.com/file/d/1A2B3C4D5E/view?usp=sharing
```

---

## Project Structure
```
Multimodal_TGN/
├── data/                    # Downloaded data will be placed here
├── scripts/
│   ├── download_data.sh     # Script to download data from Drive
├── src/
│   ├── scrape.py                 # Source code
├── .gitignore               
├── requirements.txt
└── README.md
```

---

## .gitignore

The following items are excluded from version control:
```
apikey
env
data/*
!data/.gitkeep
```