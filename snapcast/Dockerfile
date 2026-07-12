ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Copy data for add-on
COPY rootfs /

RUN printf "@edge http://dl-cdn.alpinelinux.org/alpine/edge/main\n@edge http://dl-cdn.alpinelinux.org/alpine/edge/community\n@edge http://dl-cdn.alpinelinux.org/alpine/edge/testing\n" >> /etc/apk/repositories
RUN apk update

RUN apk update \
    && apk add --no-cache \
        alsa-plugins-pulse \
        avahi \
        dbus \
        librespot@edge \
        shairport-sync \
        snapcast-client \
        snapcast-server \
        snapweb@edge

# shairport-sync ships a D-Bus policy referencing this user; create it
RUN addgroup -S shairport-sync \
    && adduser -S -D -H -G shairport-sync shairport-sync
