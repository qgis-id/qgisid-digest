---
name: qgisid-digest-pipeline
description: Pipeline for parsing QGIS Indonesia Telegram chat exports, anonymizing personal data, filtering sensitive content, generating 768-dim IndoBERT embeddings, synthesizing Markdown Knowledge Base wiki articles, and building an interactive web portal for GitHub Pages.
---

# QGIS Indonesia Knowledge Base & Digest Skill

Use this skill when processing Telegram community chat exports from the **QGIS Indonesia** group to generate an anonymized, privacy-compliant Knowledge Base portal powered by **IndoBERT** (`indobenchmark/indobert-base-p1`).

---

## 🎯 Primary Goal & Pipeline Workflow

Transform raw Telegram export JSON (`raw/telegram.json`) into:
1. **6,332 Anonymized Discussion Threads** (`output/parsed_threads.json`).
2. **10 IndoBERT Technical Domain Clusters** (`output/clustered_threads.json`).
3. **Markdown Wiki Knowledge Base Articles** (`output/knowledge_base/`).
4. **Interactive Single-Page Web Portal** (`index.html`).

---

## 🛠️ System Requirements & Dependencies

Ensure Python 3.10+ is active with the following packages:

```bash
pip install torch transformers sentence-transformers scikit-learn google-genai
```

---

## 🔒 Step 1: Privacy Scrubbing & Thread Reconstruction

Run `scripts/01_parse_threads.py`:

```bash
python3 scripts/01_parse_threads.py
```

### Privacy & Safety Rules:
- **Username Anonymization**: All `@usernames`, Telegram contact names, and reply references MUST be replaced with `[Anggota Komunitas]`.
- **Sensitive Content Filter**: Automatically screens and drops messages containing harsh words, profanity (Indonesian/Javanese/English), or religious debate terms.
- **Thread Linkage**: Groups messages sharing `reply_to_message_id` into cohesive reply-chain discussion threads.

---

## 🤖 Step 2: IndoBERT Embedding & Domain Clustering

Run `scripts/02_indobert_cluster.py`:

```bash
python3 scripts/02_indobert_cluster.py
```

### Classification Domains:
- `CRS_Proyeksi`: CRS, Proyeksi Koordinat, UTM, WGS84.
- `Vector_Attribute`: Data Vektor, Tabel Atribut, GeoPackage (.gpkg), Shapefile (.shp).
- `Raster_RemoteSensing`: Data Raster, DEM, Contour, Citra Satelit, NDVI.
- `Plugins_Tools`: QuickMapServices, SCP, QuickOSM.
- `PyQGIS_Automation`: PyQGIS, Python Scripting, Otomasi Processing Toolbox.
- `PostGIS_Database`: PostgreSQL, PostGIS, Spatial Index, SQL queries.
- `WebGIS_Server`: WebGIS, QGIS Server, Lizmap, WMS/WFS.
- `Print_Layout`: Print Layout, Kartografi, Export PDF.
- `Install_System_Crash`: OSGeo4W, Standalone Installer LTR, Hardware, Crash Dump.
- `Diskusi_Umum`: General QGIS Workflows & Community Best Practices.

---

## 📚 Step 3: Markdown Wiki Knowledge Base Synthesis

Run `scripts/03_synthesize_kb.py`:

```bash
python3 scripts/03_synthesize_kb.py
```

Generates structured Markdown wiki articles inside `output/knowledge_base/` containing:
- 📌 **Ringkasan & Gambaran Topik**: Executive domain summary & thread statistics.
- 🛠️ **Masalah Umum & Solusi Teknis (Troubleshooting Table)**: 3-column table (`Masalah / Gejala Utama`, `Akar Penyebab`, `Solusi & Langkah Perbaikan Teknis`).
- 💡 **Alur Kerja & Best Practices Komunitas**: Standardisasi data, spatial index, and QGIS LTR guidelines.
- 💬 **Contoh Diskusi Nyata Komunitas**: Clean, anonymized quote cards.

---

## 🌐 Step 4: Web Portal Generation

Run `scripts/04_build_portal.py`:

```bash
python3 scripts/04_build_portal.py
```

### Outputs Generated:
- `index.html` (Repository root for GitHub Pages)
- `QGIS Indonesia Knowledge Base UI/index.html`
- `output/qgisid-knowledge-base.html`
- `qgis-logo.svg` (Official QGIS vector logo)
- `og-preview.png` (Open Graph 1200x630 banner for WhatsApp link previews)

---

## 🚀 Deployment to GitHub Pages

To publish the generated portal to `https://qgis-id.github.io/qgisid-digest/`:

```bash
git add .
git commit -m "feat(digest): Build Knowledge Base portal via IndoBERT pipeline"
git push origin main
```

Ensure GitHub Pages source is set to `Branch: main` and `/ (root)` under **Repository Settings -> Pages**.
