# 📱 Road Roughness Prediction Using SmartRoadSense Data and Machine Learning

This project leverages **smartphone-based vibration data** from the [SmartRoadSense](http://smartroadsense.it/) open project to estimate **road surface roughness** using machine learning. A **Random Forest Regressor** model is trained on GPS, road classification, timestamp, and sensor precision data to predict a proxy for the **International Roughness Index (IRI)**.

---

## 📊 Business Use Case

### 🚧 Problem
Manual road quality inspection is expensive, slow, and infrequent. Cities lack scalable solutions to monitor road wear in real time.

### 🎯 Solution
We use smartphone sensors already in drivers' pockets to crowdsource vibration and GPS data, and apply machine learning to predict road roughness automatically and continuously.

### 👥 Target Users
- **Municipal transportation departments**
- **Logistics & fleet management companies**
- **Smart city planning initiatives**
- **Autonomous vehicle infrastructure planners**

---

## 🗃️ Dataset Description

**Source**: [SmartRoadSense Project](http://smartroadsense.it/)

**Sample Fields Used**:

| Column       | Description                                           |
|--------------|-------------------------------------------------------|
| `latitude`   | GPS latitude                                           |
| `longitude`  | GPS longitude                                          |
| `ppe`        | Position Precision Error from GPS                     |
| `osm_id`     | OpenStreetMap road identifier                         |
| `highway`    | Type of road (e.g., motorway, residential, etc.)      |
| `quality`    | Estimated road quality score (proxy for IRI)          |
| `passengers` | Number of passengers in the vehicle                   |
| `updated_at` | Timestamp of the sample collection                    |

---

## 🤖 Machine Learning Model

- **Model**: Random Forest Regressor (`scikit-learn`)
- **Features Used**:
  - Geolocation: `latitude`, `longitude`
  - Sensor precision: `ppe`
  - Road classification: encoded `highway`
  - Time features: `hour`, `minute`, `second` extracted from `updated_at`
  - Passenger load: `passengers`
- **Target**: `quality` (proxy for IRI)

### 📈 Evaluation Metrics
- **Mean Absolute Error (MAE)**
- **Root Mean Squared Error (RMSE)**
- **R² Score**

### 🧠 Feature Importance Plot
The model includes a bar plot showing which features contributed most to roughness prediction.

---

## 🛠️ How to Run

### 📦 Requirements

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
