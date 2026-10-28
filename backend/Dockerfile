
FROM python:3.12-slim-trixie@sha256:6b25cbe6577518889d553cdd5a5da97d259348d8f6e45b527dd731caaba27a07

ARG APP_VERSION=0.2

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1 \
    APP_VERSION=${APP_VERSION}

WORKDIR /app

RUN apt-get update \
    && apt-get upgrade -y \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir -r requirements.txt

RUN groupadd --system appgroup \
    && useradd --system --gid appgroup --home-dir /app appuser

COPY --chown=appuser:appgroup app.py .

USER appuser

EXPOSE 5000
CMD ["python", "app.py"]
