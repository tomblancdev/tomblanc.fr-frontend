FROM mcr.microsoft.com/devcontainers/typescript-node:latest as builder

ARG USER=root

USER ${USER}

# update and install required packages
RUN apt-get update && apt-get upgrade -y

FROM builder as development
ENV APP_HOME="/workspace"
CMD /bin/sh -c "while sleep 1000; do :; done"

FROM builder as production
ENV APP_HOME="/app"
COPY . ${APP_HOME}
WORKDIR ${APP_HOME}
RUN bun install
run bun run build
CMD bun --bun start
