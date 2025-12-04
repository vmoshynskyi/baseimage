FROM python:3.14.1-slim-trixie

LABEL maintainer="Vadym Moshynskyi <v@moshynskyi.com>"

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN addgroup --system --gid 1001 app \
    && adduser --system --disabled-password --home /app --uid 1001 --ingroup app app

ENV PYTHONDONTWRITEBYTECODE=true \
    PYTHONIOENCODING=UTF-8 \
    UV_VERSION=0.9.15 \
    UV_INSTALL_DIR="/opt/uv" \
    UV_PROJECT_ENVIRONMENT="/usr/local/"

ENV PATH="${UV_INSTALL_DIR}:${PATH}"

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        git \
        curl \
        gcc \
        libc-dev \
        libffi-dev \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sSL "https://astral.sh/uv/${UV_VERSION}/install.sh" | sh

RUN uv --version
