# ---- Stage 1: deps ----
FROM python:3.11-slim AS deps
WORKDIR /app

# (Optional but common) toolchain for native wheels; harmless here
RUN apt-get update && apt-get install -y --no-install-recommends build-essential gcc \
    && rm -rf /var/lib/apt/lists/*

# Copy only requirements first to maximize cache hits
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# ---- Stage 2: runtime ----
FROM python:3.11-slim AS runtime
WORKDIR /app
ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1

# Reuse installed deps (site-packages and scripts) from deps stage
COPY --from=deps /usr/local /usr/local

# Copy your app code last (changes often)
COPY app ./app

EXPOSE 8080
CMD ["python", "-m", "app.app"]
