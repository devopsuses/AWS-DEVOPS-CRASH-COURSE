# [Choice] Debian version (use bullseye on local arm64/Apple Silicon): bullseye, buster
	# checkov:skip=CKV_DOCKER_2: Healthcheck not needed for devcontainer
	# checkov:skip=CKV_DOCKER_3: User is created in base image
ARG VARIANT=bullseye
FROM mcr.microsoft.com/vscode/devcontainers/base:${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends python3 python3-pip golang
