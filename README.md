![CI](https://github.com/anveshyeruva/flask-cicd-starter/actions/workflows/ci.yml/badge.svg)

# Flask CI/CD Starter

Tiny Flask service exposing `/health` for CI/CD practice.

## Highlights
- **End-to-end CI/CD** with GitHub Actions (test + Docker build jobs).
- **Baseline vs Optimized runs** documented with timings and proof screenshots.
- **Pip cache** → steadier dependency installs across runs.
- **Docker BuildKit cache** → demonstrated warm vs restored cache behavior.
- **Multi-stage Dockerfile** → industry best practice separating deps and runtime layers.
- Full performance tracking in [docs/PERFORMANCE.md](./docs/PERFORMANCE.md).

## Run locally (no Docker)
```bash
pip install -r requirements.txt
python app/app.py
# Test endpoint
curl http://localhost:8080/health
