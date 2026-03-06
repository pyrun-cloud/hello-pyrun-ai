FROM public.ecr.aws/docker/library/python:3.12-slim-bullseye

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    git \
    curl \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Create the specific user and its home directory
RUN useradd -m -s /bin/bash pyrunuser

# Set up the function directory (standard for cloud function environments)
ARG FUNCTION_DIR="/function"
RUN mkdir -p ${FUNCTION_DIR} && chown pyrunuser:pyrunuser ${FUNCTION_DIR}
WORKDIR ${FUNCTION_DIR}

# Install Python packages using pip (Lithops & Dask)
ARG LITHOPS
RUN pip install --no-cache-dir \
    pandas \
    numpy \
    requests \
    "$LITHOPS" \
    dask \
    dask-cloudprovider \
    uv \
    "dask-cloudprovider[ibm] @ git+https://github.com/dask/dask-cloudprovider.git"

# --- COPILOT INSTALLATION SECTION ---
# Switch to the specific user to install Copilot in their local directory
USER pyrunuser

# Download and execute the Copilot installer
RUN curl -fsSL https://gh.io/copilot-install | bash

# Set the PATH permanently for the Docker environment
ENV PATH="/home/pyrunuser/.local/bin:${PATH}"

# Ensure interactive shells (like 'docker exec -it') also load the new PATH
RUN echo 'export PATH="/home/pyrunuser/.local/bin:$PATH"' >> ~/.bashrc

# Ensure Python output is not buffered
ENV PYTHONUNBUFFERED=TRUE