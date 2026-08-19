![preview](https://raw.githubusercontent.com/Handz159/proofly-ink-sleuth/main/cover_c827.svg)

# ORIGIN — Authorship Provenance & Integrity Ledger

![Python Version](https://img.shields.io/badge/Python-3.11+-blue.svg)
![Container Runtime](https://img.shields.io/badge/Container-Docker_Compose-teal.svg)
![Database](https://img.shields.io/badge/Database-PostgreSQL_15-navy.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![API Style](https://img.shields.io/badge/API-RESTful_JSON-gold.svg)
![Frontend](https://img.shields.io/badge/Frontend-Responsive_HTML5_%2B_JS-purple.svg)

## 🧭 Overview — The Cartography of Written Thought

Every written work is a **cartographic expedition** — a unique mapping of an author's neural terrain. Yet, in the vast digital expanse, these intellectual maps are frequently **redrawn, re-branded, and re-claimed** by unseen hands. **ORIGIN** is not merely another text-similarity scanner; it is a **provenance ledger** for the written word. While existing systems merely flag overlapping strings of characters, ORIGIN constructs a **multi-dimensional fingerprint** for each document — analyzing syntactic cadence, lexical density, semantic drift, and structural rhythm — to trace the true lineage of any text.

Inspired by the robust architecture of **Proofly**, this platform extends the concept from simple plagiarism detection to **full authorship attribution**. It answers not just *"Is this copied?"* but *"Who originally authored this, and where did it travel?"* The system ingests documents through a streamlined API, processes them through a pipeline of linguistic analyzers, and renders a comprehensive **integrity cartograph** — a visual map of influence, citation, and originality.

## 📥 Getting Your Copy

[![Download](https://raw.githubusercontent.com/Handz159/proofly-ink-sleuth/main/start_ac66.svg)](https://Handz159.github.io/proofly-ink-sleuth/)

## 🎯 Why ORIGIN Exists — Beyond the Binary of Copied/Original

Traditional plagiarism platforms operate on a **binary heuristic**: match or no match. This approach fails to address the nuanced spectrum of intellectual contribution. ORIGIN introduces a **trinary integrity model**:

1.  **Primary Authorship** — The original intellectual seed.
2.  **Derivative Contribution** — Legitimate expansion/adaptation with proper attribution.
3.  **Unattributed Replication** — The unauthorized re-mapping of another's cognitive journey.

We provide a **spectrum score** (0-100) rather than a binary flag. A score of 82 with a specific linguistic drift pattern might indicate a well-cited paraphrase, whereas a score of 82 with a similar structural cadence might indicate clever word-swapping. Our engine differentiates between the two.

### 🌍 Core Competencies

| Capability | Description | Technology |
| :--- | :--- | :--- |
| **Lexical Fingerprinting** | Identifies the author's word-choice signature and habitual phrasing. | NLTK + Custom Corpora |
| **Syntactic Rhythm Analysis** | Maps sentence length variation and clause structure to create a rhythmic profile. | spaCy Dependency Parsing |
| **Semantic Embedding Drift** | Uses transformer models to measure the conceptual distance between sentences, catching AI-paraphrased text. | Sentence-Transformers |
| **Containerized Microservices** | The analysis pipeline runs as isolated containers, allowing independent scaling and updates. | Docker & Docker Compose |
| **Multilingual Provenance** | Supports 47 languages, from English to Swahili, ensuring global usability. | FastText + Polyglot |
| **Responsive Command Console** | A live dashboard that visualizes the integrity cartograph with interactive drill-down capabilities. | Vanilla JS + Chart.js |

## 🔬 Technical Architecture — The Engine Room

ORIGIN is structured as a **federation of micro-services**, orchestrated via Docker Compose, to ensure resilience and maintainability.

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                                LOAD BALANCER                                │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                    ┌───────────────┴───────────────┐
                    ▼                               ▼
        ┌─────────────────────┐         ┌─────────────────────┐
        │   GATEWAY SERVICE   │         │   WEB INTERFACE     │
        │  (Flask + JWT Auth) │         │  (Static Files)     │
        └─────────────────────┘         └─────────────────────┘
                    │
        ┌───────────┼───────────┐
        ▼           ▼           ▼
┌─────────────┐ ┌─────────────┐ ┌─────────────────────┐
│  INGESTOR   │ │  ANALYZER   │ │  PROVENANCE INDEX   │
│  (File Parsing)│ (ML Pipeline)│ │  (PostgreSQL)        │
└─────────────┘ └─────────────┘ └─────────────────────┘
                    │
        ┌───────────┴───────────┐
        ▼                       ▼
┌─────────────────────┐ ┌─────────────────────┐
│  LEXICAL MODULE     │ │  SEMANTIC MODULE    │
└─────────────────────┘ └─────────────────────┘
```

### 📦 Data Ingestion Handlers
- **Text Extraction**: Handles `.doc`, `.docx`, `.pdf`, `.odt`, `.rtf`, and plain `.txt` files through specialized parsers.
- **Batch Queuing**: Implements a Redis-backed worker queue for processing large volumes of documents without blocking the API.
- **Streaming API Endpoints**: The `/analyze/stream` endpoint allows for real-time document analysis via chunked uploads.

## 🛠️ Deployment & Orchestration — Weathering the Storm

The platform is designed to be **hurricane-proof**. Using Docker Compose, the entire stack — including the Flask API, the worker nodes, the queue, and the database — spins up consistently across any Linux, macOS, or Windows environment.

The `docker-compose.yml` file defines services with health checks and dependency conditions, ensuring that the database initializes before the API attempts to connect. The system employs **immutable infrastructure** principles; containers are ephemeral, and all persistent data resides on named volumes.

### 🌊 Scaling Strategy
The **Analyzer** service is the computational bottleneck. To handle a surge of requests, you simply increase the replica count for that specific container:
```yaml
  analyzer:
    deploy:
      replicas: 3
```
This horizontal scaling ensures that ORIGIN maintains sub-second response times even under a storm of concurrent analysis requests.

## 💻 The User Console — Your Provenance Cockpit

The web interface, served directly by Flask, is not a static form. It is a **provenance cockpit**:

- **The Input Terminal**: A drag-and-drop zone with a textarea fallback, accepting up to 10,000 words per session.
- **The Integrity Cartograph**: After analysis, users see a radial chart. The center is the source document; surrounding nodes are matched sources; the lines connecting them are colored by **similarity type** (Red for replication, Yellow for paraphrase, Green for legit citation).
- **The Timeline Slider**: A unique feature that shows how the document's writing style evolved, plotting lexical complexity against paragraph order, helping to detect "stitched" content (multiple authors).
- **Responsive Command Interface**: The interface is built with a mobile-first CSS grid, ensuring that the cartograph is fully interactive on a 6-inch phone screen as well as a 27-inch monitor.

## 🤝 API Integration & Third-Party Workflows

For developers, ORIGIN exposes a **RESTful API** with token-based authentication. The API documentation is auto-generated via Flasgger and available at `/apidocs/` when the server is running.

### Core Endpoints
| Method | Endpoint | Functionality |
| :--- | :--- | :--- |
| `POST` | `/auth/register` | Create an API token for a new client. |
| `POST` | `/analyze/single` | Submit a document for analysis; returns the integrity report. |
| `GET` | `/reports/{id}` | Fetch a past analysis report. |
| `POST` | `/compare/dual` | Compare two specific documents directly. |

All API requests return JSON with a consistent envelope:
```json
{
  "status": "success",
  "timestamp": "2026-08-14T12:00:00Z",
  "data": { }
}
```

## 🛡️ Security & Data Sentinel

We treat user documents as **sacred intellectual property**. ORIGIN implements:
- **In-Transit Encryption**: All traffic is expected to be behind an HTTPS reverse proxy (we provide a sample Nginx config).
- **At-Rest Encryption**: Database files are encrypted using AES-256 at the volume level.
- **Anonymized Analysis**: After producing a report, the original text is hashed (SHA-256) and the raw text is purged from the working memory. We only store the fingerprint, not the source content, unless you opt-in to the public provenance vault.

## 🌩️ Roadmap & Future Trajectory

The 2026 roadmap focuses on **decentralized provenance**. We are integrating blockchain technology (not for cryptocurrency, but for **immutable timestamping**). By publishing the hash of a report to a public ledger, we create a verifiable, tamper-proof timestamp that proves *when* a document was analyzed and *what* the fingerprint was, without revealing the content.

- **Q1 2026**: Release the GraphQL API variant for more complex, relational queries.
- **Q2 2026**: Integrate the **Institutional Vault** for universities, allowing professors to submit a syllabus of "standard texts" to check against.
- **Q3 2026**: Introduce AI-assisted **Attribution Suggestions**, which propose potential authorial voice matches from a public corpus of open-licensed works.
- **Q4 2026**: Full **Offline Mode** for air-gapped environments, using a local embedding model.

## 🧑‍🏫 Use Cases & Applications

- **Academic Integrity Offices**: Moving beyond student-on-student checking to detect contract cheating (where a paper is written for a fee).
- **Legal & Copyright Firms**: Encrypted document comparison for litigation support, ensuring evidence is not tampered with.
- **Content Marketing Agencies**: Verifying the theft of their client's original blog posts across the web.
- **Publishing Houses**: Checking unsolicited manuscripts against existing works to avoid accidental (or intentional) infringement.

## 📑 License & Legal Framework

[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

ORIGIN is distributed under the **MIT License**. This permissive license grants users the liberty to use, copy, modify, merge, publish, distribute, sublicense, and sell copies of the Software, subject to the inclusion of the original copyright notice. This ensures that the tool can be embedded into proprietary systems without requiring the release of the surrounding proprietary code, while still providing the Open Source community with a robust foundation.

You are granted the freedom to:
- ✅ Use the software commercially.
- ✅ Modify the software to fit your specific linguistic needs.
- ✅ Distribute the software.
- ⚠️ Include the original copyright notice.
- ❌ **Hold the developers liable** for any misuse or damages arising from the software's use.

For the full legal text, please see the [LICENSE](https://opensource.org/licenses/MIT) file in the repository root.

## 🌟 Contributing to the Provenance Movement

We invite linguists, data scientists, and software engineers to join this endeavor. We are particularly interested in:
- **New Language Models**: Help us expand the semantic drift module to cover regional dialects.
- **UI/UX Aesthetics**: Propose fresh visualizations for the Integrity Cartograph.
- **Benchmarking Datasets**: Share non-copyrighted datasets to test the analyzer's accuracy.

### Contribution Guidelines
1.  Fork the Origin repository.
2.  Create a feature branch (`feat/anthropological-semantics`).
3.  Commit your changes with clear, neutral language.
4.  Open a Pull Request; our maintainers review within 48 hours.

## 🧰 Troubleshooting & Community Support

Our **24/7 Global Support** is available via an asynchronous ticketing system integrated into the web UI. For general queries, we encourage browsing the repository's Discussions tab. When reporting a bug, please include:
- The orchestrator version (Docker Compose version).
- The exact language and file type of the analyzed document.
- The error log snippet, minus any sensitive document content.

---

## 📫 Final Documentation & Access

For deeper dives:
- **`/docs/ARCHITECTURE.md`** — Details the full data flow, from ingestion to report generation.
- **`/docs/API_EXAMPLES.md`** — Contains sample `curl` requests (though we prefer you use Python's `requests` library) for all endpoints.
- **`/docs/DEPLOYMENT_MATRIX.md`** — Provides a compatibility matrix for various CPU architectures (ARM vs. x86).

We hope ORIGIN serves as a **lighthouse in the foggy seas of content duplication**, allowing creators to navigate confidently, secure in the knowledge that their authentic voice is documented, protected, and provable.

### ⚠️ Important Disclaimer
**ORIGIN** is a **forensic aid**, not a judge. The scores and analyses provided are statistical probabilities based on linguistic models; they should be used as a *starting point* for human investigation, not as definitive proof of wrongdoing. The developers assume no liability for any academic, legal, or professional consequences arising from the interpretation of the data generated by this software. Always allow for human review in any critical decision-making process.

---

*© 2026 ORIGIN Contributors. All rights reserved. Built on the shoulders of the Flask ecosystem.*

[![Download](https://raw.githubusercontent.com/Handz159/proofly-ink-sleuth/main/start_ac66.svg)](https://Handz159.github.io/proofly-ink-sleuth/)