# 🛣️ Automated Road Damage Detection & Assessment System (YOLOv11m + Azure)

An end-to-end Computer Vision and MLOps system for detecting, classifying, and assessing road surface damages (**Longitudinal Cracks**, **Transverse Cracks**, **Alligator Cracks**, and **Potholes**) across images, recorded videos, and live camera streams.

---

## 🌐 Live Deployment Links
* **Interactive Web Dashboard (Frontend):** [Live Demo on GitHub Pages](https://mohameddokun.github.io/Road_Damage_Detector/)
* **REST API & Swagger Docs (Backend):** [FastAPI on Azure Container Apps](https://road-damage-api.lemoncoast-6fffcba2.uaenorth.azurecontainerapps.io/docs)

---

## 🏗️ System Architecture
1. **Deep Learning & Preprocessing:** Fine-tuned **YOLOv11m** (`imgsz=800`) enhanced with **CLAHE** (Contrast Limited Adaptive Histogram Equalization) and **Test-Time Augmentation (TTA)** to improve low-contrast crack and pothole visibility.
2. **Experiment Tracking:** All training iterations and class-level progressions tracked and logged via **MLflow**.
3. **Backend Inference Engine:** Built with **FastAPI** and **OpenCV**, containerized using **Docker**, and deployed on **Microsoft Azure Container Apps** (4 GB RAM).
4. **Frontend Dashboard:** Responsive web application hosted on **GitHub Pages** supporting image upload, video analysis, live camera detection, real-time FPS tracking, and road condition classification (`Good`, `Fair`, `Poor`).

---

## 📊 Model Progression & Performance (MLflow Results)
Trained and evaluated on the **RDD2022** dataset across 4 road damage classes:

| Model Version | Key Enhancements | mAP@50 (Overall) | D00 (Longitudinal) | D10 (Transverse) | D20 (Alligator) | D40 (Pothole) |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **YOLOv11n** | Baseline (`640px`) | 57.50% | 58.10% | 55.40% | 73.80% | 42.70% |
| **YOLOv11s** | Scaled Architecture (`640px`) | 63.20% | 62.50% | 60.80% | 76.90% | 52.60% |
| **YOLOv11m (Final)** | **CLAHE + Class Balancing + `800px` + TTA** | **68.85%** | **66.40%** | **65.20%** | **79.90%** | **79.89%** |

---

## 📂 Repository Structure
```text
├── backend/              # FastAPI server, YOLO inference pipeline (CLAHE), & Dockerfile
├── frontend/             # Web dashboard UI (HTML, CSS, JavaScript) linked to Azure API
├── training_and_mlflow/  # Model training notebooks, MLflow logging scripts, & comparison charts
├── demo_results/         # Real-world inference screenshots on unseen test images
└── README.md             # Project documentation and deployment guide
```

---

## 🚀 Run Locally (Optional)
### 1. Backend (FastAPI)
```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --host 0.0.0.0 --port 8000
```
### 2. Frontend
Open `frontend/index.html` directly in any browser or serve it via Live Server.