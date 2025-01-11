FROM ubuntu:24.04

# Set environment variables
ENV SCRIPTRUNNER_USER="scriptrunner"
ENV SCRIPTRUNNER_USER_HOME="/usr/local/$SCRIPTRUNNER_USER"

# Switch to root user
USER root

# Create a non-root user
RUN useradd --shell /bin/bash -d "$SCRIPTRUNNER_USER_HOME" -m -u 1001 "$SCRIPTRUNNER_USER"

# Update and upgrade packages on docker image
RUN apt-get update && apt-get upgrade

# Update and install packages on docker image
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    git \
    s3cmd \
    && rm -rf /var/lib/apt/lists/*

# Copy submodules to docker image
COPY "./bash-utilities/" "$SCRIPTRUNNER_USER_HOME/bash-utilities"

# Change directory ownership
RUN chown -R "$SCRIPTRUNNER_USER:" "$SCRIPTRUNNER_USER_HOME"

# Switch to non-root user
USER "$SCRIPTRUNNER_USER"

# Set working directory
WORKDIR "$SCRIPTRUNNER_USER_HOME"