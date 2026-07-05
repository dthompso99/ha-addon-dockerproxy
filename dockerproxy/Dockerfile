ARG BUILD_VERSION
ARG BUILD_ARCH

FROM ghcr.io/dthompso99/dockerproxy:main

ARG BUILD_VERSION
ARG BUILD_ARCH

LABEL \
  io.hass.version="${BUILD_VERSION}" \
  io.hass.type="app" \
  io.hass.arch="${BUILD_ARCH}"

USER 0:0
