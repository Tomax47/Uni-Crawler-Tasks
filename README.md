# Vector Search Engine

**Name:** Харб Хнейди Тамам
**Group:** 11-200

This project implements a full-cycle search engine for Russian language text

<img src="Screenshot From 2026-03-05 23-19-36.png" alt="Search Engine Demo" width="600">

## Project Components
The system consists of several integrated modules:
1. **Crawler:** A script that scrapes and saves 100 HTML pages from Russian Wikipedia.
2. **Linguistic Processor:** Custom tokenization and lemmatization pipeline using `pymorphy3`.
3. **Boolean Search:** Index-based search supporting `AND`, `OR`, `NOT` operators.
4. **Vector Space Model:** TF-IDF calculation for documents and queries.
5. **Web Interface:** A Gradio-based application for real-time ranked search.

---

## Release History (Task Log)

### v1.0 - Web Crawling
- Implemented a crawler to download 100 thematic HTML pages.
- Created an `index.txt` file mapping document IDs to source URLs.

### v2.0 - NLP & Tokenization
- Developed a tokenization pipeline to extract Cyrillic words.
- Implemented filtering to remove stop words, prepositions, conjunctions, and "noise" (mixed alphanumeric strings).
- Integrated `pymorphy3` for morphological analysis.

### v3.0 - Inverted Index & Boolean Search
- Constructed a global inverted index (lemma to document ID mapping).
- Implemented a search engine capable of parsing complex Boolean queries with parentheses (e.g., `(A AND B) OR C`).

### v4.0 - TF-IDF Weighting
- Calculated Term Frequency (TF) and Inverse Document Frequency (IDF) for all tokens and lemmas.
- Generated weight files for each document to support vector search.

### v5.0 - Vector Search & Ranking
- Implemented **Cosine Similarity** to rank documents based on query relevance.
- Integrated the search logic into a unified engine.

### v5.1 - Web Interface Deployment
- Deployed a functional **Web UI using Gradio**.
- Added ranking logic to display the **Top 10 results** in a formatted table.

### v5.2 - Granular Linguistic Extraction
- **Update:** Modified the extraction logic to produce individual `.txt` files for every crawled document.
- Created separate archives for page-specific tokens and lemmas.
- Standardized lemma format to: `<lemma> <token1> <token2>...`.

### v5.3 - Glued Words Issue Fix
- **Update:** Modified the extraction logic to avoid gluing words after removing the HTML tags, and producing non-existing words like `статьислучайный`.
