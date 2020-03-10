FROM alpine:edge

WORKDIR /data

RUN apk -U add curl cargo portaudio-dev protobuf-dev \
 && cd /root \
 && curl -LO https://github.com/librespot-org/librespot/archive/master.zip \
 && unzip master.zip \
 && cd librespot-master \
 && cargo build --jobs $(grep -c ^processor /proc/cpuinfo) --release --no-default-features \
 && mv target/release/librespot /usr/local/bin \
 && mkfifo /var/cache/snapcast/snapfifo \
 && cd / \
 && apk --purge del curl cargo portaudio-dev protobuf-dev \
 && apk add llvm-libunwind \
 && rm -rf /etc/ssl /var/cache/apk/* /lib/apk/db/* /root/master.zip /root/librespot-master /root/.cargo

ENV SYSTEM_OUTPUT_VOLUME 100
ENV DEVICE_NAME SpotifyMultiroom
ENV SPOTIFY_BACKEND pipe
ENV SPOTIFY_DEVICE /var/cache/snapcast/snapfifo

# Start raspotify
CMD librespot \
  --bitrate 320 \
  --cache /var/cache/raspotify \
  --enable-volume-normalisation \
  --linear-volume \
  --name "$DEVICE_NAME" \
  --initial-volume=$SYSTEM_OUTPUT_VOLUME \
  --backend "$SPOTIFY_BACKEND" \
  --device "$SPOTIFY_DEVICE" \
  -u "$SPOTIFY_LOGIN" \
  -p "$SPOTIFY_PASSWORD"
