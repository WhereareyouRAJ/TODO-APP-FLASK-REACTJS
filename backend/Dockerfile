
# Stage 1: Base image
# This stage sets up the base environment for the Flask application.
FROM python:3.11-slim AS base

# Environment variables for Python
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1

# Install system dependencies
# This stage installs the necessary system packages for building the application.
RUN apt-get update && apt-get install -y \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Setting up the working directory
# This stage creates a directory for the application code.
WORKDIR /app

# Copying the requirements file
# This stage copies the requirements file into the container.
COPY requirements.txt .

# Installing Python dependencies
# This stage installs the Python packages specified in the requirements file.
RUN pip install --no-cache-dir -r requirements.txt gunicorn

# Copying the application code
# This stage copies the entire application code into the container.
COPY . . 

# Exposing the application port
# This stage exposes port 5000 for the Flask application.
EXPOSE 5000

# Environment variables for Flask
# This stage sets the environment variables for Flask.
ENV FLASK_APP=application.py
ENV FLASK_RUN_HOST=0.0.0.0
ENV FLASK_RUN_PORT=5000

# Command to run the application
# This stage runs the Flask application using Gunicorn.
CMD ["sh", "-c", "flask db upgrade && gunicorn --bind 0.0.0.0:5000 'application:app'"]