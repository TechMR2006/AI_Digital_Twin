# 🌊 Coastal City Digital Twin

> **An AI-powered 3D Digital Twin for coastal-city visualization, disaster simulation, flood-risk prediction, real-time weather monitoring, and 2D-to-3D reconstruction.**

![3D Coastal City](https://img.shields.io/badge/3D-Digital%20Twin-blue)
![Three.js](https://img.shields.io/badge/Three.js-3D-black)
![Python](https://img.shields.io/badge/Python-3.x-yellow)
![FastAPI](https://img.shields.io/badge/FastAPI-Backend-009688)
![Machine Learning](https://img.shields.io/badge/AI-ML-orange)
![OpenCV](https://img.shields.io/badge/OpenCV-Computer%20Vision-red)
![SQLite](https://img.shields.io/badge/Database-SQLite-blue)

## 📌 Overview

**Coastal City Digital Twin** is an interactive 3D simulation platform designed to model a coastal city and analyze the potential impact of environmental disasters such as flooding.

The system combines **3D visualization, computer vision, machine learning, real-time weather data, and AI-assisted 2D-to-3D reconstruction** to create an interactive digital representation of a coastal environment.

The platform allows users to visualize a simulated city, inspect buildings, simulate flood scenarios, calculate building vulnerability, view weather information, and reconstruct 3D city structures from 2D imagery.

The project was developed with a focus on **AI-powered disaster management and Earth intelligence**.

---

## 🚀 Key Features

### 🏙️ Interactive 3D Coastal City

The application provides a detailed real-time 3D coastal environment containing:

* Buildings
* Roads
* Vehicles
* Boats
* Bridges
* Lighthouse
* Parks
* Pedestrians
* Birds
* Coastal environment
* Dynamic environmental effects

The city can be explored interactively through the browser.

---

### 🌊 Flood Simulation

The system allows users to simulate different flood levels and observe their potential impact on the city.

The simulation can be used to:

* Increase simulated flood levels
* Identify vulnerable buildings
* Visualize flood-risk areas
* Analyze building vulnerability
* Compare different disaster scenarios

---

### 🤖 AI-Based Disaster Prediction

A machine-learning pipeline is integrated into the backend to estimate building vulnerability.

The system considers features such as:

* Building elevation
* Building height
* Distance from water
* Building type
* Simulated flood level

The ML pipeline combines:

* **XGBoost Regression**
* **Logistic Regression**
* **SHAP Explainability**

The system produces:

* Vulnerability score
* Collapse probability
* Feature-level explanations

This makes the prediction more interpretable instead of treating the model as a complete black box.

---

### 🧠 Explainable AI with SHAP

The project integrates **SHAP (SHapley Additive exPlanations)** to identify which features contribute to a building's predicted vulnerability.

For example, the system can analyze the contribution of:

```text
Effective Elevation
Building Height
Distance to Water
Building Type
```

This helps provide an explanation alongside the prediction.

---

### 📷 2D → 3D City Reconstruction

The backend provides an image-processing pipeline that accepts a 2D image and uses **OpenCV** to identify objects and contours.

The process includes:

```text
2D Image
   ↓
Image Decoding
   ↓
Grayscale Conversion
   ↓
Gaussian Blur
   ↓
Canny Edge Detection
   ↓
Contour Detection
   ↓
Object / Building Extraction
   ↓
3D World Coordinate Mapping
   ↓
3D Building Data
```

Detected structures are converted into approximate 3D building representations.

---

### 🏗️ Hunyuan3D-2 Integration

The Phase 3 implementation also includes integration with **Tencent Hunyuan3D-2** for image-to-3D generation.

The workflow is:

```text
Camera / Image
      ↓
Base64 Image
      ↓
FastAPI Backend
      ↓
Hunyuan3D-2
      ↓
3D GLB Model
      ↓
Local Model Storage
      ↓
3D Visualization
```

Generated `.glb` models can be served through the FastAPI backend.

---

### 🛰️ Interactive Satellite View

The application includes an interactive satellite-map interface using:

* Leaflet
* OpenStreetMap
* Satellite map tiles

The map interface provides an additional geographic perspective alongside the simulated 3D environment.

---

### 🌦️ Real-Time Weather Data

The backend connects to the **Open-Meteo API** to retrieve current weather information.

The weather system can provide data such as:

* Temperature
* Wind speed
* Wind direction
* Weather conditions

This allows environmental information to be incorporated into the digital-twin interface.

---

### 🌗 Day / Night Simulation

The 3D environment includes environmental lighting and day/night visualization to make the digital twin more immersive.

---

## 🧩 System Architecture

```text
                    ┌─────────────────────────┐
                    │       User / Browser    │
                    └────────────┬────────────┘
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │   Three.js Frontend     │
                    │                         │
                    │  • 3D City              │
                    │  • Flood Simulation     │
                    │  • Weather UI           │
                    │  • Satellite View       │
                    │  • User Interaction     │
                    └────────────┬────────────┘
                                 │
                           HTTP / REST
                                 │
                                 ▼
                    ┌─────────────────────────┐
                    │     FastAPI Backend     │
                    ├─────────────────────────┤
                    │                         │
                    │  City Reconstruction    │
                    │  Flood Prediction       │
                    │  Weather API            │
                    │  2D → 3D Generation     │
                    └──────┬──────┬───────────┘
                           │      │
              ┌────────────┘      └──────────────┐
              ▼                                   ▼
    ┌──────────────────┐                ┌──────────────────┐
    │ Machine Learning │                │ Computer Vision  │
    │                  │                │                  │
    │ XGBoost          │                │ OpenCV           │
    │ Logistic Reg.    │                │ Edge Detection   │
    │ SHAP             │                │ Contours         │
    └────────┬─────────┘                └──────────────────┘
             │
             ▼
    ┌──────────────────┐
    │ SQLite Database   │
    │                  │
    │ Building Data     │
    │ Vulnerability     │
    └──────────────────┘
```

---

# 🛠️ Technology Stack

## Frontend

* HTML5
* CSS3
* JavaScript
* Three.js
* Leaflet.js
* WebGL

## Backend

* Python
* FastAPI
* Uvicorn
* SQLAlchemy
* SQLite

## Artificial Intelligence / Machine Learning

* XGBoost
* Scikit-learn
* SHAP
* Logistic Regression

## Computer Vision

* OpenCV
* NumPy
* Canny Edge Detection
* Contour Detection

## 3D Generation

* Hunyuan3D-2
* Gradio Client
* GLB / 3D model pipeline

## External Data

* Open-Meteo
* OpenStreetMap
* Satellite map tiles

---

# 📂 Project Structure

```text
3D-real-time-simulatiom-main/
│
├── index.html
│
├── coastal_city_phase2.html
│
├── coastal_city_phase3.html
│
├── temp_module.mjs
│
├── .env.example
│
├── .gitignore
│
├── README.md
│
└── backend/
    │
    ├── main.py
    ├── main_phase3.py
    ├── ml_pipeline.py
    ├── database.py
    └── requirements.txt
```

---

# ⚙️ Installation

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/3D-real-time-simulatiom.git
```

```bash
cd 3D-real-time-simulatiom
```

---

# 🌐 Running the Frontend

The frontend is primarily implemented using HTML, CSS, JavaScript, and Three.js.

You can start a local web server using Python.

```bash
python -m http.server 8080
```

Then open:

```text
http://localhost:8080
```

You can also directly open:

```text
coastal_city_phase2.html
```

or:

```text
coastal_city_phase3.html
```

---

# 🐍 Running the Backend

Navigate to the backend directory:

```bash
cd backend
```

Create a virtual environment:

### Windows

```bash
python -m venv venv
```

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv
```

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start the FastAPI server:

```bash
uvicorn main:app --reload --port 9000
```

The API will be available at:

```text
http://localhost:9000
```

FastAPI documentation:

```text
http://localhost:9000/docs
```

---

# 🔌 API Endpoints

## `POST /api/reconstruct`

Accepts a Base64-encoded image and performs computer-vision-based object extraction.

### Input

```json
{
  "image": "data:image/jpeg;base64,..."
}
```

### Output

```json
{
  "status": "success",
  "message": "Successfully extracted objects from the image.",
  "buildings": []
}
```

---

## `POST /api/predict`

Calculates flood vulnerability for selected buildings.

### Input

```json
{
  "flood_level": 10,
  "building_ids": [
    "bld_12345678",
    "bld_87654321"
  ]
}
```

### Output

The API returns vulnerability predictions including:

```text
Vulnerability Score
Collapse Probability
SHAP Explanation
```

---

## `GET /api/weather`

Fetches current weather information from the Open-Meteo service.

```text
GET /api/weather
```

---

## `POST /api/camera-to-3d`

The Phase 3 backend accepts an image and sends it through the Hunyuan3D-2 image-to-3D pipeline.

```text
POST /api/camera-to-3d
```

The generated 3D model is returned as a `.glb` resource.

---

# 🧠 Machine Learning Pipeline

The disaster prediction system uses simulated training data for the current hackathon implementation.

### Input Features

```text
1. Elevation
2. Building Height
3. Distance to Water
4. Building Type
5. Flood Level
```

### Models

```text
                 Building Data
                      │
                      ▼
             Feature Preparation
                      │
              ┌───────┴────────┐
              ▼                ▼
         XGBoost          Logistic Regression
              │                │
              ▼                ▼
      Vulnerability       Collapse Probability
           Score
              │
              └───────┬────────┘
                      ▼
                   SHAP
                      │
                      ▼
             Explainable Output
```

> **Important:** The current ML implementation is a prototype/hackathon simulation. The training dataset is generated programmatically rather than being trained on a real-world historical disaster dataset.

---

# 🌊 Disaster Simulation Workflow

The overall simulation follows this workflow:

```text
OBSERVE
   ↓
Visualize the city and environmental data
   ↓
DETECT
   ↓
Identify buildings / areas potentially affected
   ↓
PREDICT
   ↓
Run flood-risk prediction models
   ↓
EXPLAIN
   ↓
Use SHAP to understand prediction factors
   ↓
SIMULATE
   ↓
Visualize the potential disaster scenario
   ↓
ANALYZE
   ↓
Compare building vulnerability and environmental conditions
```

---

# 🏗️ Development Phases

## Phase 1 — 3D City Foundation

Initial development focused on creating the interactive 3D coastal-city environment.

---

## Phase 2 — Disaster Intelligence

Phase 2 introduced:

* AI disaster prediction
* Flood simulation
* Weather integration
* Dynamic environment
* Vehicles
* Boats
* Lighthouse
* Pedestrians
* Birds
* Coastal infrastructure

---

## Phase 3 — Advanced Digital Twin

Phase 3 introduced improvements including:

* Grid-based city layout
* Structured road system
* Vehicles restricted to road lanes
* Properly bounded park zones
* 2D-to-3D reconstruction
* Hunyuan3D-2 integration
* Camera/image-to-3D workflow
* Enhanced digital-twin visualization

---

# 🔐 Environment Variables

An example environment configuration is provided in:

```text
.env.example
```

Potential integrations include:

```text
VITE_OPENWEATHER_API_KEY
VITE_WEATHERAPI_KEY
VITE_MAPBOX_ACCESS_TOKEN
OPEN_TOPOGRAPHY_API_KEY
TOMORROW_API_KEY
GOOGLE_MAPS_API_KEY
NASA_API_KEY
BACKEND_PORT
```

Copy the example configuration:

```bash
cp .env.example .env
```

On Windows, you can manually copy:

```text
.env.example → .env
```

Add the required API keys if you enable those integrations.

---

# 🎯 Use Cases

This platform can be extended for:

* 🌊 Flood-risk assessment
* 🏙️ Smart-city planning
* 🌍 Climate-risk analysis
* 🚨 Disaster management
* 🛰️ Earth observation
* 🏗️ Infrastructure monitoring
* 🧠 Explainable AI research
* 🌐 Digital-twin applications
* 🏫 Academic and hackathon demonstrations

---

# 🔮 Future Improvements

The current project provides a foundation for a more advanced Earth Intelligence platform.

Potential future improvements include:

### Real Satellite Data

Integrate real satellite imagery from sources such as:

* NASA
* ESA
* Sentinel
* Landsat

### Real Elevation Data

Replace simulated elevation with:

* DEM
* LiDAR
* OpenTopography
* Geographic elevation datasets

### Real Disaster Datasets

Train the prediction models using historical:

* Flood events
* Building damage data
* Rainfall
* River levels
* Terrain
* Satellite imagery

### Advanced AI Models

Future versions could incorporate:

* Deep learning
* Computer vision segmentation
* Vision Transformers
* Geospatial AI
* Time-series forecasting
* Multimodal AI

### Multi-Hazard Simulation

Extend beyond flooding to simulate:

```text
Flood
 ↓
Cyclone
 ↓
Storm Surge
 ↓
Landslide
 ↓
Earthquake
 ↓
Wildfire
```

---

# ⚠️ Current Limitations

This project is currently a **prototype / hackathon implementation**.

Some components use simulated or procedurally generated data rather than production-grade real-world datasets.

In particular:

* ML training data is currently synthetic.
* Building elevation is estimated rather than obtained from real GIS/DEM data.
* Distance to water is simplified for the demonstration.
* 2D-to-3D reconstruction is an approximation.
* Hunyuan3D-2 depends on external model/API availability.
* Weather data currently uses a sample coastal-city location.
* Disaster predictions should not be treated as real-world emergency predictions.

---

# 🤝 Contributing

Contributions are welcome.

### 1. Fork the repository

```bash
git fork YOUR_REPOSITORY_URL
```

### 2. Create a feature branch

```bash
git checkout -b feature/new-feature
```

### 3. Commit your changes

```bash
git add .
git commit -m "Add new feature"
```

### 4. Push the branch

```bash
git push origin feature/new-feature
```

### 5. Open a Pull Request

---

# 📜 License

This project is intended for educational, research, and hackathon purposes.

Add an appropriate open-source license such as **MIT License** if you want others to freely use and modify the project.

---

# 👨‍💻 Project

**Coastal City Digital Twin**

Built with:

```text
Three.js
FastAPI
Python
OpenCV
XGBoost
Scikit-learn
SHAP
SQLAlchemy
SQLite
Leaflet
Hunyuan3D-2
Open-Meteo
```

> **From visualization to prediction — turning a coastal city into an intelligent digital twin.** 🌊🏙️🤖
