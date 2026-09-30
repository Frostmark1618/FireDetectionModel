# 🔥 FireDetectionModel

> A machine-learning based fire detection system combining computer vision, environmental sensing, and real-time monitoring.

This project explores an integrated fire detection workflow using **CNN-based image classification**, environmental sensor data, an Arduino-based hardware layer, and a Streamlit monitoring application.

The system combines visual and environmental signals to identify potential fire conditions and support alerting.

---

## ✨ Features

- 🔥 CNN-based fire image classification
- 📷 Camera-based visual fire detection
- 🌡️ Temperature and humidity monitoring using DHT11
- 💨 Analog environmental/smoke sensing
- 🧠 Machine-learning based fire prediction
- 🔀 Sensor + camera based prediction workflow
- 📊 Streamlit monitoring interface
- 📱 SMS alert integration using Twilio
- 🔌 Arduino-based sensor integration
- 🗄️ SQLite-based data storage
- 🔊 Text-to-speech alerts
- 📈 Sensor and fire-data monitoring

---

## 🧠 System Architecture

```text
                    ┌──────────────────┐
                    │      Camera      │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   CNN Model      │
                    │   model.h5       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Visual Prediction│
                    └────────┬─────────┘
                             │
                             │
        ┌────────────────────┴────────────────────┐
        │                                         │
        ▼                                         ▼
┌──────────────────┐                    ┌──────────────────┐
│     Arduino      │                    │    Streamlit     │
│                  │                    │   Application    │
│ DHT11 + Sensor   │                    │                  │
└────────┬─────────┘                    └────────┬─────────┘
         │                                       │
         ▼                                       ▼
┌──────────────────┐                    ┌──────────────────┐
│ Temperature /    │                    │ Sensor + Camera  │
│ Sensor Data      │───────────────────▶│ Prediction Logic │
└──────────────────┘                    └────────┬─────────┘
                                                 │
                                                 ▼
                                      ┌────────────────────┐
                                      │ Fire / No-Fire     │
                                      │ Decision           │
                                      └─────────┬──────────┘
                                                │
                           ┌────────────────────┴──────────────┐
                           │                                   │
                           ▼                                   ▼
                  ┌──────────────────┐               ┌──────────────────┐
                  │ SQLite Database  │               │ Twilio SMS Alert │
                  └──────────────────┘               └──────────────────┘
```

---

## 🤖 Machine Learning

The project uses a trained **TensorFlow/Keras CNN model** for image-based fire detection.

The trained model is stored as:

```text
model.h5
```

The application processes an input image, prepares it for the trained model, and generates a fire-related prediction.

A second machine-learning component is also included:

```text
IFELSEModelPartNew.pkl
```

This model is used as part of the prediction workflow combining:

- Camera prediction
- Smoke/sensor value
- Temperature value

---

## 📷 Computer Vision Pipeline

The image detection workflow follows this general process:

```text
Camera / Image
      │
      ▼
Image Loading
      │
      ▼
Resize to Model Input
      │
      ▼
Pixel Normalization
      │
      ▼
CNN Inference
      │
      ▼
Prediction Score
```

The application uses OpenCV and TensorFlow/Keras for the computer-vision workflow.

---

## 🌡️ Hardware & Environmental Monitoring

The hardware layer uses an **Arduino Uno** with a DHT11 sensor and an analog sensor input.

| Component | Purpose |
|---|---|
| Arduino Uno | Hardware interface |
| DHT11 | Temperature and humidity |
| Analog sensor | Environmental/smoke-related signal |
| LED | Local hardware indication |
| Camera | Visual fire detection |

The Arduino communicates with the Python application through a **serial connection at 9600 baud**.

---

## 📊 Streamlit Application

The main application is:

```text
Fire Detection Project/app.py
```

The Streamlit interface provides the application layer for:

- Fire detection
- Sensor monitoring
- Camera-based prediction
- Database interaction
- Alerting
- Text-to-speech feedback

The application also contains database functionality for storing sensor and fire-related information.

---

## 🗄️ Data Storage

The application uses **SQLite** for local data storage.

The repository contains SQLite-related files for storing and working with sensor/fire data.

The application maintains tables for information such as:

- Smoke values
- Temperature
- Fire status
- Timestamped sensor readings

---

## 📱 Alert System

The project includes **Twilio-based SMS alert functionality**.

When the system detects a potential fire condition, the application can send alert messages through Twilio.

### 🔐 Security

