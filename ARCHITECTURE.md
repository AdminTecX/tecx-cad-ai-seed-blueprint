# System Architecture Specification — TecX CAD AI Studio

## 1. High-Level Data & Manufacturing Flow
- **Input Layer:** Browser UI (Voice & Text Prompt) OR External Retailer / Desktop CAD Agent via REST API (`X-API-Key`).
- **Orchestration Layer:** FastAPI server queueing asynchronous background CAD/CAM jobs per `org_id` and deducting API credits.
- **Geometry & Assembly Kernel:** LLM translates prompt + existing `VAULT_PARTS` metadata into sandboxed Python `cadquery` code -> builds single part or `cq.Assembly()` -> exports `.STL`, `.STEP`, `.DXF`, and `.NC` G-Code -> saves metadata JSON to Organization Vault.
- **Desktop Interoperability:** Local SolidWorks / Fusion 360 / FreeCAD bridge script watches the organization's vault API and pulls new `.STEP` files automatically.
- **Automated Billing:** Razorpay (`payment.captured`) and Polar.sh (`order.paid`) webhooks verify signatures and credit organization balances automatically.

## 2. Target Directory Structure to Generate
```text
├── frontend/
│   ├── index.html          # 3-column CAD UI: Voice/Prompt Console, 3D Viewport, Part Vault
│   ├── style.css           # Dark-mode engineering studio styling
│   └── studio.js           # Three.js STL viewer, SpeechRecognition voice loop, job poller
├── backend/
│   ├── Dockerfile          # Python 3.11 + OpenCascade/CadQuery container
│   ├── requirements.txt    # fastapi, uvicorn, cadquery, google-genai, pydantic
│   ├── main.py             # Multi-tenant FastAPI endpoints, background workers & webhooks
│   ├── cad_engine.py       # Sandboxed CadQuery executor, Assembly builder & 4-format exporter
│   └── billing.py          # Org provisioning, X-API-Key credit metering & webhook verification
├── plugins/
│   └── cad_desktop_sync.py # Local SolidWorks / FreeCAD .STEP auto-importer
├── docker-compose.yml      # Full stack container deployment
├── render.yaml             # One-click cloud blueprint with persistent vault disk
└── .env.example            # Environment variable template
```
