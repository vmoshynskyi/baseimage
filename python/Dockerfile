FROM python:3.13.2-alpine3.21

LABEL maintainer="Vadym Moshynskyi <v@moshynskyi.com>"

SHELL ["/bin/ash", "-eo", "pipefail", "-c"]

RUN addgroup --system --gid 1001 app \
    && adduser --system --disabled-password --home /app --uid 1001 --ingroup app app

ENV PYTHONDONTWRITEBYTECODE=true \
    PYTHONIOENCODING=UTF-8 \
    UV_VERSION=0.6.9 \
    UV_INSTALL_DIR="/opt/uv" \
    UV_PROJECT_ENVIRONMENT="/usr/local/"

ENV PATH="${UV_INSTALL_DIR}:${PATH}"

RUN apk --no-cache add \
    git \
    curl \
    gcc \
    libc-dev \
    libffi-dev

RUN curl -sSL "https://astral.sh/uv/${UV_VERSION}/install.sh" | sh

RUN uv --version
