# nexus-orchestrator
Zero Cloud Dependency: The demo engine works entirely offline.  No Telemetry: Nexus Web Forge does not track, log, or transmit your data.  Local Execution: All code generation, file writing, and ZIP creation happens on your machine.  Optional API Keys: If you use v0 or Lovable, your keys are stored in your environment, never in the repository.
markdown

<div align="center">

<!-- ═══════════════════════════════════════════════════════════════════════════
     NEXUS WEB FORGE — README
     Cross-platform generative AI web interface
════════════════════════════════════════════════════════════════════════════ -->

<svg width="800" height="200" viewBox="0 0 800 200" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <linearGradient id="bgGrad" x1="0%" y1="0%" x2="100%" y2="100%">
      <stop offset="0%" stop-color="#0a0a0a"/>
      <stop offset="100%" stop-color="#121212"/>
    </linearGradient>
    <linearGradient id="neonGrad" x1="0%" y1="0%" x2="100%" y2="0%">
      <stop offset="0%" stop-color="#00ff9d">
        <animate attributeName="stop-color" values="#00ff9d;#4c9aff;#00ff9d" dur="4s" repeatCount="indefinite"/>
      </stop>
      <stop offset="100%" stop-color="#4c9aff">
        <animate attributeName="stop-color" values="#4c9aff;#00ff9d;#4c9aff" dur="4s" repeatCount="indefinite"/>
      </stop>
    </linearGradient>
    <filter id="glow">
      <feGaussianBlur stdDeviation="4" result="blur"/>
      <feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge>
    </filter>
  </defs>

  <rect width="800" height="200" fill="url(#bgGrad)" rx="12"/>
  <rect x="1" y="1" width="798" height="198" fill="none" stroke="url(#neonGrad)" stroke-width="2" rx="11" opacity="0.4"/>

  <text x="400" y="100" text-anchor="middle" font-family="ui-monospace, monospace" font-size="46" font-weight="900" fill="url(#neonGrad)" filter="url(#glow)">
    NEXUS WEB FORGE
    <animate attributeName="opacity" values="1;0.8;1" dur="2s" repeatCount="indefinite"/>
  </text>
  <text x="400" y="140" text-anchor="middle" font-family="ui-monospace, monospace" font-size="16" fill="#a0a0a0" letter-spacing="4">
    LOCAL AI WEB GENERATION ENGINE
  </text>
</svg>

<br/>

