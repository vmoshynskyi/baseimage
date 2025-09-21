FROM python:3.12.11-slim-trixie

LABEL maintainer="Vadym Moshynskyi <v@moshynskyi.com>"

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN addgroup --system --gid 1001 app \
    && adduser --system --disabled-password --home /app --uid 1001 --ingroup app app

ENV PYTHONDONTWRITEBYTECODE=true \
    PYTHONIOENCODING=UTF-8 \
    POETRY_VERSION=2.1.1 \
    POETRY_HOME="/opt/poetry" \
    POETRY_VIRTUALENVS_CREATE=false

ENV PATH="${POETRY_HOME}/bin:${PATH}"

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        curl \
        gcc \
        libc-dev \
        libffi-dev \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://install.python-poetry.org | python3 -

RUN poetry --version
