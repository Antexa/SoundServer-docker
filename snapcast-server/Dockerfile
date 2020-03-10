FROM alpine:edge

WORKDIR /data

RUN apk --no-cache add snapcast-server
 
COPY snapserver.conf /etc/snapserver.conf

CMD snapserver
