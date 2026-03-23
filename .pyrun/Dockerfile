FROM public.ecr.aws/docker/library/python:3.12-slim-bullseye

# Install system dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    gcc \
    git \
    curl \
    openssh-client \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Install Node.js (required for skills and agent tools)
RUN curl -fsSLO "https://nodejs.org/dist/v20.11.1/node-v20.11.1-linux-x64.tar.gz" \
    && tar -xzf "node-v20.11.1-linux-x64.tar.gz" -C /usr/local --strip-components=1 --no-same-owner \
    && rm "node-v20.11.1-linux-x64.tar.gz"

# Create the specific user and its home directory
RUN useradd -m -s /bin/bash pyrunuser

# Ensure Python output is not buffered
ENV PYTHONUNBUFFERED=TRUE

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

# Cleaning apt packages
RUN apt-get purge -y --auto-remove gcc \
    && rm -rf /var/lib/apt/lists/*

# Switch to the specific user to install tools in their local directory
USER pyrunuser

# Install skills using npx (cleaning cache to save space)
RUN npx -y skills add vercel-labs/agent-skills \
    && npm cache clean --force

# --- COPILOT INSTALLATION SECTION ---
# Download and execute the Copilot installer
RUN curl -fsSL https://gh.io/copilot-install | bash

# Set the PATH permanently for the Docker environment
ENV PATH="/home/pyrunuser/.local/bin:${PATH}"

# Ensure interactive shells (like 'docker exec -it') also load the new PATH
RUN echo 'export PATH="/home/pyrunuser/.local/bin:$PATH"' >> ~/.bashrc

# -- OPENCODE INSTALLATION SECTION --
# Install OpenCode using curl
RUN curl -fsSL https://opencode.ai/install | bash