Credentials and personal recipient numbers **must not be committed to a public repository**.

Use environment variables or another secure configuration mechanism for production use.

Example:

```python
account_sid = "YOUR_ACCOUNT_SID"
auth_token = "YOUR_AUTH_TOKEN"
twilio_number = "YOUR_TWILIO_NUMBER"
recipient_number = "YOUR_RECIPIENT_NUMBER"
```

Never commit:

- Twilio Account SID
- Twilio Auth Token
- Personal phone numbers
- API keys
- Passwords
- Other private credentials

---

## 🔊 Text-to-Speech

The application also includes a text-to-speech component using `pyttsx3`.

This can provide local audio feedback when important events occur.

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| Programming | Python |
| Machine Learning | TensorFlow / Keras |
| Computer Vision | OpenCV |
| Interface | Streamlit |
| Hardware | Arduino Uno |
| Sensors | DHT11 + Analog Sensor |
| Communication | PySerial |
| Alerts | Twilio |
| Database | SQLite |
| Audio | pyttsx3 |
| Data Processing | NumPy, Pandas |
| Model Serialization | Joblib |

---

## 📁 Project Structure

```text
FireDetectionModel/
│
├── Fire Detection Project/
│   │
│   ├── app.py
│   ├── model.h5
│   ├── IFELSEModelPartNew.pkl
│   ├── requirements.txt
│   │
│   ├── ArduinoCode/
│   │   └── ArduinoCode.ino
│   │
│   ├── temp_db.sqlite
│   ├── temp_db_converted.sqlite
│   └── temp_db_converted.sql
│
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/Frostmark1618/FireDetectionModel.git
cd FireDetectionModel
```

### 2. Enter the project directory

```bash
cd "Fire Detection Project"
```

### 3. Install dependencies

The repository includes a `requirements.txt` file.

```bash
pip install -r requirements.txt
```

### 4. Arduino Setup

1. Open `ArduinoCode/ArduinoCode.ino` in Arduino IDE.
2. Connect the Arduino Uno.
3. Connect the DHT11 and analog sensor.
4. Upload the Arduino program.
5. Connect the Arduino to the computer through USB.
6. Make sure the serial connection is available.

### 5. Run the application

```bash
streamlit run app.py
```

The Streamlit application should then open locally in your browser.

---

## 🔄 Detection Workflow

```text
Image + Sensor Data
        │
        ▼
┌─────────────────────┐
│ Camera CNN Model    │
└──────────┬──────────┘
           │
           ▼
    Camera Prediction
           │
           │
           ├──────────────┐
           │              │
           ▼              ▼
      Smoke Value   Temperature
           │              │
           └──────┬───────┘
                  ▼
        Prediction Model
                  │
                  ▼
          Fire Probability
                  │
                  ▼
       ┌──────────┴──────────┐
       │                     │
       ▼                     ▼
   Database              Alert System
       │                     │
       ▼                     ▼
 Sensor History          Twilio SMS
```

---

## 🎯 Possible Use Cases

This project can serve as a prototype for:

- 🔥 Fire detection systems
- 📷 Computer-vision based monitoring
- 🌡️ Environmental monitoring
- 🤖 ML-assisted safety systems
- 🔌 IoT-style sensor systems
- 📱 Automated alerting workflows
- 🧪 Academic machine-learning projects

---

## ⚠️ Limitations

This project should be considered a **prototype / educational system**, not a certified fire-protection or life-safety system.

Real-world performance can depend on:

- Training data quality
- Camera conditions
- Lighting
- Sensor accuracy
- Hardware configuration
- Model performance
- Serial communication
- Network availability
- SMS service availability

A production safety system would require extensive testing, validation, fail-safe design, and appropriate certification.

---

## 🔮 Future Improvements

- Improve CNN architecture and training pipeline
- Add formal model evaluation metrics
- Improve fire/smoke classification
- Add real-time video inference
- Improve sensor fusion
- Add historical analytics
- Add stronger anomaly detection
- Improve configuration management
- Add automated testing
- Add containerized deployment
- Improve monitoring and observability
- Build a more robust production architecture

---

## 👨‍💻 Author

**Riddhiman Adak**

B.Tech CSE (AI & ML)

[GitHub](https://github.com/Frostmark1618) •
[Portfolio](https://riddhi-s-vision.vercel.app) •
[LinkedIn](https://www.linkedin.com/in/riddhiman-adak-5b6336307/)

---

⭐ If you find this project interesting, consider starring the repository.
