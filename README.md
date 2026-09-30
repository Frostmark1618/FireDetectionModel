# 🔥 FireDetectionModel

> A machine-learning based fire detection system combining computer vision with environmental monitoring.

This project explores an integrated approach to fire detection using **CNN-based image classification**, environmental sensors, an Arduino-based monitoring layer, and a Streamlit interface.

The system is designed to detect potential fire conditions and support timely monitoring and alerting.

---

## ✨ Features

- 🔥 CNN-based fire image classification
- 📷 Camera-based visual fire detection
- 🌡️ Temperature monitoring using DHT11
- 💨 Smoke monitoring using MQ2
- 🧠 Machine learning based detection
- 📊 Streamlit-based monitoring interface
- 📱 SMS alert integration using Twilio
- 🔌 Arduino-based sensor integration
- 📈 Fire and sensor data visualization

---

## 🧠 System Architecture

```text
Camera
   │
   ▼
Fire Image
   │
   ▼
CNN Model
   │
   ▼
Fire / No Fire
   │
   ├───────────────┐
   │               │
   ▼               ▼
Arduino         Streamlit
   │               │
   ├── DHT11       ├── Fire Data
   │               ├── Sensor Data
   └── MQ2         └── Monitoring
   │
   ▼
Environmental Data
   │
   ▼
Alert System
   │
   ▼
Twilio SMS
```

---

## 🔬 Machine Learning

The project uses a **Convolutional Neural Network (CNN)** for image-based fire detection.

The model processes fire-related visual patterns and classifies the input image according to the trained detection categories.

The system can combine the visual prediction with environmental signals such as:

- Temperature
- Smoke level
- Fire detection status

---

## 🌡️ Environmental Monitoring

The hardware layer uses an Arduino Uno together with environmental sensors.

| Component | Purpose |
|---|---|
| Arduino Uno | Sensor interface and control |
| DHT11 | Temperature monitoring |
| MQ2 | Smoke / gas sensing |
| Camera | Visual fire detection |

---

## 📊 Streamlit Application

The Streamlit interface provides a simple monitoring layer for the system.

It can display:

- Fire detection status
- Temperature readings
- Smoke levels
- Sensor information
- Fire-related monitoring data

---

## 📱 Alert System

The project includes **Twilio-based SMS alert integration** for fire detection events.

For security, credentials and recipient phone numbers must be configured privately.

**Never commit:**

- Twilio Account SID
- Twilio Auth Token
- Twilio phone numbers
- Personal recipient phone numbers
- Other API credentials

Example configuration:

```python
account_sid = "YOUR_ACCOUNT_SID"
auth_token = "YOUR_AUTH_TOKEN"
twilio_number = "YOUR_TWILIO_NUMBER"
recipient_number = "YOUR_RECIPIENT_NUMBER"
```

Use environment variables or another secure configuration method for real credentials.

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Machine Learning | TensorFlow |
| Computer Vision | CNN |
| Interface | Streamlit |
| Hardware | Arduino Uno |
| Sensors | DHT11, MQ2 |
| Communication | Twilio SMS |
| Data | SQLite / application storage |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.10
- Arduino IDE
- Arduino Uno
- DHT11 sensor
- MQ2 sensor
- Camera
- Required Python dependencies

### Clone the repository

```bash
git clone https://github.com/Frostmark1618/FireDetectionModel.git
cd FireDetectionModel
```

### Install dependencies

Install the packages required by the project environment.

```bash
pip install streamlit mysql-connector-python pyserial tensorflow numpy pandas opencv-python pyttsx3 twilio gdown
```

### Arduino Setup

1. Open the Arduino source file in Arduino IDE.
2. Connect the Arduino Uno.
3. Connect the required sensors.
4. Upload the Arduino program.
5. Ensure the serial connection is available to the application.

### Run the application

```bash
streamlit run W.py
```

The Streamlit application should then be available locally.

---

## 📂 Project Structure

The repository contains the machine-learning, Streamlit, and Arduino components required for the fire detection workflow.

A typical flow is:

```text
FireDetectionModel/
│
├── Machine Learning / CNN
├── Streamlit Application
├── Arduino / Sensor Code
├── Data / Model Assets
└── README.md
```

---

## 🎯 Use Cases

This project can serve as a prototype for:

- Fire detection systems
- Environmental monitoring
- IoT-based safety systems
- Computer-vision assisted monitoring
- Sensor + ML hybrid systems
- Real-time alerting workflows

---

## ⚠️ Limitations

This project should be treated as a **prototype / educational system**, not as a certified life-safety or fire-protection system.

Detection quality can depend on:

- Training data
- Lighting and camera conditions
- Model performance
- Sensor accuracy
- Hardware setup
- Environmental conditions
- Network and alert-service availability

Real-world deployment would require extensive validation, safety engineering, and domain-specific certification.

---

## 🔮 Future Improvements

- Improved CNN architecture and training pipeline
- Better fire / smoke classification
- Model evaluation metrics
- Real-time video inference
- Improved sensor fusion
- Historical monitoring dashboards
- Secure configuration management
- Containerized deployment
- Better testing and monitoring

---

## 👨‍💻 Author

**Riddhiman Adak**

B.Tech CSE (AI & ML)

[GitHub](https://github.com/Frostmark1618) •
[Portfolio](https://riddhi-s-vision.vercel.app) •
[LinkedIn](https://www.linkedin.com/in/riddhiman-adak-5b6336307/)

---

⭐ If you find this project interesting, consider starring the repository.
