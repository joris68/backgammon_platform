FROM python:3.12-slim

# Build tools installieren
RUN apt-get update && apt-get install -y \
    gcc \
    g++ \
    && rm -rf /var/lib/apt/lists/*

COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

COPY . /backgammon_service
WORKDIR /backgammon_service

RUN uv sync --frozen --no-cache

RUN uv pip install fastapi[standard]

# Run the application.
CMD [".venv/bin/fastapi", "run", "main.py", "--port", "8001", "--host", "0.0.0.0"]