# Update the NODE_VERSION arg in docker-compose.yml to pick a Node version: 18, 20
# NOTE: use a "-bookworm" tag, not the old default (bullseye), so the base image's
# glibc is new enough for current Hugo release binaries.
ARG NODE_VERSION=26-bookworm
FROM mcr.microsoft.com/devcontainers/javascript-node:${NODE_VERSION}

# VARIANT can be either 'hugo' for the standard version or 'hugo_extended' for the extended version.
ARG VARIANT=hugo_extended
# VERSION can be either 'latest' or a specific version number
ARG VERSION=latest

# Download Hugo
RUN apt-get update && apt-get install -y ca-certificates openssl git curl && \
    rm -rf /var/lib/apt/lists/* && \
    case ${VERSION} in \
    latest) \
    export VERSION=$(curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest | grep "tag_name" | awk '{print substr($2, 3, length($2)-4)}') ;;\
    esac && \
    echo ${VERSION} && \
    case $(uname -m) in \
    aarch64) \
    export ARCH=ARM64 ;; \
    *) \
    export ARCH=64bit ;; \
    esac && \
    echo ${ARCH} && \
    wget -O ${VERSION}.tar.gz https://github.com/gohugoio/hugo/releases/download/v${VERSION}/${VARIANT}_${VERSION}_Linux-${ARCH}.tar.gz && \
    tar xf ${VERSION}.tar.gz && \
    mv hugo /usr/bin/hugo

# Download Dart Sass (needed by layouts/_partials/head/style.html; libsass is deprecated in Hugo).
# Use the standalone release, not the npm `sass` package, which Hugo cannot use.
ARG DART_SASS_VERSION=latest
RUN case ${DART_SASS_VERSION} in \
    latest) \
    export DART_SASS_VERSION=$(curl -s https://api.github.com/repos/sass/dart-sass/releases/latest | grep "tag_name" | awk '{print substr($2, 2, length($2)-3)}') ;;\
    esac && \
    echo ${DART_SASS_VERSION} && \
    case $(uname -m) in \
    aarch64) \
    export SASS_ARCH=arm64 ;; \
    *) \
    export SASS_ARCH=x64 ;; \
    esac && \
    curl -fsSL https://github.com/sass/dart-sass/releases/download/${DART_SASS_VERSION}/dart-sass-${DART_SASS_VERSION}-linux-${SASS_ARCH}.tar.gz \
    | tar -xz -C /usr/local/lib && \
    ln -s /usr/local/lib/dart-sass/sass /usr/local/bin/sass && \
    sass --version

# Hugo dev server port
EXPOSE 1313

# [Optional] Uncomment this section to install additional OS packages you may want.
#
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment if you want to install more global node packages
# RUN sudo -u node npm install -g <your-package-list-here>