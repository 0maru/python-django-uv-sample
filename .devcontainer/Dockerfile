# Astral社が提供しているPythonイメージをベースにする
FROM ghcr.io/astral-sh/uv:python3.10-bookworm

# ENV UV_LINK_MODE=copy \
#     UV_COMPILE_BYTECODE=1 \
#     UV_PYTHON_DOWNLOADS=never \
#     UV_PYTHON=python${PYTHON_VERSION%.*}

WORKDIR /app
COPY . /app
