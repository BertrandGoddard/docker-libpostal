FROM alpine:3.15

LABEL version="1.1.0" \
      maintainer="sleekybadger@gmail.com"

ENV LIBPOSTAL_VERSION="1.1" \
    LIBPOSTAL_DOWNLOAD_URL="https://github.com/openvenues/libpostal/archive/v1.1.tar.gz" \
    LIBPOSTAL_DOWNLOAD_SHA="8cc473a05126895f183f2578ca234428d8b58ab6fadf550deaacd3bd0ae46032"

RUN set -ex \
        \
        && apk add --no-cache --virtual .build-deps \
                curl \
                gcc \
                g++ \
                make \
                libtool \
                autoconf \
                automake \
        \
        && wget -O libpostal.tar.gz "$LIBPOSTAL_DOWNLOAD_URL" \
        && echo "$LIBPOSTAL_DOWNLOAD_SHA *libpostal.tar.gz" | sha256sum -c - \
        \
        && mkdir -p /src  \
        && mkdir -p /data \
        \
        && tar -xzf libpostal.tar.gz -C /src --strip-components=1 \
        && rm libpostal.tar.gz \
        && cd /src \
        \
        && autoreconf -fi --warning=no-syntax --warning=no-portability \
        && ./configure --prefix=/usr --datadir=/data \
        \
        && make -j "$(nproc)" \
        && make install \
        \
        && apk del .build-deps \
        && rm -rf /src
