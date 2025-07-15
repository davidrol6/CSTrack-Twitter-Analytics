# CSTrack Twitter Analytics

[![Documentación](https://img.shields.io/badge/Docs-CSTrack-blue)](https://davidrol6.github.io/CSTrack_Docs/#)
[![Built by DavidRol6 & FernanSLN](https://img.shields.io/badge/Built%20by-DavidRol6%20%26%20FernanSLN-green)](https://github.com/davidrol6/CSTrack)

An interactive visualization platform for Twitter data built with **Python**, **Dash**, and **Plotly**. This tool lets you generate real-time dashboards from a CSV (Pandas DataFrame) or connect to a **MongoDB** database for richer user insights, including **geospatial data**.

---

## 🚀 Features

- 📊 Interactive web interface built with Dash + Plotly
- ✅ Input options:
  - CSV file (Pandas DataFrame format)
  - MongoDB database for user-level metadata, geolocation, etc.
- 🌍 Geo-based and time-series visualizations
- 🐳 **Docker support** for easy deployment

---

## 🧱 Installation

### Option 1: Using Docker
```
bash
git clone https://github.com/davidrol6/CSTrack-Twitter-Analytics.git
cd CSTrack-Twitter-Analytics
docker build -t cstrack-twitter .
docker run -p 8050:8050 \
  -e CSV_PATH=/data/my_data.csv \
  -e MONGO_URI="mongodb://user:pass@host:27017/db" \
  -v /local/data:/data \
  cstrack-twitter
```  
🔧 Environment variables:

`CSV_PATH`: path to your CSV file

`MONGO_URI`: MongoDB connection URI

### Option 2: Manual setup
```
bash
git clone https://github.com/davidrol6/CSTrack-Twitter-Analytics.git
cd CSTrack-Twitter-Analytics
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
Then update the file config.py with your settings:
```
python

CSV_PATH = "/path/to/your_data.csv"
MONGO_URI = "mongodb://..."
MONGO_COLL = "collection_name"
```
Run the app locally:
```
bash
python app.py
```
Access the dashboard at: http://localhost:8050

📂 Repository Structure
```
CSTrack-Twitter-Analytics/
├── Dockerfile # Docker container setup
├── app.py # Main Dash app
├── config.py # App configuration (CSV/MongoDB paths)
├── requirements.txt # Python dependencies
├── visualizations/ # Plotly/Dash components and charts
│ ├── map_plot.py
│ └── time_series.py
└── docs/ # Optional documentation assets
```
📈 How It Works
Load your dataset from a CSV file or a live MongoDB connection.

MongoDB collections should include geospatial and user metadata (optional).

Available dashboards:

Tweet volume over time

User engagement metrics

Geolocation maps (if available)

Filtering options by user, date, hashtags, etc.

🧪 Example MongoDB Document
```
json
{
  "username": "davidrol6",
  "text": "...",
  "date": "2025-07-15T12:34:56Z",
  "location": {"type": "Point", "coordinates": [-3.8, 40.6]},
  "followers": 150
}
```
📋 Requirements
Python ≥ 3.8

Docker (optional)

MongoDB instance (optional)

CSV containing Twitter (X) data


📄 License
This project is under the GPL-3.0 License.

👥 Authors
DavidRol6 – github.com/davidrol6

FernanSLN – github.com/FernanSLN

