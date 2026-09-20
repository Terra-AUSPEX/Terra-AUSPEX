<div align="center">

# 🛰️ TERRA AUSPEX

### *Cutting through clouds. Revealing the Earth beneath.*

![Status](https://img.shields.io/badge/status-in%20development-blueviolet?style=for-the-badge)
![Python](https://img.shields.io/badge/python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PyTorch](https://img.shields.io/badge/PyTorch-DL%20Model-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Satellite](https://img.shields.io/badge/data-Sentinel--2-00A3E0?style=for-the-badge&logo=satellite&logoColor=white)
![License](https://img.shields.io/badge/license-TBD-lightgrey?style=for-the-badge)

*An interactive Earth-observation platform that uses deep learning to see through cloud cover — and shows you what's really happening on the ground.*

</div>


## 🌍 What Is This?

Optical satellites like **Sentinel-2** photograph the Earth on a regular cycle — but on average, **58–66% of the planet is obscured by cloud cover** at any given moment. That means huge blind spots in monitoring crops, disasters, and land change, exactly when it matters most.

**Terra Auspex** is a full-stack platform that:

```
🌐  Explore Earth on an interactive map
   ↓
📡  Pull real Sentinel-2 satellite imagery for any region
   ↓
🧠  Run a deep learning model to strip away the clouds
   ↓
🌱  Reveal insights hidden underneath — starting with vegetation health (NDVI)
```

This project is being built across **two semesters**:

| | Focus |
|---|---|
| 🎓 **Minor Project** *(this sem)* | Core cloud-removal pipeline · interactive map frontend · NDVI overlay |
| 🚀 **Major Project** *(next sem)* | SAR-optical fusion · anytime temporal querying · disaster & crop-anomaly detection |

---

## 🎯 Why This Matters

Cloud removal research today splits into two camps — and both have a gap:

| Approach | The Problem |
|---|---|
| 🖼️ **Single-image methods** *(dark-channel priors, cloud matting)* | Can't recover anything under **thick, opaque clouds** — there's simply no signal left to reconstruct |
| ⏱️ **Time-series methods** | Use multiple observations over time to fill gaps well, but exist mostly as **research code**, not usable products |

**Terra Auspex bridges that gap** — taking proven time-series reconstruction research and turning it into an actual, interactive tool anyone can use to look at any point on Earth, cloud-free.

---

## 🏗️ How It Works

```
┌──────────────────────────────────────────────────────────┐
│  🌐  FRONTEND                                              │
│  Interactive globe/map (Leaflet / Mapbox / CesiumJS)       │
│  → user selects a region on Earth                          │
└──────────────────────────┬───────────────────────────────┘
                            │
┌──────────────────────────▼───────────────────────────────┐
│  📡  INGESTION LAYER                                       │
│  Sentinel-2 imagery via Sentinel Hub / Earth Engine /      │
│  AWS Open Data                                             │
└──────────────────────────┬───────────────────────────────┘
                            │
┌──────────────────────────▼───────────────────────────────┐
│  🧠  CLOUD REMOVAL MODEL                                    │
│  Sequence-to-sequence deep learning model                  │
│  (CNN spatial encoder + temporal attention + decoder)      │
└──────────────────────────┬───────────────────────────────┘
                            │
┌──────────────────────────▼───────────────────────────────┐
│  🌱  ANALYSIS & OUTPUT LAYER                                │
│  NDVI overlay (vegetation/crop health)                     │
│  ⏭ next sem: disaster & anomaly detection                  │
└──────────────────────────┬───────────────────────────────┘
                            │
                 ✨ rendered back on the map ✨
```

---

## 🧠 The Research Behind It

The cloud-removal model draws on recent satellite time-series research:

- **🧩 U-TILISE** *(Stucker et al., 2023)* — a sequence-to-sequence model combining a convolutional U-Net encoder/decoder with lightweight temporal self-attention. **This is the core architecture powering Terra Auspex.**
- **🌊 AGFlow** *(Fallah et al., 2026)* — a flow-matching model fusing SAR (radar) with optical imagery, supporting "anytime" querying. **Blueprint for the major-project extension.**
- **☁️ Cloud-Matting** *(Ma et al., 2023)* — a single-image alpha-matting approach, used as a **baseline comparison** to demonstrate why single-frame methods fall short.

**Why start here?**
- ✅ No SAR dependency yet — a simpler data pipeline to begin with
- ✅ Public reference implementation + dataset (EarthNet2021) to build from
- ✅ Naturally extensible into SAR fusion and generative querying later

---

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| 🌐 Frontend | Leaflet / Mapbox GL JS *(or CesiumJS for a full 3D globe)* |
| ⚙️ Backend | Python — FastAPI / Flask |
| 🧠 Deep Learning | PyTorch |
| 📡 Data Source | Sentinel Hub API / Google Earth Engine / AWS Open Data *(Sentinel-1 & 2)* |
| ☁️ Deployment | TBD |

---

## 📚 References

1. Ma, D.; Wu, R.; Xiao, D.; Sui, B. *Cloud Removal from Satellite Images Using a Deep Learning Model with the Cloud-Matting Method.* Remote Sensing, 2023.
2. Stucker, C.; Sainte Fare Garnot, V.; Schindler, K. *U-TILISE: A Sequence-to-Sequence Model for Cloud Removal in Optical Satellite Time Series.* IEEE TGRS, 2023.
3. Fallah, F.; Hsu, C.-Y.; Li, W.; Liljedahl, A.; Yang, Y. *Asynchronous Remote Sensing Time-Series Fusion for Cloud Removal and Anytime Reconstruction (AGFlow).* 2026.

---

<div align="center">

## 👤 Author

Built with ☁️ + 🧠 as a B.Tech minor/major project.

**⭐ If you like the concept, watch this space — the globe is coming.**

</div>

---

## 📄 License

TBD
