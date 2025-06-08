#EchoMap 🗺️
**A transparency tool that detects and displays coordinated comment campaigns (e.g., troll farms, disinfo).**

## 🔍 What It Does
- Scrapes comments from news sites, forums, and social media.
- Detects duplicated or near-duplicated messages across sites.
- Flags clusters of likely coordinated posts.
- Displays results on a public dashboard — no censorship, just visibility.

## 🚀 MVP Stack
- Python, FastAPI, sentence-transformers, PostgreSQL (or SQLite for now)
- Frontend: HTML/React
- Deployment: Docker + Render/Railway

## 🛠️ Setup
```bash
git clone git@github.com:Mo0-Mo0/EchoMap.git
cd EchoMap
pip install -r requirements.txt


## Directory 

echomap/
├── scraper/
│   ├── reddit_scraper.py
│   ├── guardian_scraper.py
│   └── yahoo_scraper.py
├── detection/
│   ├── detect_duplicates.py
│   ├── clustering.py
│   └── utils.py
├── backend/
│   ├── main.py (FastAPI)
│   └── db.py (SQLAlchemy models)
├── frontend/
│   └── index.html (or Next.js)
├── data/
│   └── comments.db / comments.csv
├── config/
│   └── settings.py
├── scheduler/
│   └── job_runner.py (APScheduler/cron)
└── Dockerfile

