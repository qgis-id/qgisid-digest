# Changelog & Data Coverage History

All notable updates, architectural changes, and data ingestion milestones for the **QGIS Indonesia Knowledge Base & Community Digest** are documented here.

---

## 📊 Dataset Ingestion & Coverage Status

| Metric | Details |
| :--- | :--- |
| **Total Messages Processed** | 26,475 Telegram messages |
| **Total Chat Messages** | 18,030 messages (excluding system join/leave events) |
| **Reconstructed Threads** | 6,332 discussion threads |
| **Earliest Chat Recorded** | **15 Mei 2019, 22:15:03** (`2019-05-15T22:15:03`) |
| **Last / Latest Chat Recorded** | **10 Februari 2026, 14:27:08** (`2026-02-10T14:27:08`) |
| **Telegram Export Dump Date** | 15 Februari 2026 (`raw/ChatExport_2026-02-15`) |
| **Active Time Horizon** | May 2019 – February 2026 (7+ years of community knowledge) |
| **Domain Categories** | 10 Technical Domains |
| **Embedding Engine** | IndoBERT (`indobenchmark/indobert-base-p1`, 768 dimensions) |

> ℹ️ **Note on Cutoff Date:**  
> The current digest reflects community discussions up to **10 Februari 2026, 14:27:08**. Messages sent after this date will be incorporated in future scheduled updates.

---

## Releases

### [1.2.0] - 2026-11-22

#### Added
- **Explicit Data Coverage Changelog**: Documented exact earliest (`2019-05-15`) and latest (`2026-02-10T14:27:08`) Telegram chat messages in `CHANGELOG.md`.
- **Hermes Agent Automation Skill**: Added `SKILL.md` specifying pipeline rules, privacy scrubbing, and automation steps for local homelab Hermes agents.
- **Mobile Responsive Navbar**: Fully responsive header with mobile hamburger drawer menu (`max-width: 860px`) and responsive grid layouts for stats and cards.
- **Social Media Link Previews**: Integrated Open Graph and Twitter Card meta tags with high-res banner `og-preview.png` (1200x630) for WhatsApp, Telegram, and X sharing.
- **Official Branding & Assets**: Added `qgis-logo.svg` vector badge and linked to `https://qgis-id.github.io/` and `https://t.me/qgisindonesia`.

#### Fixed
- **Default Landing Screen**: Configured default view to Beranda (`home`) instead of jumping directly to Arsip Digest on page refresh.
- **Topic Filtering Logic**: Resolved matching bug in `Component.renderVals()` where clicking domain chips failed to match full category names.
- **Yearly Analytics Data**: Resolved duplicate `yearlyAnalytics = {}` initialization, restoring 2019–2026 trend data on live deployment.

---

### [1.1.0] - 2026-08-29

#### Added
- **Yearly Trending Topics Engine (2019–2026)**: Visual analytics component tracking topic popularity, thread volume, and yearly milestones.
- **Option B GitHub Actions Workflow**: Automated periodic updates via `.github/workflows/update_digest.yml`.

---

### [1.0.0] - 2026-08-22

#### Added
- **Initial Knowledge Base Release**: Reconstructed 6,332 discussion threads from 26,475 raw Telegram messages.
- **IndoBERT Embedding & Clustering**: 768-dimensional Indonesian NLP text embeddings classifying discussions into 10 QGIS domains.
- **Privacy & Safety Filtering**: Complete anonymization (`[Anggota Komunitas]`) and filtering of profanity, harsh words, and sensitive debate terms.
- **Knowledge Base Markdown Wiki**: Synthesized structured articles with Troubleshooting Tables, Best Practices, and Community Quotes.
- **Single-Page Application Portal**: Built interactive UI portal using Google Fonts Manrope & Source Sans 3 with QGIS dark green branding.
