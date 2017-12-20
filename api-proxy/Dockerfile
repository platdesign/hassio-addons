ARG BUILD_FROM=hassioaddons/base-amd64:1.2.0
FROM ${BUILD_FROM}

# Copy root filesystem
COPY rootfs /

# Setup base
RUN \
    apk add --no-cache --virtual .build-dependencies \
    && apk add --no-cache \
        git \
        nodejs \
        nodejs-npm \
    \
    && npm set unsafe-perm true

# Create app directory
WORKDIR /usr/src

RUN git clone https://github.com/platdesign/hassio-addon-api_proxy.git .

WORKDIR /usr/src/app

RUN npm install --production

ENV NODE_ENV=production

EXPOSE 8080
CMD [ "npm", "start" ]


# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="ApiProxy" \
    io.hass.description="ApiProxy with auth for public access" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Christian Blaschke <mail@platdesign.de>" \
    org.label-schema.description="ApiProxy with auth for public access" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="ApiProxy" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://community.home-assistant.io/t/community-hass-io-add-on-homebridge/33803?u=frenck" \
    org.label-schema.usage="https://github.com/platdesign/hassio-addon-api_proxy" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/platdesign/hassio-addon-api_proxy" \
    org.label-schema.vendor="Platdesign"



