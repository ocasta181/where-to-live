# syntax=docker/dockerfile:1

# Base image for both development and production
FROM python:3.11-slim as base

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install uv for faster package installation
RUN curl -LsSf https://astral.sh/uv/install.sh | sh

# Set working directory
WORKDIR /app

# Development stage
FROM base as development

# Copy dependency files
COPY pyproject.toml .

# Install dependencies using uv
RUN uv pip install -e ".[dev]"

# Production stage
FROM base as production

# Copy dependency files
COPY pyproject.toml .

# Install production dependencies only
RUN uv pip install .

# Copy application code
COPY . .

# Run the application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
