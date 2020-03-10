FROM alpine:edge

WORKDIR /data

RUN apk --no-cache add snapcast-client

ENV SNAPCAST_SERVER 10.0.0.100

CMD snapclient -h $SNAPCAST_SERVER
