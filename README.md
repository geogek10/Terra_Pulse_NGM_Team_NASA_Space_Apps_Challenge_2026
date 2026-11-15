# TerraPulse — *The GPS for Agriculture*

> **Authors:** Gkekas Georgios, Kyritsis Thomas  
> **Project Paper:** *TerraPulse: A Precision Digital Agriculture Platform Leveraging NASA Earth Observation Data and Specialized Neural Networks* — [Read the Full Paper (PDF)](<https://drive.google.com/file/d/1Itrr0SEqXuZhnRUyevfTjdnPLwHSKElD/view?usp=drive_link>)

---

## Project Links & Media

- **Canva Presentation:** [View TerraPulse Pitch Deck on Canva](https://canva.link/r5jtxxe224ry0d1)
- **Project Presentation Video:** [Watch Project Presentation Video](<https://drive.google.com/file/d/1H2_RAsfx15EeBXayk801OG2dDIiEk_Ui/view?usp=drive_link>)
- **App Demonstration Video:** [Watch Live App Demonstration Video](<https://drive.google.com/file/d/1H2_RAsfx15EeBXayk801OG2dDIiEk_Ui/view?usp=drive_link>)
- **Technical Paper (PDF):** [TerraPulse Scientific Paper (9 pages, incl. Appendix & System Screenshots)](<https://drive.google.com/file/d/1Itrr0SEqXuZhnRUyevfTjdnPLwHSKElD/view?usp=drive_link>)

---

## Overview

**TerraPulse** is an AI-powered precision agriculture and satellite intelligence platform built for the **NASA Space Apps Challenge**.  
As detailed in our accompanying technical paper, it bridges the gap between complex Earth Observation (EO) telemetry and practical, everyday decisions at the field level—translating multi-sensor satellite baselines and live meteorological feeds into **simple, actionable guidance for farmers**, supported by deep scientific charts and neural network analytics underneath.

---

## Why TerraPulse?

Modern farmers face four interconnected challenges under a changing climate:
1. **Drought & Water Waste:** Irregular rainfall and heatwaves reduce root-zone soil moisture, while watering without telemetry wastes water and pumping electricity.
2. **Soil Exhaustion & Erosion:** Continuous monoculture drains organic matter, accelerates topsoil erosion, and drives up chemical fertilizer dependency.
3. **The Crop Rotation Dilemma:** Choosing the right next crop requires balancing soil history, aridity, nitrogen needs, and farm profitability.
4. **Wildfires & Extreme Storms:** After wildfires or severe weather, sloped farmland can lose its fertile topsoil in the very first heavy rain unless stabilized immediately.

**TerraPulse solves all four in one unified interface.** You click any location or draw your exact field boundary on the map, and four specialized PyTorch neural networks analyze the land, fuse live weather forecasts, and explain—in plain language—**what is happening and what to do tomorrow morning**.

---

## Key Features

- **Interactive 3D Earth Landing Page:** A Three.js 3D globe with dual orbital rings and a moving satellite marker introducing TerraPulse, with instant Dark/Light theme and `GR ↔ EN` language toggles.
- **Interactive Field Map OS (Leaflet + Leaflet.Draw):**
  - Switch between **Dark OS**, **Satellite**, and **NDVI / Topo** base layers.
  - Search any city or farming region worldwide (powered by **OpenStreetMap Nominatim**—demonstrated live on fields such as **Nafpaktos**, **Larissa**, **Aetolia**, **Crete**, and **Giannitsa**).
  - **Draw any field polygon** to automatically calculate its real geodesic area in **hectares & stremmata** without resetting your zoom level.
  - **3×3 Variable Rate Application (VRA) Sub-Grid:** Displays 9 color-coded micro-zones inside your field (`+15%`, `0%`, `-15%` dose adjustments) to demonstrate sub-field micro-zoning.
  - **Compare Two Fields (Field A vs Field B):** Save any two fields and compare their water stress, soil health, erosion risk, and annual savings side-by-side.
- **Two-Layer Data Analysis Suite:**
  - **Layer 1 — At a Glance (For the Farmer):** A circular animated gauge, a plain-language headline and explanation, and a 1-2-3 step-by-step morning action plan.
  - **Layer 2 — Further Satellite Analytics:** Multi-series Chart.js gradient graphs, regional benchmarks, annual cost breakdowns (€), a live 7-day rain-aware irrigation schedule, interactive mini-maps with radar sweeps, and a full scientific summary.
- **Interactive "What-If" Farmer Simulator:** Change **Crop** (*Durum Wheat, Cotton, Corn, Olive Grove, Vineyard, Alfalfa*), **Irrigation Method** (*Flood Furrow 52%, Overhead Sprinkler 74%, Subsurface Drip 93%*), or **Weather Scenario** (*Live Forecast, Heatwave +5.5°C, Post-Fire Storm*) to watch every prediction, chart, and recommendation update in real time.
- **Voice Briefing ("Listen"):** Built-in **Web Speech API** reads the active field advisory aloud in **Greek (`el-GR`)** or **English (`en-US`)**.
- **100% Bilingual (`GR ↔ EN`) & True Dark/Light Theme:** Translates every UI element, chart label, voice readout, SMS alert, and scientific report on the fly.
- **Clean 1-Page PDF Prescription Export:** Dedicated `@media print` styling turns the dashboard into a clean, white, ink-friendly agronomist prescription sheet.

---

## How the 4 PyTorch Neural Networks Work

Because multi-year, field-level labeled datasets spanning all four domains are scarce, the four PyTorch networks are implemented as **biophysically grounded surrogate models** trained on agro-climatic datasets parameterized with NASA EO-informed priors (**NASA POWER, SMAP, ECOSTRESS, GPM, Landsat, MODIS, SRTM**) and established domain models (**FAO-56**, **RUSLE**, biological nitrogen fixation **BNF**, and post-fire **dNBR** runoff curves):

| Network | Focus | Key Inputs | Outputs & Farmer Value |
| :--- | :--- | :--- | :--- |
| **Network 1 — Water** | Drought & Irrigation | 6-month temperature, rainfall, soil moisture, NDVI, slope, `ET₀` | Predicts root-zone water stress (`0–1`), exact `m³/stremma`, best watering hours (`05:00–07:00`), and skips irrigation when rain (`≥ 4 mm`) is forecast. |
| **Network 2 — Soil** | Degradation & Depletion | Spectral vegetation, organic matter, slope, rainfall, aridity | Outputs `health_proxy` & `erosion_proxy` (`0–1`), NPK & carbon balance, and no-till / cover-crop advice to cut fertilizer costs. |
| **Network 3 — Rotation** | Crop Matchmaking | Aridity, soil organic matter, terrain slope, moisture | Scores rotation crops (Legumes, Alfalfa, Wheat, Sorghum), estimates free **BNF** (`kg N/ha`), projects 3-year nitrogen recovery, and compares ROI. |
| **Network 4 — Fire & Floods** | Extreme Events | Burn severity (`dNBR`), slope, vegetation state, canopy heat | Outputs post-fire `erosion_risk` & `recovery_score` (`0–1`), simulates 12-month vegetation rebound, creates a 72h rapid-seeding plan, and previews a **72h Farmer SMS Alert**. |

---

## Projected Ecological & Economic Impact (Literature-Benchmarked)

As documented in our paper, by translating sensor-driven scheduling and legume-diversified rotation principles into an accessible tool, TerraPulse targets the following peer-reviewed benchmarks:
- **27–45% Projected Water Conservation** compared to conventional scheduling without hurting crop yield.
- **Up to 40% Reduction in Synthetic Nitrogen Dependency** through strategic integration of nitrogen-fixing legumes (`32–115 kg N/ha/year` BNF) and soil organic carbon restoration.
- **Lower Operational Costs (OPEX)** on irrigation energy and chemical inputs, alongside improved harvest resilience under extreme climate shocks.

---

## Live Data Sources

- **Open-Meteo Forecast & Soil Moisture API:** 30 days of historical temperature/rainfall plus a live 7-day forecast, FAO reference evapotranspiration (`ET₀`), and volumetric root-zone soil moisture (`7–28 cm`).
- **Open-Meteo 5-Point Elevation API:** Queries elevation at the field center and four surrounding offsets to compute true terrain slope (`°`).
- **OpenStreetMap Nominatim:** Worldwide place and region search.
- *(Offline Fallback: A 10-minute in-memory cache and deterministic telemetry fallback ensure the platform always runs smoothly even without internet access.)*

---

## Project Structure

```text
terra_pulse/
├── README.md                       # Project documentation
├── terra_pulse_frontend/
│   ├── index.html                  # Main HTML layout (3D Globe, Map OS, 5-Tab Analysis Suite)
│   ├── logo.png                    # TerraPulse brand logo & favicon
│   ├── css/
│   │   └── styles.css              # Light/Dark CSS variables, HUD styling, animations & print sheet
│   └── js/
│       ├── state.js                # App state, zoom-lock fix, EN/GR translations, theme & voice readout
│       ├── globe.js                # Three.js 3D Earth, starfield & orbital satellites
│       ├── charts.js               # Chart.js gradient charts & Leaflet mini-maps
│       ├── map.js                  # Leaflet Map OS, polygon drawing, search & 3x3 VRA grid
│       ├── api.js                  # Backend API calls, What-If simulator & Field A/B comparison
│       └── main.js                 # View/sidebar/tab navigation & startup
│
└── terra_pulse_backend/
    ├── main.py                     # FastAPI entry point + CORS + router registration
    ├── requirements.txt            # Python dependencies (fastapi, uvicorn, torch)
    ├── core/
    │   ├── config.py               # Crop coefficients (Kc), irrigation efficiencies & paths
    │   ├── model_loader.py         # PyTorch architectures, .pth weights & preprocess.json loaders
    │   ├── geo_live.py             # Live Open-Meteo weather/moisture/elevation fetch + 10-min cache
    │   └── telemetry.py            # Location telemetry builder, 7-day schedule & VRA sub-grid
    ├── routes/
    │   ├── water.py                # GET /api/water-analysis (Network 1)
    │   ├── soil.py                 # GET /api/soil-analysis (Network 2)
    │   ├── rotation.py             # GET /api/rotation-analysis (Network 3)
    │   └── fire.py                 # GET /api/fire-analysis (Network 4)
    ├── training/
    │   ├── train_network1_water.py     # Trains & saves terrapulse_water_model.pth
    │   ├── train_network2_soil.py      # Trains & saves terrapulse_soil_model.pth + preprocess.json
    │   ├── train_network3_rotation.py  # Trains & saves terrapulse_rotation_model.pth
    │   └── train_network4_fire.py      # Trains & saves terrapulse_fire_model.pth + preprocess.json
    └── *.pth / *.json              # Saved PyTorch weights & normalization parameters
```

---

## Quick Start Guide

### 1. Start the Backend (Python + FastAPI)
Make sure Python 3.10+ is installed, then install the backend dependencies:

```bash
cd terra_pulse_backend
pip install -r requirements.txt
uvicorn main:app --reload
```

The API will run at **`http://localhost:8000`** (interactive docs at `http://localhost:8000/docs`).

### 2. Start the Frontend
Open `terra_pulse_frontend/index.html` using **VS Code Live Server** (recommended) or Python's built-in HTTP server:

```bash
cd terra_pulse_frontend
python -m http.server 5500
```

Then open **`http://localhost:5500`** in your browser.

### 3. (Optional) Retrain the 4 Neural Networks
To regenerate or retrain the `.pth` weight files and preprocessing `.json` scalers from scratch:

```bash
cd terra_pulse_backend
python training/train_network1_water.py
python training/train_network2_soil.py
python training/train_network3_rotation.py
python training/train_network4_fire.py
```

---

## Tech Stack

- **Frontend:** HTML5, Tailwind CSS, Vanilla Modular JavaScript, Three.js, Leaflet + Leaflet.Draw, Chart.js, Web Speech API
- **Backend:** Python, FastAPI, Uvicorn, PyTorch
- **Data & Maps:** Open-Meteo (Forecast, Soil Moisture, Elevation), OpenStreetMap / Nominatim, Esri World Imagery, OpenTopoMap, NASA EO Baselines (POWER, SMAP, ECOSTRESS, GPM, Landsat, MODIS, SRTM)
