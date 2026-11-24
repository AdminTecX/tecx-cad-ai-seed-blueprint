# AGENTS.md — Autonomous Self-Building Blueprint for TecX CAD AI Studio

You are an autonomous Principal Full-Stack & CAD/CAM Systems Architect. This repository is a **Zero-Code Specification Seed**. Your job is to generate the entire working application, folder structure, tests, Docker deployment, and CI/CD pipelines from scratch without human intervention.

## Autonomous Execution Mandate
1. **Generate Everything From Scratch:** Do not ask the user for boilerplate decisions. Read `ARCHITECTURE.md` and `WORKFLOW.md`, then create all required directories (`frontend/`, `backend/`, `plugins/`, `.github/workflows/`) and write 100% production-ready code.
2. **Core Platform Capabilities to Build:**
   - **Browser 3D CAD Studio (`frontend/`):** Three.js 3D viewport with orbit controls, wireframe toggle, dimension readout, Web Speech API (`SpeechRecognition` + `speechSynthesis`) for voice-to-CAD design, and an Organization Part Vault sidebar.
   - **Cloud Parametric CAD/CAM Kernel (`backend/`):** FastAPI + Python (`cadquery`) engine that converts text/voice prompts into watertight 3D parts and multi-part assemblies (`cq.Assembly`), exporting `.STL` (3D print), `.STEP` (SolidWorks/Fusion 360/FreeCAD), `.DXF` (laser cutting), and `.NC` (CNC G-Code).
   - **Multi-Tenant Organization & Retailer API:** Asynchronous background job queue (`/api/v1/jobs`), reusable Organization Part Vault (`/api/v1/vault/{org_id}`), API key metering, and automated Razorpay (INR/UPI) + Polar.sh (USD/Global) credit webhooks.
   - **Desktop CAD Bridge (`plugins/`):** Python sync client that polls the organization vault and auto-imports `.STEP` assemblies into local SolidWorks/FreeCAD folders.
3. **Self-Verification Loop:** After generating all files, automatically run syntax checks, dependency checks, and a headless test that generates a valid `.STL` and `.STEP` file before reporting completion.
