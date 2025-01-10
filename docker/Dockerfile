FROM ubuntu:24.04

# Set environment variables
ENV SCRIPTRUNNER_USER="scriptrunner"
ENV SCRIPTRUNNER_USER_HOME="/usr/local/$SCRIPTRUNNER_USER"

# Switch to root user
USER root

# Create a non-root user
RUN useradd --shell /bin/bash -d "$SCRIPTRUNNER_USER_HOME" -m -u 1001 "$SCRIPTRUNNER_USER"

# Update and upgrade packages on base docker image
RUN apt-get update && apt-get upgrade

# Switch to non-root user
USER "$SCRIPTRUNNER_USER"

# Set working directory
WORKDIR "$SCRIPTRUNNER_USER_HOME"