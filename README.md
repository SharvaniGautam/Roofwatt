<div align="center">

# ☀️ RoofWatt

### Rooftop solar potential mapping for Indian cities, using open data and GeoAI

*Part of the **geofiedwithme** GeoAI learning journey*

![Status](https://img.shields.io/badge/status-in%20progress-orange)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Domain](https://img.shields.io/badge/domain-GeoAI%20%7C%20Solar%20Energy-yellow)
![Data](https://img.shields.io/badge/data-open%20source-brightgreen)
![License](https://img.shields.io/badge/license-MIT-lightgrey)

</div>

---

## 📌 Problem Statement

India is pushing rooftop solar at scale through national schemes such as PM Surya Ghar, but the question **"which roofs are actually worth equipping, and how much power can they produce?"** is still answered mostly by site visits and rough estimates.

This creates three gaps:

- **Utilities and city planners** lack building-level maps of rooftop potential, so they cannot plan grid capacity or target neighbourhoods.
- **Installers and lenders** spend time and money surveying roofs before they know whether a project makes financial sense.
- **Households** get generic estimates that ignore their own roof size, shading and obstructions such as water tanks and stairwells.

Existing open tools are built for Western cities. Indian rooftops are smaller, more irregular and more cluttered, and free high-resolution imagery for Indian cities is limited.

## 🎯 Objective

For a chosen Indian city, estimate for every building:

1. Usable roof area, after accounting for obstructions
2. Solar capacity (kW) and yearly energy generation (kWh)
3. Annual savings (₹) and payback period

Then aggregate results by ward to show where rooftop solar potential is concentrated.

## 🧭 Approach

| Step | What happens | Tools |
| --- | --- | --- |
| 1. Footprints | Load open building footprints and compute roof areas in a metric projection | GeoPandas, Shapely |
| 2. Sunlight | Get solar irradiance for the city | pvlib, PVGIS / NASA POWER |
| 3. Baseline | Fixed usable-area fraction × irradiance × efficiency | Python |
| 4. Model | Segmentation model to detect obstructions and refine usable roof area | PyTorch, U-Net |
| 5. Insights | Savings, payback and ward-level ranking | GeoPandas |
| 6. App | Interactive map to click any building | Streamlit / MapLibre |

The model is always compared against the simple baseline and validated on neighbourhoods it never saw during training.

## 📊 Results

> Results will be added as each phase is completed.

| Method | Usable-area IoU | Notes |
| --- | --- | --- |
| Fixed-fraction baseline | TBD | Phase 3 |
| U-Net model | TBD | Phase 4, tested on held-out neighbourhoods |

**City estimate:** TBD MW of rooftop potential in `<city name>`.

## 🗺️ Roadmap

- [ ] **Phase 0:** Setup
- [ ] **Phase 1:** Geospatial fundamentals
- [ ] **Phase 2:** Solar basics and choosing the city
- [ ] **Phase 3:** Baseline estimate
- [ ] **Phase 4:** Deep learning for usable roof area
- [ ] **Phase 5:** Savings, payback and ward-level insights
- [ ] **Phase 6:** Web app and write-up

## 📂 Repo Structure

```
geofiedwithme/
├── notebooks/        # one notebook per phase
├── src/              # reusable code (data loading, model, metrics)
├── app/              # web app
├── data/             # small samples only; large files stay out of git
├── docs/             # images and demo GIF
├── requirements.txt
└── README.md
```

## 🚀 Getting Started

```bash
git clone https://github.com/<your-username>/geofiedwithme.git
cd geofiedwithme
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

## 🗃️ Data Sources

- Building footprints: Google Open Buildings or Overture Maps
- Solar irradiance: PVGIS, NASA POWER or Global Solar Atlas
- Roof imagery: to be chosen in Phase 2 (OpenAerialMap, Maxar Open Data or drone data)

## ⚠️ Assumptions and Limitations

- Usable roof fraction, electricity tariff and installed cost per kW are assumptions and will be stated explicitly in the notebooks.
- Free high-resolution imagery for Indian cities is limited, which affects model accuracy.
- Estimates are for planning purposes and do not replace a site survey.

## 🙏 Acknowledgements

Copernicus / ESA, Google Open Buildings, PVGIS, NASA POWER, and the open-source GeoAI community.

## 📄 License

MIT. Add a `LICENSE` file to the repo.

---

<div align="center">

⭐ If you find this project useful, consider giving it a star.

</div>
