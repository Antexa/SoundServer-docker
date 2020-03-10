FROM alpine:edge

WORKDIR /data

ENV BUILD_PACKAGES=git \
                   build-base \
                   autoconf \
                   automake \
                   libtool \
                   libdaemon-dev \
                   popt-dev \
                   libressl-dev \
                   soxr-dev \
                   avahi-dev \
                   libconfig-dev

ENV PACKAGES=libdaemon \
             libgcc \
             popt \
             libressl \
             soxr \
             libconfig

RUN apk --no-cache add \
      git \
      build-base \
      autoconf \
      automake \
      libtool \
      libdaemon-dev \
      popt-dev \
      libressl-dev \
      soxr-dev \
      avahi-dev \
      libconfig-dev

RUN apk --no-cache add \
      libdaemon \
      libgcc \
      popt \
      libressl \
      soxr \
      libconfig

RUN apk --no-cache add ${BUILD_PACKAGES} ${PACKAGES} \
       && git clone --depth=1 --recursive https://github.com/mikebrady/shairport-sync.git \
       && cd /tmp/shairport-sync \
       && autoreconf -i -f \
       &&   ./configure \
              --with-tinysvcmdns \
              --with-pipe \
              --with-ssl=openssl \
              --with-soxr \
       && make \
       && make install \
       && cd /tmp \
       && rm -rf /tmp/shairport-sync \
       && apk --no-cache --purge del ${BUILD_PACKAGES}

ENV DEVICE_NAME Airplay Multiroom
ENV SHAIRPORT_BACKEND "-o pipe -- /var/cache/snapcast/snapfifo"

# Start AirPlay
CMD shairport-sync \
  -a "$DEVICE_NAME" \
  $SHAIRPORT_BACKEND
