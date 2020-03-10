FROM local/librespot:latest

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