[![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](#)
[![Architecture](https://img.shields.io/badge/Architecture-Local%20%2B%20MCP-00ff9d?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-NEXUS--OPEN--3.0-4c9aff?style=for-the-badge)](#)
[![Status](https://img.shields.io/badge/Status-Operational-00ff9d?style=for-the-badge)](#)

<br/>

**Write an idea. Watch the code write itself. Export as ZIP.**
**Powered by Lovable MCP, v0 API, and a local demo engine.**

**[⚡ Quick Start](#-quick-start) · [🧠 Engines](#-engines) · [🏗️ Architecture](#️-architecture) · [📦 Export](#-export)**

</div>

---

## 🧬 What is Nexus Web Forge?

**Nexus Web Forge** is a fully local, sovereign web interface that bridges the gap between your ideas and your codebase. It orchestrates multiple generative AI engines, including Lovable (via MCP), v0 (via API), and a custom-built local demo engine that works with zero external dependencies.

You type an idea. Nexus Web Forge sends it to the selected engine, retrieves the generated code, writes the files to your local disk, and offers a live preview and a downloadable ZIP archive.

**No cloud storage. No telemetry. The code stays with you.**

---

## ⚡ Quick Start

### Prerequisites

- Python 3.10+
- `requests` library (for the v0/Lovable engines)
- Optional API keys: `V0_API_KEY`, `LOVABLE_API_KEY`

### 1. Clone the repository

```bash
git clone https://github.com/Aissamohammedi88/Nexus-Web-Forge.git
cd Nexus-Web-Forge

2. Install dependencies
bash

pip install requests

3. Run the forge
bash

python3 nexus_web_forge.py

4. Open the interface

Navigate to http://127.0.0.1:9999 in your browser.
🧠 Engines
Engine	Type	Authentication	Description
Lovable	MCP	LOVABLE_API_KEY (OAuth)	Full project generation via Lovable's MCP protocol
v0	API	V0_API_KEY	Vercel's v0 API for chat-based code generation
Bolt	Link	None	Opens Bolt.new in a new tab with your prompt pre-filled
Demo	Local	None	A built-in local generator that creates a fully functional static site without any API
Choosing an engine

    auto (default): Uses v0 if available, then Lovable, then falls back to Demo.

    v0: Requires V0_API_KEY.

    lovable: Requires LOVABLE_API_KEY (OAuth flow).

    bolt: Generates a direct link to Bolt.new.

    demo: Works offline, generates a complete static site.

🏗️ Architecture
text

┌─────────────────────────────────────────────────────────────────────────┐
│                        NEXUS WEB FORGE (HTTP UI)                       │
│                          Python 3.10+ · Port 9999                      │
└───────────────────────────────┬─────────────────────────────────────────┘
                                │
        ┌───────────────────────┼───────────────────────┐
        │                       │                       │
        ▼                       ▼                       ▼
┌───────────────┐       ┌───────────────┐       ┌───────────────┐
│   LOVABLE     │       │      V0       │       │     BOLT      │
│   (MCP)       │       │   (API)       │       │   (Link)      │
├───────────────┤       ├───────────────┤       ├───────────────┤
│ Create Project│       │ Create Chat   │       │ Open External │
│ Retrieve Data │       │ Get Preview   │       │ URL with      │
│               │       │               │       │ Prompt        │
└───────────────┘       └───────────────┘       └───────────────┘
        │                       │                       │
        └───────────────────────┼───────────────────────┘
                                ▼
                    ┌───────────────────┐
                    │  DEMO ENGINE      │
                    │  (Local Fallback) │
                    ├───────────────────┤
                    │ Generates Static  │
                    │ HTML/CSS/JS       │
                    │ Files in Memory   │
                    └───────────────────┘

📦 Export

When a project is generated:

    Files are written to ~/.nexus_web_forge/{project_id}/ (or memory if no disk access).

    A ZIP archive is generated on demand via the /api/zip endpoint.

    A live preview is available if the engine returns a preview_url.

🔐 Security & Sovereignty

    Zero Cloud Dependency: The demo engine works entirely offline.

    No Telemetry: Nexus Web Forge does not track, log, or transmit your data.

    Local Execution: All code generation, file writing, and ZIP creation happens on your machine.

    Optional API Keys: If you use v0 or Lovable, your keys are stored in your environment, never in the repository.

🛠️ Development
API Endpoints
Method	Endpoint	Description
GET	/	Main UI
GET	/api/engines	Engine availability status
GET	/api/file?project=...&name=...	Retrieve a file's content
GET	/api/zip?id=...	Download a ZIP
POST	/api/forge	Generate a project
Example Request
bash

curl -X POST http://127.0.0.1:9999/api/forge \
  -H "Content-Type: application/json" \
  -d '{"prompt": "Create a SaaS landing page with dark mode", "engine": "demo"}'

🧬 Author

Aissa Mohammedi (DGK)
github.com/Aissamohammedi88

Architect of the Nexus Ecosystem.
📜 License

NEXUS-OPEN-3.0 — See LICENSE for details.

    Free for personal, educational, and research use.

    Commercial use permitted with attribution.

    Modifications must be documented.

<div align="center"><svg width="600" height="40" viewBox="0 0 600 40" xmlns="http://www.w3.org/2000/svg"> <defs> <linearGradient id="endGrad" x1="0%" y1="0%" x2="100%" y2="0%"> <stop offset="0%" stop-color="#00ff9d" stop-opacity="0"/> <stop offset="50%" stop-color="#00ff9d" stop-opacity="1"/> <stop offset="100%" stop-color="#00ff9d" stop-opacity="0"/> </linearGradient> </defs> <line x1="0" y1="20" x2="600" y2="20" stroke="url(#endGrad)" stroke-width="2"/> <text x="300" y="28" text-anchor="middle" font-family="ui-monospace, monospace" font-size="13" fill="#a0a0a0" font-style="italic"> « Code is the only sovereignty that cannot be delegated. » <animate attributeName="opacity" values="0.4;1;0.4" dur="4s" repeatCount="indefinite"/> </text> </svg>

Made with ⚡ by Aissa Mohammedi (DGK) · 2026 · NEXUS OPEN SOURCE
</div> ```
