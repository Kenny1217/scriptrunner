FROM ubuntu:25.04

ENV SCRIPTRUNNER_USER="scriptrunner"
ENV SCRIPTRUNNER_HOME="/usr/local/$SCRIPTRUNNER_USER"

USER root

RUN useradd --shell /bin/bash -d "$SCRIPTRUNNER_HOME" -m -u 1001 "$SCRIPTRUNNER_USER"

RUN apt-get update && apt-get upgrade && apt-get install -y --no-install-recommends \
    curl \
    git \
    jq \
    s3cmd \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*


RUN chown -R "$SCRIPTRUNNER_USER": "$SCRIPTRUNNER_HOME"

USER $SCRIPTRUNNER_USER

WORKDIR "$SCRIPTRUNNER_HOME"