ARG BUILD_FROM
# hadolint ignore=DL3006
# Using deftdawg fork which adds /api/v1/rpc, /api/v1/events, /api/v1/check endpoints
# for signal-cli daemon HTTP API compatibility (required for openclaw integration)
FROM ghcr.io/deftdawg/signal-cli-rest-api:latest

COPY options.sh /options.sh

RUN ["chmod", "+x", "/options.sh"]

RUN apt-get clean \

        && apt-get update \

        && apt-get install -y --no-install-recommends jq

# WORKDIR /config/data/

ENTRYPOINT ["/options.sh"]

VOLUME ["/config"]

# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="Signal Messenger" \
    io.hass.description="Signal Messenger" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.version="${BUILD_VERSION}" \
    io.hass.type="addon" \
    maintainer="haberda" \
    org.label-schema.description="Signal Messenger" \
    org.label-schema.build-date="${BUILD_DATE}" \
    org.label-schema.name="Signal Messenger" \
    org.label-schema.schema-version="${BUILD_VERSION}" \
    org.label-schema.url="https://github.com/deftdawg/signal-addon" \
    org.label-schema.usage="https://github.com/deftdawg/signal-addon" \
    org.label-schema.vcs-ref="${BUILD_REF}" \
    org.label-schema.vcs-url="https://github.com/deftdawg/" \
    org.label-schema.vendor="No Vendor"

