# Flask CI/CD Starter

Tiny Flask service exposing `/health` for CI/CD practice.

## Run locally
```bash
pip install -r requirements.txt
python app/app.py
# curl http://localhost:8080/health

docker build -t flask-cicd-starter -f docker/Dockerfile .
docker run --rm -p 8080:8080 flask-cicd-starter
# curl http://localhost:8080/health

