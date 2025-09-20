# 🛰 Satellite Visibility Prediction – IIT Madras

Predicting satellite visibility windows from ground stations using orbital data and machine learning. This project leverages **Skyfield**, **Python**, and **Random Forest regression** to estimate how long a satellite remains visible from a given location.

---

## 🚀 Project Overview

Satellites constantly orbit the Earth, but ground stations can only communicate with them during specific **“visibility windows.”** Accurate prediction of these windows is crucial for:

- Communication
- Remote sensing
- Scientific experiments

**Project Goals:**

1. Generate a comprehensive dataset of satellite passes over **IIT Madras** (12.9916° N, 80.2337° E).  
2. Preprocess and clean the dataset for machine learning.  
3. Train regression models (**Random Forest** and **Neural Networks**) to predict pass durations.  
4. Explore bonus features:
   - Visualizing satellite pass arcs  
   - Identifying **good passes** for communication  
   - Deploying a tool to estimate visibility windows from TLE data  

---

## 📦 Dataset

The dataset was generated using **NORAD TLE data** and **Skyfield simulations**, focusing on key satellites:

- ISS (ZARYA)  
- CSS (TIANHE, WENTIAN, MENGTIAN)  
- SOYUZ-MS 27  
- Shenzhou-20  
- Crew Dragon 11  

### Features

| Column | Description |
|--------|-------------|
| Satellite | Name of the satellite |
| Time | Timestamp of the observation (UTC) |
| Altitude | Altitude above the horizon (degrees) |
| Azimuth | Azimuth angle (degrees) |
| Distance_km | Distance from the ground station (km) |
| Pass_Duration_min | Duration of the satellite pass (minutes) |

**Dataset size:** 18,077 entries across multiple satellites over several days.

---

## 🧹 Data Cleaning & Preprocessing

- **Handling Missing Values:** Filled missing `Pass_Duration_min` with `0`.  
- **Datetime Standardization:** Converted `Time` to UTC-aware datetime objects.  
- **Feature Selection:** Retained numeric features relevant for regression (`Altitude`, `Azimuth`, `Distance_km`, `Pass_Duration_min`).  
- **Scaling & Normalization:** Optional normalization applied for neural network training.  

---

## 🏗 Model Training

### Random Forest Regression

- Trained on cleaned dataset.  
- **Performance:**  
  - MSE: 0.81  
  - R²: 0.88  

### Neural Network Regression

- Sequential model with 3 hidden layers (128 → 64 → 32 units) and dropout for regularization.  
- **Performance:**  
  - MSE: 1.00  
  - R²: 0.86  

**Chosen model:** Random Forest (better interpretability and accuracy).

---

## 📊 Bonus Features

1. **Satellite Pass Visualization**  
   - 3D plots of pass arcs from the ground station.  
   - Multiple satellites visualized simultaneously.  

2. **Good Pass Prediction**  
   - Identifies passes with high altitude and long duration for **optimal communication**.  

3. **Visibility Window Tool**  
   - Accepts TLE lines and a location to compute predicted pass times.  
   - Can be deployed as a standalone utility for planning communications.  

---

## ⚡ Technologies Used

- Python 3.12  
- Pandas, NumPy, Matplotlib, Seaborn  
- Scikit-learn (Random Forest)  
- Keras (Neural Network)  
- Skyfield (Orbital simulations)  
- tqdm (Progress bars)  

---

## 📍 About IIT Madras

This project uses **IIT Madras** as the primary ground station, showcasing how advanced ML techniques can support **space communication and research** from a premier Indian institute.  
