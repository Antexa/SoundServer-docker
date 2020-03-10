FROM local/shairport-sync:latest

ENV DEVICE_NAME Airplay Multiroom
ENV SHAIRPORT_BACKEND "-o pipe -- /var/cache/snapcast/snapfifo"

# Start AirPlay
CMD shairport-sync \
  -a "$DEVICE_NAME" \
  $SHAIRPORT_BACKEND
