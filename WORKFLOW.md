# Autonomous Build Workflow (5 Phases)

Execute these 5 phases in order:

1. **Phase 1 — Backend CAD & Assembly Kernel:** Create `backend/requirements.txt`, `backend/cad_engine.py`, and `backend/billing.py`. Verify that `cad_engine.py` supports both single `cq.Workplane` parts and `cq.Assembly` multi-part builds using previously saved `.STEP` files from `org_vault/{org_id}/`.
2. **Phase 2 — Multi-Tenant API & Webhooks:** Create `backend/main.py` exposing `/api/v1/orgs/{org_id}/provision`, `/api/v1/jobs`, `/api/v1/jobs/{job_id}`, `/api/v1/vault/{org_id}`, `/api/v1/webhooks/razorpay`, and `/api/v1/webhooks/polar`.
3. **Phase 3 — Browser Voice & 3D CAD Studio:** Create `frontend/index.html`, `frontend/style.css`, and `frontend/studio.js` using Three.js `STLLoader` + `OrbitControls` and browser `SpeechRecognition` + `speechSynthesis`.
4. **Phase 4 — Desktop CAD Sync & Cloud DevOps:** Create `plugins/cad_desktop_sync.py`, `backend/Dockerfile`, `docker-compose.yml`, `render.yaml`, `.env.example`, and `.github/workflows/ci-deploy.yml`.
5. **Phase 5 — Automated Self-Test:** Run `python3 -m py_compile backend/*.py plugins/*.py` and validate all HTML/JSON/YAML files. Output a summary of generated endpoints and deployment commands.
