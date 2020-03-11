FROM alpine:edge

ENV GITHUB_ORGANIZATION librespot-org
ENV LIBRESPOT_VERSION v0.1.1

WORKDIR /data

RUN apk -U add curl cargo portaudio-dev protobuf-dev git libgcc \
 && git clone -b ${LIBRESPOT_VERSION} --depth 1 https://github.com/${GITHUB_ORGANIZATION}/librespot.git librespot \
 && cd librespot \
 && cargo build --jobs $(grep -c ^processor /proc/cpuinfo) --release --no-default-features \
 && mv target/release/librespot /usr/local/bin \
 && cd / \
 && apk --purge del curl cargo portaudio-dev protobuf-dev git \
 && apk add llvm-libunwind \
 && rm -rf /etc/ssl /var/cache/apk/* /lib/apk/db/* /data/librespot /root/.cargo

ENV CACHE_FOLDER /var/cache/raspotify
ENV SPOTIFY_BACKEND pipe
ENV SPOTIFY_DEVICE /var/cache/snapcast/snapfifo

# Start raspotify
CMD librespot \
  --bitrate 320 \
  --cache "$CACHE_FOLDER" \
  --enable-volume-normalisation \
  --linear-volume \
  --name "$DEVICE_NAME" \
  --initial-volume=$SYSTEM_OUTPUT_VOLUME \
  --backend "$SPOTIFY_BACKEND" \
  --device "$SPOTIFY_DEVICE" \
  -u "$SPOTIFY_LOGIN" \
  -p "$SPOTIFY_PASSWORD"
