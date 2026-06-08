# SPDX-FileCopyrightText: © 2026 Team CharLS
# SPDX-License-Identifier: BSD-3-Clause
# Note: This Dockerfile is based on Microsoft VS Code dev container templates.
#       See https://github.com/microsoft/devcontainers for the originals.

FROM docker.io/emscripten/emsdk:6.0.0

# Avoid warnings by switching to noninteractive
ENV DEBIAN_FRONTEND=noninteractive

# Configure apt and install packages
RUN apt-get update \
    && apt-get -y install --no-install-recommends \
    #
    # Install C++ development tools
    build-essential \
    cmake \
    ninja-build \
    gdb \
    cppcheck \
    clang-format \
    clang-tidy \
    #
    # Install utilities
    git \
    curl \
    wget \
    zip \
    unzip \
    ca-certificates \
    #
    # Install Node.js (LTS version via NodeSource)
    && curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs \
    #
    # Clean up
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*

# Switch back to dialog for any ad-hoc use of apt-get
ENV DEBIAN_FRONTEND=dialog

# Set the default user to emscripten (already exists in base image)
USER emscripten
