FROM python:3.12-slim as builder

ARG DEPLOY_TARGET=/app/

# Install Python Packages
WORKDIR ${DEPLOY_TARGET}
COPY pyproject.toml poetry.lock ${DEPLOY_TARGET}
RUN pip3 install poetry=="1.8.2" poethepoet \
    && poetry config virtualenvs.create false \
    && poetry install --no-interaction

# PYTHONPATHを通す
ENV PYTHONPATH ${PYTHONPATH}:${DEPLOY_TARGET}

# logger用の環境変数
ENV VALIDATION_MODE=debug

# Setting Run Option
USER root
