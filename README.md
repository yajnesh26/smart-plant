# 🌱 Smart Plant Monitoring System

An IoT-based Smart Plant Monitoring System that collects **temperature**, **soil moisture**, and **light intensity** data using **MQTT**, stores it in **SQLite**, and visualizes real-time data and historical trends through a **Flask + Chart.js** web dashboard.

---

## 🚀 Features

- Real-time plant monitoring dashboard
- MQTT-based sensor data communication
- Historical data visualization with live graphs
- REST APIs for latest and historical sensor data
- Lightweight SQLite database storage
- Sensor simulator for testing without hardware
- Responsive and simple UI

---

## 🛠️ Tech Stack

### Backend
- Python 3.x
- Flask
- SQLite
- MQTT (paho-mqtt)
- Flask-CORS

### Frontend
- HTML5
- CSS3
- JavaScript
- Chart.js

### Communication
- MQTT Protocol
- Public Broker: `broker.hivemq.com`

---

## 🗂️ Project Structure

```
.
├── app.py                  # Flask app + MQTT subscriber
├── sensor_simulator.py     # Simulates IoT sensor data
├── requirements.txt        # Python dependencies
├── data.db                 # SQLite database (auto-created)
│
├── templates/
│   └── index.html          # Dashboard UI
│
└── README.md
```

---

## ✅ Prerequisites

- Python 3.8 or higher
- Internet connection (for MQTT broker & CDN)
- (Optional) Python virtual environment

---

## 📦 Installation

Create a virtual environment (recommended):

```bash
python -m venv venv
```

Activate it:

**Windows**
```bash
venv\Scripts\activate
```

**Linux / macOS**
```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## ⚙️ Configuration

Edit the following values in `app.py` if needed:

```python
DB_FILE = "data.db"
BROKER = "broker.hivemq.com"
PORT = 1883
TOPIC = "smartplant/device1"
```

---

## ▶️ Running the Application

### 1️⃣ Start the Flask Server

```bash
python app.py
```

Server runs at:

```
http://localhost:5000
```

---

### 2️⃣ Run Sensor Simulator (Optional)

To simulate sensor data without actual hardware:

```bash
python sensor_simulator.py
```

Publishes data every **5 seconds**.

---

## 🌐 Web Dashboard

Open a browser and visit:

```
http://localhost:5000/
```

### Dashboard Displays:
- Current temperature (°C)
- Soil moisture (%)
- Light intensity (lux)
- Time-series charts for each parameter
- Last updated timestamp

---

## 🔗 API Endpoints

### Get Latest Sensor Reading
```
GET /api/latest
```

Example Response:
```json
{
  "status": "ok",
  "data": {
    "timestamp": "2025-12-05 11:22:33",
    "temperature": 26.4,
    "moisture": 58.2,
    "light": 420.5
  }
}
```

---

### Get Sensor History
```
GET /api/history?limit=100
```

- `limit`: Number of previous records (default: 100)

---

## 🧾 MQTT Payload Format

Published to topic:

```
smartplant/device1
```

```json
{
  "timestamp": "2025-12-05 11:22:33",
  "temperature": 25.1,
  "moisture": 47.9,
  "light": 312.4
}
```

If timestamp is missing, the server automatically assigns one.

---

## 🧠 System Workflow

1. Sensor (or simulator) publishes data via MQTT
2. Flask backend subscribes to topic and receives data
3. Data is stored in SQLite database
4. Dashboard fetches data using REST APIs
5. Chart.js visualizes live and historical data

---

## ⚠️ Notes

- Uses a **public MQTT broker**; suitable only for development and academic use
- SQLite database is lightweight and auto-created
- CORS enabled for ease of development
- Charts auto-refresh every few seconds

---

## 🚧 Future Enhancements

- Mobile app support
- Plant health recommendations
- Threshold-based alerts (SMS / Email)
- Cloud database integration
- Secure MQTT with TLS
- Automated irrigation control

---

## 📚 Academic Use

This project is suitable for:
- IoT Mini Project
- DBMS Mini Project
- Python / Flask based applications
- Engineering laboratory and final-year demos

---

## 🧑‍💻 Author

Developed as an academic IoT mini project.

---

## 📄 License

MIT License
