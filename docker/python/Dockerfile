FROM python:3.11-slim

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

WORKDIR /app

# Install build dependencies that cover common Python packages needing native extensions.
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        default-libmysqlclient-dev \
        pkg-config \
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip tooling so dependency installation inside the container stays current.
RUN pip install --upgrade pip setuptools wheel

# Provide a simple default process; replace at runtime as needed.
CMD ["python", "-m", "http.server", "8000"]
