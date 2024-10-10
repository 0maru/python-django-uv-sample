<<<<<<< HEAD
ARG PYTHON_VERSION="3.11.9"

FROM ghcr.io/astral-sh/uv:python${PYTHON_VERSION%.*}-bookworm-slim as builder
ENV UV_LINK_MODE=copy \
    UV_COMPILE_BYTECODE=1 \
    UV_PYTHON_DOWNLOADS=never \
    UV_PYTHON=python${PYTHON_VERSION%.*}

WORKDIR /app
COPY ./pyproject.toml /app
COPY ./uv.lock /app

#
RUN cd /app && \
    uv sync --frozen --no-install-project

FROM python:${PYTHON_VERSION}-slim-bookworm as runtime

ENV PATH=/app/.venv/bin:$PATH

WORKDIR /app
COPY hello.py /app
COPY --from=build /app /app

EXPOSE 8080

CMD [ "python", "manage.py", "runserver" ]
||||||| aa7666e
=======
ARG PYTHON_VERSION="3.12.6"

# Astral社が提供しているPythonイメージをベースにする
FROM ghcr.io/astral-sh/uv:python${PYTHON_VERSION%.*}-bookworm-slim as build

ENV UV_LINK_MODE=copy \
    UV_COMPILE_BYTECODE=1 \
    UV_PYTHON_DOWNLOADS=never \
    UV_PYTHON=python${PYTHON_VERSION%.*}

WORKDIR /app
COPY ./pyproject.toml /app
COPY ./uv.lock /app

RUN --mount=type=cache,target=/root/.cache \
    set -ex && \
    cd /app && \
    uv sync --frozen --no-install-project

COPY hello.py /app

FROM python:${PYTHON_VERSION}-slim-bookworm

ENV PATH=/app/.venv/bin:$PATH

WORKDIR /app

COPY --from=build /app /app

EXPOSE 8080

CMD [ "python", "hello.py" ]
>>>>>>> refs/remotes/origin/main
