FROM ubuntu:24.04

# Set environment variables
ENV SCRIPTRUNNER_USER "scriptrunner"
ENV SCRIPTRUNNER_HOME "/home/${SCRIPTRUNNER_USER}"

# Switch to root user
USER root

# Create non-root user
RUN useradd --shell /bin/bash -d ${SCRIPTRUNNER_HOME} -m -u 1001 ${SCRIPTRUNNER_USER}

# Update and install required packages
RUN apt update && apt install -y --no-install-recommends \
    curl \
    git \
    && rm -rf /var/lib/apt/lists/*

# Switch to non-root user
USER 1001

# Set work directory
WORKDIR ${SCRIPTRUNNER_HOME} 
