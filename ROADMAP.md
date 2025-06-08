hoMap Project Roadmap

## 🛍️ Phase 1: MVP – Core Pipeline + Initial Sources

### 🌟 Goal

Detect and cluster repeated or near-duplicate comments posted across multiple domains within a short time window. Display them on a public-facing dashboard.

---

### 📅 Part 1: Data Ingestion – Initial Sites

| Site                   | Pros                                             | Notes                           |
| ---------------------- | ------------------------------------------------ | ------------------------------- |
| Daily Mail             | High comment volume, UK-focused                  | Likely noisy data               |
| The Guardian           | Civil comments, quality journalism               | Easy HTML structure             |
| RT.com                 | Known for coordinated propaganda campaigns       | Good for disinfo tests          |
| Yahoo News UK          | Massive volume, mixes AP/Reuters                 | Many bot-sounding replies       |
| Sky News / Independent | Mainstream UK press                              | May require more parsing effort |
| ZeroHedge.com          | Often cited in conspiracy or alt-finance circles | Unmoderated threads             |
| Telegraph              | Right-leaning UK news, popular comment sections  | Subscription wall possible      |

---

## 🧰 Phase 2: Pattern Detection & Clustering

### Tasks

* Normalize comment text (lowercase, strip punctuation, lemmatize)
* Encode using `sentence-transformers`
* Compare using cosine similarity (threshold > 0.9)
* Optionally filter by Levenshtein distance or token overlap
* Detect duplicates posted within time window across ≥2 domains
* Store detected clusters in DB (cluster\_id, texts, sites, timestamp spread)

---

## 🔧 Phase 3: Classification & Tagging

### Start Rule-Based:

* “Same/similar message across ≥4 sites in <2 hours” = high confidence
* Assign coordination tag + intent guess (e.g. "anti-NATO", "pro-Kremlin")
* Confidence scoring = based on site count, time spread, similarity strength

### Future:

* ML classifier using comment metadata (length, origin, similarity, site diversity)
* Optional: LDA/BERTopic to auto-tag clusters with themes

---

## 🚀 Phase 4: Backend API + Dashboard

### Backend (FastAPI):

* `/clusters/latest` – list recent flagged clusters
* `/cluster/{id}` – metadata + comments in cluster
* `/comment/{id}` – detail view

### Frontend:

* Display clusters in card/table format
* Sort by confidence, size, time
* Timeline visualization of when/where it appeared
* Option to report or tag clusters (optional moderation system)

---

## 🚧 Phase 5: Public Tools & Alerting

* Daily digest post: “Top 5 coordinated clusters of June 8”
* Telegram/Discord bot for live alerts
* API access for researchers, journalists
* Public vote/flag system like Reddit

---

## ✨ Stretch Goals

* Realtime detection & stream processing
* Bot account clustering via username/IP/time correlation
* Influence campaign timeline builder
* Collaboration with OSINT projects

