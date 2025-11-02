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

If you want to run `scrape.py`, you must create a TMDB API Key and export that in to your environment

---

## Data Setup

This repository requires additional dataset files that are not tracked in Git due to their size. These files are stored on a shared Google Drive.

To download the required dataset(s), run the following script:
```bash
bash scripts/download_data.sh
```

Make sure `wget` is installed on your system. You may need to edit the script to include your own Google Drive file IDs if you're working with new or different data.

### Tip: Finding Google Drive File IDs

To download a file using its Drive ID:

1. Right-click the file in Google Drive → "Get link."
2. You will get a link like:
```
   https://drive.google.com/file/d/1A2B3C4D5E/view?usp=sharing
```

---

## Running `scrape.py`

The `scrape.py` script enriches MovieLens data with TMDB metadata and optionally downloads movie posters.

### 1. Export Your TMDB API Key

Create an API key on [TMDB](https://www.themoviedb.org/documentation/api) and export it to your environment:
```bash
export TMDB_API_KEY="your_tmdb_api_key"   # Mac/Linux
setx TMDB_API_KEY "your_tmdb_api_key"     # Windows (new shell required)
```

### 2. Run the Script

Basic usage (writes output CSV to `data/ml32m_tmdb_enriched.csv`):
```bash
python src/scrape.py
```
This will run the script with default arguments, but they are configurable. Remember to set a `--limit` for testing! See below:

**Optional arguments:**
```bash
python src/scrape.py --movielens-dir data/ml-32m         # path to MovieLens CSVs
python src/scrape.py --out data/enriched.csv             # output CSV path
python src/scrape.py --limit 1000                        # limit number of movies (for testing)
python src/scrape.py --download-images                   # download poster images
python src/scrape.py --poster-size w500                  # choose TMDB poster size
python src/scrape.py --concurrency 10                    # max concurrent TMDB requests
```

After running with `--download-images`, poster images will be saved to `data/posters/`.
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
