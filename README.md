# LLM Pipeline Explorer

> **How text becomes tokens, and then becomes points in 3D space.**

An interactive, client-side web application that visualizes two foundational stages of modern Large Language Model (LLM) pipelines: **subword tokenization** and **3D sentence embeddings**.

---

## 🌟 Overview

Before an LLM can understand sentences, it transforms unstructured human language into numerical representations:
1. **Tokenization**: Converting words and subwords into discrete integer token IDs.
2. **Embedding & Geometry**: Transforming token sequences into continuous high-dimensional vector spaces where semantic similarity translates into geometric proximity.

**LLM Pipeline Explorer** lets you see and interact with both stages directly inside your browser—no backend servers or complex environment setups required.

---

## ✨ Features

### 1. Interactive Tokenizer
- **Corpus-based Vocabulary Construction**: Learns a vocabulary of words and individual characters from an editable training corpus, sorted by frequency (with alphabetical tie-breaking).
- **Dynamic Vocabulary Scaling**: Adjust the vocabulary size via an interactive slider. As the vocabulary shrinks, observe how unknown words gracefully decompose into greedy longest-match subword pieces and characters (marked with `##` continuation prefixes).
- **Live Token Breakdown & Metrics**: Displays tokens as colored badges with their corresponding integer token IDs alongside real-time token count, word count, and subword statistics.

### 2. In-Browser 3D Embeddings
- **Client-Side Sentence Transformers**: Runs [`Xenova/all-MiniLM-L6-v2`](https://huggingface.co/Xenova/all-MiniLM-L6-v2) directly in your browser using [Transformers.js](https://github.com/xenova/transformers.js), computing 384-dimensional normalized sentence embeddings locally.
- **Pure JavaScript PCA**: Uses power-iteration Principal Component Analysis (PCA) written in vanilla JavaScript to reduce the 384-dimensional embedding vectors into 3 principal components (PC1, PC2, PC3).
- **Interactive 3D Scatter Visualization**: Powered by [Plotly.js](https://plotly.com/javascript/), enabling 3D orbit rotation, zooming, hover inspection, and automated semantic clustering (k-means).
- **Project Custom Inputs**: Type any custom word or sentence to tokenize it, compute its embedding, and project it onto the existing PCA coordinate space to see where it lands relative to the baseline clusters.

---

## 🎨 Design

- **Purple & Blue Palette**: Styled with deep royal violets (`#6d28d9`), sapphire blues (`#2563eb`), and midnight indigo headers.
- **Editorial & Human Aesthetic**: Crafted with typography using [Lora](https://fonts.google.com/specimen/Lora) for headings, [Inter](https://fonts.google.com/specimen/Inter) for clean interface text, and [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) for code and numerical data.
- **Responsive Layout**: Designed to work cleanly on desktop monitors as well as mobile screens.

---

## 🚀 Getting Started

The application is completely standalone:
- **No build steps** (no npm, webpack, or bundlers needed).
- All libraries (Transformers.js and Plotly.js) load via CDN.

### Option 1: Open Directly
Simply double-click `index.html` or open it in any modern web browser.

### Option 2: Local HTTP Server
If you prefer serving via a local server:
```bash
# Using Python 3
python3 -m http.server 8000
```
Then visit `http://localhost:8000` in your browser.

---

## 🛠️ Tech Stack

- **Vanilla HTML5, CSS3, & Modern JavaScript (ES Modules)**
- **Embeddings**: [@xenova/transformers](https://cdn.jsdelivr.net/npm/@xenova/transformers) (`all-MiniLM-L6-v2`)
- **3D Visualization**: [Plotly.js](https://cdn.jsdelivr.net/npm/plotly.js-dist)
- **Dimensionality Reduction**: In-house Power Iteration PCA & K-Means clustering

---

## 📄 License

MIT License. Feel free to explore, learn, and build upon it!
