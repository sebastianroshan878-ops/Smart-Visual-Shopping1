---
title: VisionCart AI
emoji: 🛍️
colorFrom: purple
colorTo: blue
sdk: streamlit
app_file: app.py
pinned: false
---

# 🛍️ VisionCart AI — Smart Visual Shopping & Price Discovery

An intelligent visual e-commerce assistant that allows users to upload or capture any product image and automatically identifies it using an ensemble of computer vision and language models (**BLIP**, **EasyOCR**, and **MobileNetV4**), comparing real-time prices across major Indian e-commerce platforms including **Amazon**, **Flipkart**, **Myntra**, **Meesho**, and **Snapdeal**.

---

## 🌟 Key Features

* **Visual Product Search**: Upload any photo or take a picture using your webcam/mobile camera.
* **AI Recognition Ensemble**:
  * **Salesforce BLIP**: Generates natural language image descriptions and identifies product categories.
  * **EasyOCR**: Detects and extracts brand text and logos from the image.
  * **MobileNetV4**: Extracts deep visual embeddings for similarity search.
* **Multi-Platform Price Comparison**: Automatically queries Amazon.in, Flipkart, Myntra, Meesho, and Snapdeal.
* **Reverse Image Search**: Integrated Google Lens visual search via SerpApi.
* **Glassmorphic Modern UI**: Dynamic WebGL background shader, interactive product carousel, and full Dark Mode support.
* **Progressive Web App (PWA)**: Includes manifest and service worker for mobile and offline capabilities.

---

## 🏗️ System Architecture

```
[ User Image Upload / Camera ]
               │
               ▼
   [ AI Recognition Pipeline ]
   ├── Salesforce BLIP (Image Captioning)
   ├── EasyOCR (Brand & Logo Text Detection)
   └── MobileNetV4 (Deep Visual Feature Extractor)
               │
               ▼
     [ Keyword & Query Engine ]
               │
               ▼
    [ Multi-Vendor Scraper ]
   ├── Amazon India
   ├── Flipkart
   ├── Myntra
   ├── Meesho
   └── Snapdeal
               │
               ▼
 [ Best Deal & Price Comparison UI ]
```

---

## 📁 Project Structure

```
Smart-Visual-Shopping1/
├── app.py                         # Streamlit application UI and orchestration
├── requirements.txt               # Project dependencies
├── README.md                      # Documentation and deployment metadata
├── class_indices.json             # 20 product category mappings
├── temp_query.jpg                 # Sample query image
├── .gitattributes                 # LFS and text attributes
├── .gitignore                     # Git ignore rules (secrets protected)
│
├── src/                           # Backend AI & Scraper Modules
│   ├── smart_recognizer.py        # BLIP + EasyOCR + Classifier ensemble
│   ├── scraper.py                 # Multi-platform e-commerce scraper
│   ├── feature_extractor.py       # MobileNetV4 feature extraction
│   ├── recommender.py             # Vector similarity ranking
│   ├── siamese.py                 # Siamese network similarity architecture
│   ├── classifier.py              # Product category classification
│   └── bg_shader.py               # WebGL background shader
│
├── .streamlit/                    # Streamlit Config & Static Assets
│   ├── secrets.toml.example       # API Key configuration template
│   └── static/                    # PWA assets (manifest, sw.js, icons)
│
└── .github/workflows/             # CI/CD Workflows
    └── huggingface_sync.yml       # Hugging Face deployment workflow
```

---

## 🚀 Getting Started

### 1. Prerequisites
* Python 3.10+
* Git

### 2. Installation

```bash
# Clone repository
git clone https://github.com/sebastianroshan878-ops/Smart-Visual-Shopping1.git
cd Smart-Visual-Shopping1

# Install dependencies
pip install -r requirements.txt
```

### 3. Configuration (Optional)
To enable real-time Google Lens reverse image search:
1. Copy `.streamlit/secrets.toml.example` to `.streamlit/secrets.toml`:
   ```bash
   cp .streamlit/secrets.toml.example .streamlit/secrets.toml
   ```
2. Add your free [SerpApi](https://serpapi.com/) key inside `.streamlit/secrets.toml`:
   ```toml
   SERPAPI_KEY = "your_actual_serpapi_key"
   ```

### 4. Running the Application

```bash
python -m streamlit run app.py
```


The app will be accessible at `http://localhost:8501`.

---

## 🛠️ Technology Stack

* **Frontend**: Streamlit, HTML5, Vanilla CSS, WebGL Shader, PWA
* **Deep Learning**: PyTorch, Torchvision, TIMM (MobileNetV4), Hugging Face Transformers (Salesforce BLIP)
* **OCR**: EasyOCR, OpenCV
* **Web Scraping & APIs**: BeautifulSoup4, Requests, SerpApi
* **Deployment**: Hugging Face Spaces / GitHub Actions
